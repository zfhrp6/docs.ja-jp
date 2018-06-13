---
title: '方法: 子要素 (XPATH-LINQ to XML) を検索 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
ms.openlocfilehash: 122cc269b95a3f35b8eef71e9c7ca1d50af4210b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640459"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="3827f-102">方法: 子要素 (XPATH-LINQ to XML) を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3827f-102">How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3827f-103">このトピックでは、XPath の子要素軸と [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> メソッドを比較します。</span><span class="sxs-lookup"><span data-stu-id="3827f-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="3827f-104">XPath 式は `DeliveryNotes` です。</span><span class="sxs-lookup"><span data-stu-id="3827f-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3827f-105">例</span><span class="sxs-lookup"><span data-stu-id="3827f-105">Example</span></span>  
 <span data-ttu-id="3827f-106">この例では、`DeliveryNotes` 子要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="3827f-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="3827f-107">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="3827f-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault  
  
'LINQ to XML query  
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")  
' same as "child::DeliveryNotes"  
' same as "./DeliveryNotes"  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 <span data-ttu-id="3827f-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3827f-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3827f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3827f-109">See Also</span></span>  
 [<span data-ttu-id="3827f-110">LINQ to XML を XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3827f-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
