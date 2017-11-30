---
title: "回収可能アセンブリの動的な型の生成"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>回収可能アセンブリの動的な型の生成

*回収可能アセンブリ*動的アセンブリが作成されたアプリケーション ドメインをアンロードせずアンロードできます。 回収可能アセンブリとが含まれている型で使用される、すべてのマネージ コードとアンマネージ メモリが再利用できることができます。 アセンブリ名などの情報は、内部テーブルから削除されます。

アンロードを有効にするには、<xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType>動的アセンブリを作成するときにフラグを設定します。 アセンブリが一時的な (つまり、保存できません) で説明されている制限事項が適用、[回収可能アセンブリに関する制限事項](#restrictions-on-collectible-assemblies)セクションです。 共通言語ランタイム (CLR) は、アセンブリに関連付けられているすべてのオブジェクトを解放するときに自動的に回収可能アセンブリをアンロードします。 その他のすべての点で回収可能アセンブリが作成され、他の動的アセンブリと同じ方法で使用します。

## <a name="lifetime-of-collectible-assemblies"></a>回収可能アセンブリの有効期間

回収可能アセンブリの有効期間への参照が含まれている型やこれらの型から作成されるオブジェクトの存在によって制御されます。 次の 1 つ以上存在する限り、共通言語ランタイムがアセンブリをアンロードしません (`T`アセンブリで定義されている型である)。 

- `T` のインスタンス。

- インスタンスの配列の`T`します。
 
- 持つジェネリック型のインスタンス`T`として、型引数のいずれか。 ジェネリック コレクションが含まれます`T`場合でも、そのコレクションが空です。

- インスタンス<xref:System.Type>または<xref:System.Reflection.Emit.TypeBuilder>を表す`T`です。 

   > [!IMPORTANT]
   > アセンブリの部分を表すすべてのオブジェクトを解放する必要があります。 <xref:System.Reflection.Emit.ModuleBuilder>を定義する`T`への参照を保持、 <xref:System.Reflection.Emit.TypeBuilder>、および<xref:System.Reflection.Emit.AssemblyBuilder>オブジェクトへの参照を保持する、<xref:System.Reflection.Emit.ModuleBuilder>ので、これらのオブジェクトへの参照を解放する必要があります。 存在も、<xref:System.Reflection.Emit.LocalBuilder>または<xref:System.Reflection.Emit.ILGenerator>の作成に使用される`T`アンロードできなくなります。

- 参照を静的`T`動的に定義された別の種類によって`T1`コードを実行して到達可能です。 たとえば、`T1`から導き出さ`T`、または`T`のメソッドのパラメーターの型である可能性があります`T1`です。
 
- A **ByRef**に属している静的フィールドを`T`です。

- A <xref:System.RuntimeTypeHandle>、 <xref:System.RuntimeFieldHandle>、または<xref:System.RuntimeMethodHandle>を参照する`T`またはのコンポーネントに`T`です。

- インスタンスが使用可能なない直接リフレクション オブジェクトまたはアクセスに直接、<xref:System.Type>を表すオブジェクト`T`です。 たとえば、<xref:System.Type>オブジェクトに対する`T`要素型が配列型から取得できます`T`、またはを持つジェネリック型から`T`型引数として。 

- メソッド`M`任意のスレッドのコール スタックに場所`M`のメソッドは、`T`またはアセンブリで定義されているモジュール レベル メソッドです。

- アセンブリのモジュールで定義されている静的メソッドへのデリゲート。

この一覧から 1 つの項目は、1 つだけの型またはアセンブリ内の 1 つのメソッドが、しかない場合、ランタイムは、アセンブリをアンロードできません。

> [!NOTE]
> ランタイムが実際にアンロードしないアセンブリ リスト内のすべての項目に対してファイナライザーが実行されるまでです。

追跡の有効期間の目的では、構築されたジェネリック型などの入力`List<int>`(C# の場合) または`List(Of Integer)`(Visual Basic で) を作成されで使用される回収可能アセンブリの生成をされていると見なされます、アセンブリのいずれかを定義します。ジェネリックを含む定義を入力するか、型引数のいずれかの定義を含むアセンブリにします。 使用される正確なアセンブリは、実装の詳細と件名を変更します。
 
## <a name="restrictions-on-collectible-assemblies"></a>回収可能アセンブリに関する制限事項

回収可能アセンブリには次の制限が適用されます。 

- **静的参照**   
  通常の動的アセンブリ内の型は、回収可能アセンブリで定義されている型への静的参照を持つことはできません。 たとえば、回収可能アセンブリ内の型から継承する通常の型を定義する場合、<xref:System.NotSupportedException>例外がスローされます。 回収可能アセンブリ内の型は、別の回収可能アセンブリ、型への静的参照を持つことができますが、これは、参照されたアセンブリを参照しているアセンブリの有効期間の有効期間を拡張します。

- **COM 相互運用機能**   
   回収可能アセンブリ内でない COM インターフェイスを定義することができ、COM オブジェクトに回収可能アセンブリ内の型のインスタンスを変換することができます。 回収可能アセンブリ内の型は、COM 呼び出し可能ラッパー (CCW) またはランタイム呼び出し可能ラッパー (RCW) として使用できません。 ただし、回収可能アセンブリ内の型は COM インターフェイスを実装するオブジェクトを使用できます。

- **プラットフォーム呼び出し**   
   持つメソッドを<xref:System.Runtime.InteropServices.DllImportAttribute>回収可能アセンブリ内で宣言されているときに、属性はコンパイルされません。 <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType>命令は、回収可能アセンブリ内の型の実装で使用することはできませんし、このような型は、アンマネージ コードにマーシャ リングすることはできません。 ただし、非回収可能アセンブリで宣言されているエントリ ポイントを使用してネイティブ コードを呼び出すことができます。
 
- **マーシャ リング**   
   回収可能アセンブリで定義されている (特に、デリゲートは) 内のオブジェクトをマーシャ リングすることはできません。 これは、すべての一時的な生成型に制限します。

- **アセンブリの読み込み**   
   リフレクション出力は、回収可能アセンブリを読み込むためのサポートされている唯一のメカニズムです。 アセンブリの読み込みの他の形式を使用して、読み込まれたアセンブリをアンロードすることはできません。
 
- **コンテキスト バインド オブジェクト**    
   コンテキストの静的変数はサポートされていません。 回収可能アセンブリで型を拡張することはできません<xref:System.ContextBoundObject>です。 ただし、回収可能アセンブリのコードは他の場所で定義されているコンテキスト バインド オブジェクトを使用できます。

- **スレッドの静的データ**       
   スレッドの静的変数はサポートされていません。

## <a name="see-also"></a>関連項目

[動的メソッドおよびアセンブリの出力](emitting-dynamic-methods-and-assemblies.md)
