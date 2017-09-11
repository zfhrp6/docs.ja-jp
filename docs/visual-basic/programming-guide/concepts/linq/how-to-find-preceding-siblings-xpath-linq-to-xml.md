---
title: "方法: 先行する (XPATH-LINQ to XML) の兄弟を検索 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 59055718-d0a7-4db3-8901-18dd33587703
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8a6487d52e99bbf937439c902b59bf75bb67c8e4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="c5332-102">方法: 先行する (XPATH-LINQ to XML) の兄弟を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5332-102">How to: Find Preceding Siblings (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c5332-103">このトピックで、XPath は比較`preceding-sibling`軸、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]子<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>軸</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="c5332-103">This topic compares the XPath `preceding-sibling` axis to the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] child <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> axis.</span></span>  
  
 <span data-ttu-id="c5332-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5332-104">The XPath expression is:</span></span>  
  
 `preceding-sibling::*`  
  
 <span data-ttu-id="c5332-105">両方の結果<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>と<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>はドキュメント順にします</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.XPath.Extensions.XPathSelectElements%2A>。</span><span class="sxs-lookup"><span data-stu-id="c5332-105">Note that the results of both <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> and <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> are in document order.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5332-106">例</span><span class="sxs-lookup"><span data-stu-id="c5332-106">Example</span></span>  
 <span data-ttu-id="c5332-107">次の例では、`FullAddress` 要素を検索し、次に `preceding-sibling` 軸を使用して前の要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="c5332-107">The following example finds the `FullAddress` element, and then retrieves the previous elements using the `preceding-sibling` axis.</span></span>  
  
 <span data-ttu-id="c5332-108">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="c5332-108">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim add As XElement = co.<Customers>.<Customer>. _  
        <FullAddress>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="c5332-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c5332-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5332-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5332-110">See Also</span></span>  
 [<span data-ttu-id="c5332-111">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5332-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
