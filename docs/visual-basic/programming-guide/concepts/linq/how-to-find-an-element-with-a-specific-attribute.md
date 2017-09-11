---
title: "方法: 特定の属性 (Visual Basic) で要素を検索 |Microsoft ドキュメント"
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
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 16c3d06eaae8fb77c0844ac78736692de2bfc6f2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a><span data-ttu-id="e6990-102">方法: 特定の属性 (Visual Basic) で要素を検索</span><span class="sxs-lookup"><span data-stu-id="e6990-102">How to: Find an Element with a Specific Attribute (Visual Basic)</span></span>
<span data-ttu-id="e6990-103">このトピックでは、特定の値を含む属性を持つ要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6990-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6990-104">例</span><span class="sxs-lookup"><span data-stu-id="e6990-104">Example</span></span>  
 <span data-ttu-id="e6990-105">この例では、"Billing" の値を含む `Address` 属性を持つ `Type` 要素を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e6990-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="e6990-106">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6990-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="e6990-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e6990-107">This code produces the following output:</span></span>  
  
```xml  
  
          <Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
 <span data-ttu-id="e6990-108">この例ではメモ、 [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)、および[XML 値プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6990-108">Note that this example uses the [XML Child axis property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6990-109">例</span><span class="sxs-lookup"><span data-stu-id="e6990-109">Example</span></span>  
 <span data-ttu-id="e6990-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="e6990-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e6990-111">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6990-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="e6990-112">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書、Namespace で](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6990-112">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e6990-113">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e6990-113">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6990-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6990-114">See Also</span></span>  
 <span data-ttu-id="e6990-115"><xref:System.Xml.Linq.XElement.Attribute%2A></xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="e6990-115"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="e6990-116"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="e6990-116"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
<span data-ttu-id="e6990-117"> [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e6990-117"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
<span data-ttu-id="e6990-118"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e6990-118"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="e6990-119"> [射影操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)</span><span class="sxs-lookup"><span data-stu-id="e6990-119"> [Projection Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)</span></span>
