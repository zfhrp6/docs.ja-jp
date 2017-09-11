---
title: "方法: Namespace (Visual Basic) 内のすべてのノードの検索 |Microsoft ドキュメント"
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
ms.assetid: b735d7da-5727-48a3-ab57-a16378adc32e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 8ec8acfc576434dd8d48ae4dd9133ba7fbb43959
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-all-nodes-in-a-namespace-visual-basic"></a><span data-ttu-id="ea20b-102">方法: Namespace (Visual Basic) ですべてのノードを検索</span><span class="sxs-lookup"><span data-stu-id="ea20b-102">How to: Find All Nodes in a Namespace (Visual Basic)</span></span>
<span data-ttu-id="ea20b-103">各要素または各属性の名前空間をフィルター処理することで、特定の名前空間内にあるすべてのノードを検索できます。</span><span class="sxs-lookup"><span data-stu-id="ea20b-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea20b-104">例</span><span class="sxs-lookup"><span data-stu-id="ea20b-104">Example</span></span>  
 <span data-ttu-id="ea20b-105">次の例では、2 つの名前空間を持つ XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ea20b-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="ea20b-106">次に、このツリーを反復処理して、いずれかの名前空間内にあるすべての要素と属性の名前を出力します。</span><span class="sxs-lookup"><span data-stu-id="ea20b-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
    Sub Main()  
        Dim xmlTree As XElement = _  
            <aw:Root>  
                <fc:Child1>abc</fc:Child1>  
                <fc:Child2>def</fc:Child2>  
                <aw:Child3>ghi</aw:Child3>  
                <fc:Child4>  
                    <fc:GrandChild1>jkl</fc:GrandChild1>  
                    <aw:GrandChild2>mno</aw:GrandChild2>  
                </fc:Child4>  
            </aw:Root>  
        Console.WriteLine("Nodes in the http://www.adventure-works.com namespace")  
        Dim awElements As IEnumerable(Of XElement) = _  
            From el In xmlTree.Descendants() _  
            Where (el.Name.Namespace = GetXmlNamespace(aw)) _  
            Select el  
        For Each el As XElement In awElements  
            Console.WriteLine(el.Name.ToString())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ea20b-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea20b-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="ea20b-108">例</span><span class="sxs-lookup"><span data-stu-id="ea20b-108">Example</span></span>  
 <span data-ttu-id="ea20b-109">次のクエリでアクセスする XML ファイルには、2 つの異なる名前空間内にある購買発注書が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea20b-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="ea20b-110">このクエリは、いずれかの名前空間内にある要素だけを含む新しいツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ea20b-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="ea20b-111">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 統合購買発注](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md)します。</span><span class="sxs-lookup"><span data-stu-id="ea20b-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cpo As XDocument = XDocument.Load("ConsolidatedPurchaseOrders.xml")  
        Dim newTree As XElement = _  
            <Root>  
                <%= From el In cpo.Root.Elements() _  
                    Where el.Name.Namespace = GetXmlNamespace(aw) _  
                    Select el %>  
            </Root>  
        Console.WriteLine(newTree)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ea20b-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ea20b-112">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea20b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea20b-113">See Also</span></span>  
 [<span data-ttu-id="ea20b-114">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea20b-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

