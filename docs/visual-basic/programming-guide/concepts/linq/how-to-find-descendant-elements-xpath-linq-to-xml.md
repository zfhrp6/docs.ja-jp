---
title: '方法: 子孫要素 (XPATH-LINQ to XML) を検索 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e7e2dc9e-bda9-420d-a5b1-4fabf1cca46b
ms.openlocfilehash: e5915eb06af427c0631049af6dfc30399cb775e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="6d538-102">方法: 子孫要素 (XPATH-LINQ to XML) を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d538-102">How to: Find Descendant Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6d538-103">このトピックでは、特定の名前を指定して子孫要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d538-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="6d538-104">XPath 式は `//Name` です。</span><span class="sxs-lookup"><span data-stu-id="6d538-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d538-105">例</span><span class="sxs-lookup"><span data-stu-id="6d538-105">Example</span></span>  
 <span data-ttu-id="6d538-106">この例では、`Name` という名前の子孫要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="6d538-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="6d538-107">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d538-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
      Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po...<Name>  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")  
  
If (list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="6d538-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6d538-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d538-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d538-109">See Also</span></span>  
 [<span data-ttu-id="6d538-110">LINQ to XML を XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d538-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
