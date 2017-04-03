---
title: "XElement クラスの概要 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 193ae8193d73d57638835c96c3f7dfd28d320473
ms.lasthandoff: 03/13/2017

---
# <a name="xelement-class-overview-c"></a>XElement クラスの概要 (C#)
<xref:System.Xml.Linq.XElement> クラスは、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の基礎クラスの 1 つです。 これは XML 要素を表します。 このクラスを使用すると、要素の作成、要素のコンテンツの変更、子要素の追加、変更、削除、要素への属性の追加、および要素のコンテンツのテキスト形式へのシリアル化を行うことができます。 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、<xref:System.Xml.Xsl.XslCompiledTransform> などの、<xref:System.Xml?displayProperty=fullName> の他のクラスと相互運用することもできます。  
  
## <a name="xelement-functionality"></a>XElement の機能  
 このトピックでは、<xref:System.Xml.Linq.XElement> クラスによって提供される機能について説明します。  
  
### <a name="constructing-xml-trees"></a>XML ツリーの構築  
 次のようなさまざまな方法で XML ツリーを構築できます。  
  
-   コードで XML ツリーを構築できます。 詳しくは、「[XML ツリーの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)」をご覧ください。  
  
-   <xref:System.IO.TextReader>、テキスト ファイル、Web アドレス (URL) など、さまざまなソースから XML を解析できます。 詳しくは、「[XML の解析 (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)」をご覧ください。  
  
-   <xref:System.Xml.XmlReader> を使用してツリーを設定できます。 詳しくは、 <xref:System.Xml.Linq.XNode.ReadFrom%2A> をご覧ください。  
  
-   <xref:System.Xml.XmlWriter> にコンテンツを書き込むことができるモジュールがある場合は、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> メソッドを使用してライターを作成し、このライターをモジュールに渡し、<xref:System.Xml.XmlWriter> に書き込まれたコンテンツを使用して XML ツリーを設定できます。  
  
 しかし、XML ツリーを作成する最も一般的な方法は次のとおりです。  
  
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
  
 XML ツリーを作成するもう 1 つの一般的な方法では、次の例に示すように、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリの結果を使用して XML ツリーを設定します。  
  
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
  
### <a name="serializing-xml-trees"></a>XML ツリーのシリアル化  
 XML ツリーを <xref:System.IO.File>、<xref:System.IO.TextWriter> または <xref:System.Xml.XmlWriter> にシリアル化することができます。  
  
 詳しくは、「[XML ツリーのシリアル化 (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)」をご覧ください。  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>軸メソッドによる XML データの取得  
 軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。  
  
 詳しくは、「[LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)」をご覧ください。  
  
### <a name="querying-xml-trees"></a>XML ツリーのクエリ  
 XML ツリーからデータを抽出する [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリを記述できます。  
  
 詳しくは、「[XML ツリーのクエリ (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)」をご覧ください。  
  
### <a name="modifying-xml-trees"></a>XML ツリーの変更  
 要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。 要素を親から削除することもできます。  
  
 詳しくは、「[XML ツリーの変更 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML プログラミングの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
