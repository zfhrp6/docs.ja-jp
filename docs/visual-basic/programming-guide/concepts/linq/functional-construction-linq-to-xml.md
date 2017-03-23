---
title: "関数型構築 (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9fa8cb3c97a1e23a863296c828c82b240e9ab5db
ms.lasthandoff: 03/13/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>関数型構築 (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]呼ばれる XML 要素を作成するための優れた方法は、*関数型構築*します。 関数型構築は、単一のステートメントで XML ツリーを作成するための機能です。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] プログラミング インターフェイスには、関数型構築を利用するためのいくつかの重要な機能があります。  
  
-   <xref:System.Xml.Linq.XElement>コンス トラクターはさまざまな種類のコンテンツ引数を受け取ります</xref:System.Xml.Linq.XElement>。 別の渡すなど<xref:System.Xml.Linq.XElement>子要素になるオブジェクト</xref:System.Xml.Linq.XElement>。 渡すことができます、<xref:System.Xml.Linq.XAttribute>要素の属性になるオブジェクト</xref:System.Xml.Linq.XAttribute>。 また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。  
  
-   <xref:System.Xml.Linq.XElement>コンス トラクターは、`params`型の配列<xref:System.Object>、オブジェクトの数をコンス トラクターに渡すことができます</xref:System.Object></xref:System.Xml.Linq.XElement>。 これにより、複雑なコンテンツを持つ要素を作成できます。  
  
-   オブジェクトを実装する場合<xref:System.Collections.Generic.IEnumerable%601>、オブジェクトのコレクションが列挙され、コレクション内のすべての項目が追加されます</xref:System.Collections.Generic.IEnumerable%601>。 コレクションに含まれる場合<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト、コレクション内の各アイテムは個別に追加されます</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。 これは、重要の結果を渡すことができるので、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]コンス トラクターにクエリします。  
  
 次に例を示します。  
  
 これらの機能を使用する XML ツリーを作成しの結果を使用するコードを記述に XML リテラルを使用するコードを記述する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]XML ツリーを作成するときにクエリを実行します。  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリー (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
