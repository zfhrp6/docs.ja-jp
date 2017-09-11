---
title: "方法: 関連要素 (XPATH-LINQ to XML) を検索 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e7e5bfc249e0bdeeeefd56508354ac62e5c73465
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="13ca9-102">方法: 関連要素 (XPATH-LINQ to XML) を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13ca9-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="13ca9-103">このトピックでは、別の要素の値によって参照される属性に基づいて要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13ca9-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="13ca9-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="13ca9-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="13ca9-105">例</span><span class="sxs-lookup"><span data-stu-id="13ca9-105">Example</span></span>  
 <span data-ttu-id="13ca9-106">この例では、12 番目の `Order` 要素を検索し、その注文に対応する顧客を検索します。</span><span class="sxs-lookup"><span data-stu-id="13ca9-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="13ca9-107">.Net のリストのインデックスは '0' から始まることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13ca9-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="13ca9-108">XPath 述語のノード コレクションのインデックスは '1' から始まります。</span><span class="sxs-lookup"><span data-stu-id="13ca9-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="13ca9-109">両者の違いを次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="13ca9-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="13ca9-110">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="13ca9-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 <span data-ttu-id="13ca9-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="13ca9-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ca9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="13ca9-112">See Also</span></span>  
 [<span data-ttu-id="13ca9-113">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13ca9-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

