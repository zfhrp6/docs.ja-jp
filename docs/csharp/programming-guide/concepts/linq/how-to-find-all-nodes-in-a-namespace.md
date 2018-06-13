---
title: '方法: 名前空間内のすべてのノードを検索する (C#)'
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: b22acdd7c2d64316e802c4dd01876a61141c8979
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317779"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="0cc09-102">方法: 名前空間内のすべてのノードを検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="0cc09-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="0cc09-103">各要素または各属性の名前空間をフィルター処理することで、特定の名前空間内にあるすべてのノードを検索できます。</span><span class="sxs-lookup"><span data-stu-id="0cc09-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc09-104">例</span><span class="sxs-lookup"><span data-stu-id="0cc09-104">Example</span></span>  
 <span data-ttu-id="0cc09-105">次の例では、2 つの名前空間を持つ XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0cc09-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="0cc09-106">次に、このツリーを反復処理して、いずれかの名前空間内にあるすべての要素と属性の名前を出力します。</span><span class="sxs-lookup"><span data-stu-id="0cc09-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="0cc09-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0cc09-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="0cc09-108">例</span><span class="sxs-lookup"><span data-stu-id="0cc09-108">Example</span></span>  
 <span data-ttu-id="0cc09-109">次のクエリでアクセスする XML ファイルには、2 つの異なる名前空間内にある購買発注書が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0cc09-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="0cc09-110">このクエリは、いずれかの名前空間内にある要素だけを含む新しいツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0cc09-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="0cc09-111">この例では、「[サンプル XML ファイル : 統合購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0cc09-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="0cc09-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0cc09-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cc09-113">参照</span><span class="sxs-lookup"><span data-stu-id="0cc09-113">See Also</span></span>  
 [<span data-ttu-id="0cc09-114">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0cc09-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
