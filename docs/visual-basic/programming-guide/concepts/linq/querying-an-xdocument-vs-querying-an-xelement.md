---
title: "XDocument のクエリと (Visual Basic) XElement のクエリ |Microsoft ドキュメント"
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
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 93f0f7f50ad305540a6afef2374d4b948de48705
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a><span data-ttu-id="94057-102">XDocument のクエリと (Visual Basic) XElement のクエリ</span><span class="sxs-lookup"><span data-stu-id="94057-102">Querying an XDocument vs. Querying an XElement (Visual Basic)</span></span>
<span data-ttu-id="94057-103"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>。</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>を使用して読み込む場合よりも少し異なる方法でクエリを記述する必要があることを確認は、</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>使用してドキュメントを読み込む場合</span><span class="sxs-lookup"><span data-stu-id="94057-103">When you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, you will notice that you have to write queries slightly differently than when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>.</span></span>  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="94057-104">XDocument.Load と XElement.Load の比較</span><span class="sxs-lookup"><span data-stu-id="94057-104">Comparison of XDocument.Load and XElement.Load</span></span>  
 <span data-ttu-id="94057-105">XML ドキュメントを読み込む場合、<xref:System.Xml.Linq.XElement>経由で<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement>ツリーには XML のルートには、読み込んだドキュメントのルート要素が含まれています</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="94057-105">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="94057-106">ただし、読み込む場合、同じ XML ドキュメントに、<xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>ツリーのルートの<xref:System.Xml.Linq.XDocument>ノードで、読み込んだドキュメントのルート要素は&1; つの許可されている子<xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XDocument>。</xref:System.Xml.Linq.XDocument>ノード</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>、</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>使用して</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="94057-106">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="94057-107">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 軸は、ルート ノードを基準に動作します。</span><span class="sxs-lookup"><span data-stu-id="94057-107">The [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] axes operate relative to the root node.</span></span>  
  
 <span data-ttu-id="94057-108">この最初の例は、 <xref:System.Xml.Linq.XElement.Load%2A>。</xref:System.Xml.Linq.XElement.Load%2A>を使用して XML ツリーを読み込みます</span><span class="sxs-lookup"><span data-stu-id="94057-108">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="94057-109">次に、ツリーのルートの子要素をクエリします。</span><span class="sxs-lookup"><span data-stu-id="94057-109">It then queries for the child elements of the root of the tree.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="94057-110">この例では、次の出力が生成されることが想定されます。</span><span class="sxs-lookup"><span data-stu-id="94057-110">As expected, this example produces the following output:</span></span>  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 <span data-ttu-id="94057-111">次の例は、1 つとして前、に、 <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>ではなく</xref:System.Xml.Linq.XDocument>XML ツリーが読み込まれている例外で同じ</span><span class="sxs-lookup"><span data-stu-id="94057-111">The following example is the same as the one above, with the exception that the XML tree is loaded into an <xref:System.Xml.Linq.XDocument> instead of an <xref:System.Xml.Linq.XElement>.</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="94057-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="94057-112">This example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 <span data-ttu-id="94057-113">この同じクエリでは、3 つの子ノードではなく&1; つの `Root` ノードが返されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="94057-113">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>  
  
 <span data-ttu-id="94057-114">これに対処する方法の&1; つは、使用する、<xref:System.Xml.Linq.XDocument.Root%2A>軸メソッドを次のようにアクセスする前にプロパティ:</xref:System.Xml.Linq.XDocument.Root%2A></span><span class="sxs-lookup"><span data-stu-id="94057-114">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="94057-115">このクエリは、同じようになりました実行<xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>ルートとすると、ツリーのクエリ方法。</span><span class="sxs-lookup"><span data-stu-id="94057-115">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="94057-116">この例では次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="94057-116">The example produces the following output:</span></span>  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94057-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="94057-117">See Also</span></span>  
 [<span data-ttu-id="94057-118">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94057-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
