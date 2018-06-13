---
title: x:Array のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: 7c728b63c16d8f24c4ad68d07e6d174f510204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565014"
---
# <a name="xarray-markup-extension"></a>x:Array のマークアップ拡張機能
マークアップ拡張機能によって、XAML でのオブジェクトの配列には、一般的なサポートを提供します。 これに対応して、 `x:ArrayExtension` [MS-XAML] の XAML の型。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`typeName`|型の名前を`x:Array`が含まれます。 `typeName` 可能性があります (および多くの場合) を含む XAML 名前空間は XAML のプレフィックス定義を入力します。|  
|`arrayContents`|組み込みに割り当てられている項目コンテンツ`ArrayExtension.Items`プロパティです。 通常、これらの項目が内に含まれる 1 つまたは複数のオブジェクト要素として指定、`x:Array`タグと終了タグ。 指定したオブジェクトはここで含められるはずで指定された XAML 型に割り当てることができる`typeName`です。|  
  
## <a name="remarks"></a>コメント  
 `Type` すべての必須の属性は、 `x:Array` object 要素。 A`Type`パラメーターの値が使用する必要はありません、`x:Type`マークアップ拡張機能です。 短い型の名前は XAML 型の型を文字列として指定することができます。  
  
 入力 XAML の型と CLR の出力の間の関係、.NET Framework XAML サービス実装で<xref:System.Type>作成された配列のサービス コンテキストのマークアップ拡張機能によって影響を受けます。 出力<xref:System.Type>は、 <xref:System.Xaml.XamlType.UnderlyingType%2A> 、必要なを検索した後、入力の XAML 型の<xref:System.Xaml.XamlType>XAML スキーマ コンテキストに基づいて、<xref:System.Windows.Markup.IXamlTypeResolver>サービス コンテキストを提供します。  
  
 配列の内容に割り当てられた、処理されるときに、`ArrayExtension.Items`組み込みプロパティです。 <xref:System.Windows.Markup.ArrayExtension>実装では、これは、によって表される<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>です。  
  
 .NET Framework XAML サービス実装では、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.ArrayExtension>クラスです。 <xref:System.Windows.Markup.ArrayExtension> 封印されていないと、カスタムの配列型のマークアップ拡張機能の実装の基礎として使用できます。  
  
 `x:Array` 以上の目的の一般的な XAML の言語拡張機能です。 しかし、`x:Array`にも特定のプロパティの構造化プロパティ コンテンツとして XAML でサポートされているコレクションを取得する XAML の値を指定するために役立ちます。 内容を指定するなど、<xref:System.Collections.IEnumerable>を持つプロパティ、`x:Array`使用量。  
  
 `x:Array` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 `x:Array` その規則の例外では部分的に代替の属性値の処理を提供する代わりに`x:Array`その内部のテキスト コンテンツの代替の処理を提供します。 この動作により、型を配列にグループ化して、名前付きの配列へのアクセスを後で分離コード内で参照する既存のコンテンツ モデルでサポートされていない可能性があります。呼び出すことができます<xref:System.Array>を個々 の配列項目を取得するメソッド。  
  
 XAML でのすべてのマークアップ拡張機能は、かっこを使用して ({,} `)`それぞれ属性の構文では、マークアップ拡張機能が属性値を処理する必要がありますを XAML プロセッサが認識される規約。 一般にマークアップ拡張機能の詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)します。  
  
 XAML 2009 で`x:Array`マークアップ拡張機能ではなくプリミティブ言語として定義されます。 詳細については、次を参照してください。[共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)です。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 通常、オブジェクトの要素を設定する、`x:Array`に存在する要素ではない、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]の XAML 名前空間を既定以外の XAML 名前空間プレフィックスのマッピングを必要とします。  
  
 例を次に示します、単純な 2 つの文字列の配列で、`sys`プレフィックス (も`x`) 配列のレベルで定義します。  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 配列の要素として使用されるカスタム型、クラスは、xaml オブジェクト要素としてインスタンス化の要件をサポートもする必要があります。 詳細については、次を参照してください。 [XAML と WPF のカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)です。  
  
## <a name="see-also"></a>関連項目  
 [マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [WPF から System.Xaml に移行した型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
