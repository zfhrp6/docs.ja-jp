---
title: "方法: 複数のキー (Visual Basic) に基づいて要素を並べ替える |Microsoft ドキュメント"
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
ms.assetid: 0c4c1462-3047-4766-b9e2-7e0e9cc7f421
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: ebb71092cb8341df0eaae71ac77f69ff41dd4b30
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-sort-elements-on-multiple-keys-visual-basic"></a><span data-ttu-id="5e956-102">方法: 複数のキー (Visual Basic) に基づいて要素を並べ替える</span><span class="sxs-lookup"><span data-stu-id="5e956-102">How to: Sort Elements on Multiple Keys (Visual Basic)</span></span>
<span data-ttu-id="5e956-103">このトピックでは、複数のキーに基づく並べ替えの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e956-103">This topic shows how to sort on multiple keys.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e956-104">例</span><span class="sxs-lookup"><span data-stu-id="5e956-104">Example</span></span>  
 <span data-ttu-id="5e956-105">この例の結果は、まず出荷先の郵便番号順に並べ替えられ、次に発注日順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="5e956-105">In this example, the results are ordered first by the shipping postal code, then by the order date.</span></span>  
  
 <span data-ttu-id="5e956-106">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="5e956-106">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim result = _  
    From c In co.<Orders>.<Order> _  
    Order By c.<ShipInfo>.<ShipPostalCode>.Value, Convert.ToDateTime(c.<OrderDate>.Value) _  
    Select New With { _  
        .CustomerID = c.<CustomerID>.Value, _  
        .EmployeeID = c.<EmployeeID>.Value, _  
        .ShipPostalCode = c.<ShipInfo>.<ShipPostalCode>.Value, _  
        .OrderDate = Convert.ToDateTime(c.<OrderDate>.Value) _  
    }  
For Each r In result  
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}", _  
                r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate)  
Next  
```  
  
 <span data-ttu-id="5e956-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5e956-107">This code produces the following output:</span></span>  
  
```  
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997  
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997  
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997  
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997  
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997  
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996  
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997  
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997  
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997  
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997  
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997  
```  
  
## <a name="example"></a><span data-ttu-id="5e956-108">例</span><span class="sxs-lookup"><span data-stu-id="5e956-108">Example</span></span>  
 <span data-ttu-id="5e956-109">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="5e956-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5e956-110">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="5e956-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="5e956-111">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: Namespace における Customers と Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="5e956-111">This example uses the following XML document: [Sample XML File: Customers and Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim co As XElement = XElement.Load("CustomersOrdersInNamespace.xml")  
        Dim result = _  
            From c In co.<Orders>.<Order> _  
            Order By c.<ShipInfo>.<ShipPostalCode>.Value, Convert.ToDateTime(c.<OrderDate>.Value) _  
            Select New With { _  
                .CustomerID = c.<CustomerID>.Value, _  
                .EmployeeID = c.<EmployeeID>.Value, _  
                .ShipPostalCode = c.<ShipInfo>.<ShipPostalCode>.Value, _  
                .OrderDate = Convert.ToDateTime(c.<OrderDate>.Value) _  
            }  
        For Each r In result  
            Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}", _  
                        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5e956-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5e956-112">This code produces the following output:</span></span>  
  
```  
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997  
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997  
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997  
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997  
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997  
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997  
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998  
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998  
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996  
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996  
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997  
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997  
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997  
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997  
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e956-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e956-113">See Also</span></span>  
 [<span data-ttu-id="5e956-114">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e956-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

