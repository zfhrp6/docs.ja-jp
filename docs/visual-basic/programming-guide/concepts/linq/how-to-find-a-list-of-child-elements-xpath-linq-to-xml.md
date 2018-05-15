---
title: '方法: 子要素 (XPATH-LINQ to XML) の一覧を検索 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: 9b852e2a1129dfc9c54357b6c20769e16a992d80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="5d8a5-102">方法: 子要素 (XPATH-LINQ to XML) の一覧を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d8a5-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="5d8a5-103">このトピックでは、XPath の子要素軸と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を比較します。</span><span class="sxs-lookup"><span data-stu-id="5d8a5-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="5d8a5-104">XPath 式は `./*` です。</span><span class="sxs-lookup"><span data-stu-id="5d8a5-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d8a5-105">例</span><span class="sxs-lookup"><span data-stu-id="5d8a5-105">Example</span></span>  
 <span data-ttu-id="5d8a5-106">この例では、`Address` 要素の子要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="5d8a5-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="5d8a5-107">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d8a5-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="5d8a5-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5d8a5-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d8a5-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d8a5-109">See Also</span></span>  
 [<span data-ttu-id="5d8a5-110">LINQ to XML を XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d8a5-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
