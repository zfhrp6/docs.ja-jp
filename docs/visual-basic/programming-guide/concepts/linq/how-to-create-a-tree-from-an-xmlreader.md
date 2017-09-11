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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a60b5cb3557016bba7bae9be6e0b9c9a448c1284
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="38867-102">方法: XmlReader (Visual Basic の場合) からツリーを作成</span><span class="sxs-lookup"><span data-stu-id="38867-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="38867-103">このトピックは、 <xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>から直接 XML ツリーを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="38867-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="38867-104">作成する、<xref:System.Xml.Linq.XElement>から、 <xref:System.Xml.XmlReader>、配置する必要があります、<xref:System.Xml.XmlReader>要素ノードにします</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="38867-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="38867-105"><xref:System.Xml.XmlReader>コメントをスキップし、処理命令の場合は、<xref:System.Xml.XmlReader>が配置されているテキスト ノードに、エラーがスローされます</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="38867-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="38867-106">このようなエラーを避けるためには、常に、配置<xref:System.Xml.XmlReader><xref:System.Xml.XmlReader>。</xref:System.Xml.XmlReader>から XML ツリーを作成する前に要素を</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="38867-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38867-107">例</span><span class="sxs-lookup"><span data-stu-id="38867-107">Example</span></span>  
 <span data-ttu-id="38867-108">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="38867-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="38867-109">次のコードでは、`T:System.Xml.XmlReader` オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="38867-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="38867-110">次に、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="38867-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="38867-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="38867-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38867-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="38867-112">See Also</span></span>  
 [<span data-ttu-id="38867-113">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="38867-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
