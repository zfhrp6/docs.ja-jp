---
title: '方法: XML ファイルから読み込みます (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: fce4ebee075f5e622de17bd5227dd6e4ae9cccd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="fe772-102">方法: XML ファイルから読み込みます (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe772-102">How to: Load XML from a File (Visual Basic)</span></span>
<span data-ttu-id="fe772-103">このトピックでは、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> メソッドを使用して URI から XML を読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe772-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe772-104">例</span><span class="sxs-lookup"><span data-stu-id="fe772-104">Example</span></span>  
 <span data-ttu-id="fe772-105">次の例では、ファイルから XML ドキュメントを読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe772-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="fe772-106">この例では、books.xml を読み込んで、XML ツリーをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="fe772-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="fe772-107">この例では、「[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe772-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim booksFromFile As XElement = XElement.Load("books.xml")  
Console.WriteLine(booksFromFile)  
```  
  
 <span data-ttu-id="fe772-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fe772-108">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe772-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe772-109">See Also</span></span>  
 [<span data-ttu-id="fe772-110">(Visual Basic) の XML の解析</span><span class="sxs-lookup"><span data-stu-id="fe772-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
