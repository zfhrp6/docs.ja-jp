---
title: "関数型構築の比較 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a>関数型構築の比較 (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] には、"*関数型構築*" と呼ばれる強力な XML 要素作成機能があります。 関数型構築は、単一のステートメントで XML ツリーを作成するための機能です。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] プログラミング インターフェイスには、関数型構築を利用するためのいくつかの重要な機能があります。  
  
-   <xref:System.Xml.Linq.XElement> コンストラクターは、さまざまな種類のコンテンツ引数を受け取ります。 たとえば、このコンストラクターに、子要素になる別の <xref:System.Xml.Linq.XElement> オブジェクトや、 要素の属性になる <xref:System.Xml.Linq.XAttribute> オブジェクトを渡すことができます。 また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。  
  
-   <xref:System.Xml.Linq.XElement> コンストラクターは、`params` 型の <xref:System.Object> 配列を受け取ります。そのため、任意の数のオブジェクトを配列に渡すことができます。 これにより、複雑なコンテンツを持つ要素を作成できます。  
  
-   オブジェクトが <xref:System.Collections.Generic.IEnumerable%601> を実装している場合、オブジェクト内のコレクションが列挙され、コレクション内のすべての項目が追加されます。 コレクションに <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトが含まれている場合、コレクション内の各項目が個別に追加されます。 これは重要な機能といえます。その理由は、この機能により、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの結果をコンストラクターに渡すことができるためです。  
  
 これらの機能により、XML ツリーを作成するコードを記述することができます。 次に例を示します。  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 また、これらの機能により、XML ツリーを作成するときに、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの結果を使用するコードを記述することができます。次に例を示します。  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
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
 [XML ツリーの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
