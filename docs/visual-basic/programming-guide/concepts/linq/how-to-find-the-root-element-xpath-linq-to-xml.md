---
title: "方法: ルート要素 (XPATH-LINQ to XML) を検索 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e2851bd0fac8132966ea64694d07207e4c9e4f46
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="883dd-102">方法: ルート要素 (XPATH-LINQ to XML) を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="883dd-102">How to: Find the Root Element (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="883dd-103">このトピックでは、XPath および [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] を使用してルート要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="883dd-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
 <span data-ttu-id="883dd-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="883dd-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="883dd-105">例</span><span class="sxs-lookup"><span data-stu-id="883dd-105">Example</span></span>  
 <span data-ttu-id="883dd-106">この例では、ルート要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="883dd-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="883dd-107">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 複数の発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="883dd-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 <span data-ttu-id="883dd-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="883dd-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="883dd-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="883dd-109">See Also</span></span>  
 [<span data-ttu-id="883dd-110">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="883dd-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
