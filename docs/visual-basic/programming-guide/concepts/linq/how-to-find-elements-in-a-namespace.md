---
title: '方法: Namespace (XPATH-LINQ to XML) 内の要素を検索 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
ms.openlocfilehash: 417ff63408ea640bbbd5cc4863193e769a2ec444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="d79cd-102">方法: Namespace (XPATH-LINQ to XML) 内の要素を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d79cd-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d79cd-103">XPath 式を使用すると、特定の名前空間内のノードを検索できます。</span><span class="sxs-lookup"><span data-stu-id="d79cd-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="d79cd-104">XPath 式では、名前空間を指定する名前空間プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d79cd-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="d79cd-105">名前空間プレフィックスを含む XPath 式を解析するには、<xref:System.Xml.IXmlNamespaceResolver> を実装する XPath メソッドにオブジェクトを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d79cd-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="d79cd-106">この例では <xref:System.Xml.XmlNamespaceManager> を使用します。</span><span class="sxs-lookup"><span data-stu-id="d79cd-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="d79cd-107">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d79cd-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="d79cd-108">例</span><span class="sxs-lookup"><span data-stu-id="d79cd-108">Example</span></span>  
 <span data-ttu-id="d79cd-109">次の例では、2 つの名前空間を含む XML ツリーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d79cd-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="d79cd-110"><xref:System.Xml.XmlReader> を使用して XML ドキュメントを読み込ます。</span><span class="sxs-lookup"><span data-stu-id="d79cd-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="d79cd-111">次に、<xref:System.Xml.XmlNameTable> から <xref:System.Xml.XmlReader> を取得し、<xref:System.Xml.XmlNamespaceManager> から <xref:System.Xml.XmlNameTable> を取得します。</span><span class="sxs-lookup"><span data-stu-id="d79cd-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="d79cd-112">要素を選択する際には <xref:System.Xml.XmlNamespaceManager> を使用します。</span><span class="sxs-lookup"><span data-stu-id="d79cd-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
```vb  
Dim reader As XmlReader = _  
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")  
Dim root As XElement = XElement.Load(reader)  
Dim nameTable As XmlNameTable = reader.NameTable  
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")  
  
Dim list1 As IEnumerable(Of XElement) = _  
        root.XPathSelectElements("./aw:*", namespaceManager)  
Dim list2 As IEnumerable(Of XElement) = _  
    From el In root.Elements() _  
    Where el.Name.Namespace = "http://www.adventure-works.com" _  
    Select el  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="d79cd-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d79cd-113">This example produces the following output:</span></span>  
  
```  
Results are identical  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="d79cd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d79cd-114">See Also</span></span>  
 [<span data-ttu-id="d79cd-115">LINQ to XML を XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d79cd-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
