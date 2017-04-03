---
title: "方法: 名前空間内の要素を検索する (XPath-LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dc1b201a807b8e5c060720018195fe3639e748dc
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a>方法: 名前空間内の要素を検索する (XPath-LINQ to XML) (C#)
XPath 式を使用すると、特定の名前空間内のノードを検索できます。 XPath 式では、名前空間を指定する名前空間プレフィックスを使用します。 名前空間プレフィックスを含む XPath 式を解析するには、<xref:System.Xml.IXmlNamespaceResolver> を実装する XPath メソッドにオブジェクトを渡す必要があります。 この例では、<xref:System.Xml.XmlNamespaceManager> を使用します。  
  
 XPath 式を次に示します。  
  
 `./aw:*`  
  
## <a name="example"></a>例  
 次の例では、2 つの名前空間を含む XML ツリーを読み込みます。 <xref:System.Xml.XmlReader> を使用して XML ドキュメントを読み込ます。 次に、<xref:System.Xml.XmlReader> から <xref:System.Xml.XmlNameTable> を取得し、<xref:System.Xml.XmlNameTable> から <xref:System.Xml.XmlNamespaceManager> を取得します。 要素を選択するときには <xref:System.Xml.XmlNamespaceManager> を使用します。  
  
```csharp  
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");  
XElement root = XElement.Load(reader);  
XmlNameTable nameTable = reader.NameTable;  
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");  
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);  
IEnumerable<XElement> list2 =  
    from el in root.Elements()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [XPath ユーザー向けの LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
