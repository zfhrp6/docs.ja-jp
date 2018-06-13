---
title: XAML のコレクションおよびコレクション型
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 5605c97b13503e18e2f698f2a19f715663052b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562977"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML のコレクションおよびコレクション型
このトピックでは、コレクションをサポートして、親オブジェクトの要素またはプロパティ要素の子要素としてコレクション アイテムをインスタンス化するため、XAML 構文をサポートするためには、型のプロパティを定義する方法について説明します。  
  
## <a name="xaml-collection-concepts"></a>XAML のコレクションの概念  
 概念的には、xaml を XAML オブジェクト要素のスコープ内で複数の子項目があるまたは XAML プロパティ要素をコレクションとして実装する必要がある関係します。 コレクションには、そのリレーションシップの親である XAML 型の特定の XAML プロパティを関連付ける必要があります。 プロパティは、XAML プロセッサは、バッキング コレクション プロパティの新しく追加された項目であるマークアップ内の各項目を割り当てるが必要ですがあるために、コレクションにすることがあります。  
  
 XAML 言語レベルでは、コレクションのサポートの正確な要件は完全には定義されていません。 コレクションできるリストまたはディクショナリ (が両方ではなく) の概念が XAML 言語レベルで定義されているが、どのバッキング型は、いずれかのリストを表すまたは辞書は、XAML 言語で定義されていません。  
  
 .NET Framework XAML サービスでは、バッキング型の .NET Framework の観点から、XAML コレクションのサポートの概念がより明確に定義します。 具体的には、コレクションの XAML サポートは、いくつかの .NET Framework の概念とリストやディクショナリで .NET Framework の一般的なプログラミングに使用される Api に基づいています。  
  
1.  <xref:System.Collections.IList>インターフェイスは、リスト コレクションを表します。  
  
2.  <xref:System.Collections.IDictionary>インターフェイスが dicionary コレクションを表します。  
  
3.  <xref:System.Array> 配列、および配列をサポートしている表します<xref:System.Collections.IList>メソッドです。  
  
 これらの概念のコレクションの各で、.NET Framework XAML サービスの XAML プロセッサは、予期を呼び出して、`Add`コレクション プロパティの型の特定のインスタンス上のメソッドです。 または、XAML プロセッサ シナリオでは、シリアル化、リスト、ディクショナリまたは「アイテム」の各コレクションの特定の概念に基づいて配列内に見つかった項目ごとに個別の XAML 型のインスタンスが生成されます。 これらは、:<xref:System.Collections.IList.Item%2A>です。<xref:System.Collections.IDictionary.Item%2A>; 明示的な<xref:System.Array.System%23Collections%23IList%23Item%2A>の<xref:System.Array>します。  
  
## <a name="generic-collections"></a>ジェネリック コレクション  
 ジェネリック コレクションは、プログラミングでは、一般的な .NET Framework の役に立ち、XAML コレクションのプロパティも使用できます。 ただし、ジェネリック インターフェイス<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>として、非ジェネリックと同等の .NET Framework XAML サービスの XAML プロセッサによって識別されない<xref:System.Collections.IList>または<xref:System.Collections.IDictionary>です。 ジェネリック コレクションのプロパティの型の方法をお勧めのクラスから派生するインターフェイスを実装するのではなく<xref:System.Collections.Generic.List%601>または<xref:System.Collections.Generic.Dictionary%602>です。 これらのクラスは、非ジェネリック インターフェイスを実装して、したがってサポートが含まれて、期待される XAML コレクションの基底クラスの実装です。  
  
## <a name="read-only-collections-and-initialization-logic"></a>読み取り専用のコレクションおよび初期化ロジック  
 .NET Framework プログラミングでは、読み取り専用のコレクションとして、コレクションの値が格納されるすべてのプロパティを作成する一般的なデザイン パターンを勧めします。 このパターンでは、コレクションへの影響の制御を強化するコレクションのプロパティを所有するインスタンスで許可される. 具体的には、パターンにより、既存コレクション全体の置換を偶発的なプロパティを設定します。 このパターンでは呼び出し元が、コレクションへのアクセス代わりにできるようにように、コレクションの種類や、関連するコレクション インターフェイスでサポートされているメソッドまたはプロパティを呼び出すことによって<xref:System.Collections.IList>です。  
  
 このパターンを使用すると、読み取り専用コレクションのプロパティを公開する任意のクラスが空のコレクションを保持するには、そのプロパティを初期化する必要があります最初を意味します。 通常、初期化は、クラスの構築の動作の一部として実行されます。 XAML の役に立ちます、ことが重要このようなロジックが常に既定のコンス トラクターによって参照されている XAML は、通常、プロパティを処理する前に既定のコンス トラクターを呼び出すため (コレクションのプロパティまたはそれ以外の場合)。  
  
## <a name="xaml-type-system-support-and-collections"></a>XAML 型システムのサポートとコレクション  
 XAML を解析しを設定するまたはコレクションのプロパティをシリアル化の基本的なメカニズム、以外は、.NET Framework XAML サービスに実装されている XAML 型システムには、XAML でのコレクションに関連するいくつかのデザイン機能が含まれています。  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A> XAML の型は、XAML コレクションのサポートを提供する型によってバックアップされている場合は true を返します。  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A> および<xref:System.Xaml.XamlType.IsArray%2A>XAML の型をサポートするコレクション モードをさらに特定できます。 カスタム XAML の .NET Framework XAML サービスと、XAML に基づくプロセッサは入力システムが、既存に基づいていない<xref:System.Xaml.XamlWriter>実装では、使用するコレクション モードを知る必要がありますを呼び出す方法を把握するためにコレクションの処理です。  
  
3.  前のプロパティの値の各可能性のある影響を受けますの上書きによって<xref:System.Xaml.XamlType.LookupCollectionKind%2A>XAML の型にします。
