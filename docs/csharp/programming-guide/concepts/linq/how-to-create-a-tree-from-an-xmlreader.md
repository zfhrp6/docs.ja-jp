---
title: "方法: XmlReader からツリーを作成する (C#)"
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
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 61685e93e6886b3101d6b30c7f8eb04d026ea55a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="7b522-102">方法: XmlReader からツリーを作成する (C#)</span><span class="sxs-lookup"><span data-stu-id="7b522-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="7b522-103">このトピックでは、<xref:System.Xml.XmlReader> から直接 XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b522-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="7b522-104"><xref:System.Xml.Linq.XElement> から <xref:System.Xml.XmlReader> を作成するには、<xref:System.Xml.XmlReader> を要素ノードに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b522-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="7b522-105"><xref:System.Xml.XmlReader> はコメントや処理命令をスキップしますが、<xref:System.Xml.XmlReader> がテキスト ノードに配置されている場合はエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="7b522-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="7b522-106">このようなエラーを回避するため、<xref:System.Xml.XmlReader> から XML ツリーを作成する前に、必ず <xref:System.Xml.XmlReader> を要素に配置してください。</span><span class="sxs-lookup"><span data-stu-id="7b522-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b522-107">例</span><span class="sxs-lookup"><span data-stu-id="7b522-107">Example</span></span>  
 <span data-ttu-id="7b522-108">この例では、「[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b522-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7b522-109">次のコードでは、`T:System.Xml.XmlReader` オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="7b522-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="7b522-110">次に <xref:System.Xml.Linq.XElement> オブジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="7b522-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="7b522-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7b522-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b522-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b522-112">See Also</span></span>  
 [<span data-ttu-id="7b522-113">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="7b522-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

