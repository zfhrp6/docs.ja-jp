---
title: "XName オブジェクト (LINQ to XML) の事前アトミック化 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 519b64a96e03e098d7325cfb779bcd5d53db3741
ms.lasthandoff: 03/13/2017


---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>XName オブジェクト (LINQ to XML) の事前アトミック化 (Visual Basic)
LINQ to XML でパフォーマンスを向上させる方法の&1; つは、事前アトミック化<xref:System.Xml.Linq.XName>オブジェクト</xref:System.Xml.Linq.XName>。 事前アトミック化では、文字列を割り当てることを意味する<xref:System.Xml.Linq.XName>オブジェクトのコンス トラクターを使用して XML ツリーを作成する前に、<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XAttribute>クラス</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName>。 次に、コンス トラクターに文字列を渡す代わりに変換を使用する、暗黙の型を文字列から<xref:System.Xml.Linq.XName>、渡す、初期化された<xref:System.Xml.Linq.XName>オブジェクト</xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>。  
  
 これによって、特定の名前が繰り返される大きい XML ツリーを作成するときにパフォーマンスが向上します。 これを行うには、宣言して初期化<xref:System.Xml.Linq.XName>オブジェクトを XML ツリーを構築し、使用する前に、<xref:System.Xml.Linq.XName>文字列要素および属性の名前を指定するのではなくオブジェクト</xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>。 この手法では、同じ名前の多数の要素や属性を作成する場合に、パフォーマンスが大幅に向上します。  
  
 各自のシナリオで事前アトミック化をテストし、使用すべきかどうかを判断してください。  
  
## <a name="example"></a>例  
 次に例を示します。  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 次の例は同じ手法を示し、XML ドキュメントが名前空間にあります。  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 次に示すのは、より実働環境に近い例です。 この例では、要素の内容がクエリによって提供されます。  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 前の例では、名前が事前アトミック化されていない次の例に比べて良いパフォーマンスが得られます。  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>関連項目  
 [パフォーマンス (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)   
 [最小単位に分割 XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
