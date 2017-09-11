---
title: "方法: ルート要素を検索する (XPath-LINQ to XML) (C#)"
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
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2731b773e436114bb2324ba1cea339cf9327adb9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="9f104-102">方法: ルート要素を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9f104-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9f104-103">このトピックでは、XPath および [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用してルート要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9f104-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="9f104-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9f104-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="9f104-105">例</span><span class="sxs-lookup"><span data-stu-id="9f104-105">Example</span></span>  
 <span data-ttu-id="9f104-106">この例では、ルート要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="9f104-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="9f104-107">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="9f104-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 <span data-ttu-id="9f104-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9f104-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f104-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f104-109">See Also</span></span>  
 [<span data-ttu-id="9f104-110">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9f104-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

