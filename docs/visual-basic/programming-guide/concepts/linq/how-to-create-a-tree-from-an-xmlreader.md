---
title: "方法: XmlReader (Visual Basic の場合) からツリーを作成 |Microsoft ドキュメント"
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
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a8dff4e518d8850b4050389e5677ac81ecd1e074
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>方法: XmlReader (Visual Basic の場合) からツリーを作成
このトピックは、 <xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>から直接 XML ツリーを作成する方法を示しています。 作成する、<xref:System.Xml.Linq.XElement>から、 <xref:System.Xml.XmlReader>、配置する必要があります、<xref:System.Xml.XmlReader>要素ノードにします</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader></xref:System.Xml.Linq.XElement>。 <xref:System.Xml.XmlReader>コメントをスキップし、処理命令の場合は、<xref:System.Xml.XmlReader>が配置されているテキスト ノードに、エラーがスローされます</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader>。 このようなエラーを避けるためには、常に、配置<xref:System.Xml.XmlReader><xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>から XML ツリーを作成する前に要素を</xref:System.Xml.XmlReader>  
  
## <a name="example"></a>例  
 この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)します。  
  
 次のコードでは、`T:System.Xml.XmlReader` オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取ります。 次に、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications   
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a>関連項目  
 [(Visual Basic) の XML の解析](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
