---
title: "方法: 子要素 (XPATH-LINQ to XML) を検索 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: adb46c98-a650-42e2-b62d-835920fe8421
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 463c68cd32d185f8a58e866e1915dd94c0ed76c4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="492cf-102">方法: 子要素 (XPATH-LINQ to XML) を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="492cf-102">How to: Find a Child Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="492cf-103">このトピックに XPath の子要素軸を比較し、 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>メソッド</xref:System.Xml.Linq.XContainer.Element%2A>。</span><span class="sxs-lookup"><span data-stu-id="492cf-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="492cf-104">XPath 式は `DeliveryNotes` です。</span><span class="sxs-lookup"><span data-stu-id="492cf-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="492cf-105">例</span><span class="sxs-lookup"><span data-stu-id="492cf-105">Example</span></span>  
 <span data-ttu-id="492cf-106">この例では、`DeliveryNotes` 子要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="492cf-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="492cf-107">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 複数の発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="492cf-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="492cf-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="492cf-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="492cf-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="492cf-109">See Also</span></span>  
 [<span data-ttu-id="492cf-110">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="492cf-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

