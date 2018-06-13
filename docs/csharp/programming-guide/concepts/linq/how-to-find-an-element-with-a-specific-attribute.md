---
title: '方法: 特定の属性を持つ要素を検索する (C#)'
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 53296b2ace23bbc57deb0f5e7c0b23ebfc9613d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325696"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="2f0a2-102">方法: 特定の属性を持つ要素を検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0a2-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="2f0a2-103">このトピックでは、特定の値を含む属性を持つ要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f0a2-104">例</span><span class="sxs-lookup"><span data-stu-id="2f0a2-104">Example</span></span>  
 <span data-ttu-id="2f0a2-105">この例では、"Billing" の値を含む `Address` 属性を持つ `Type` 要素を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="2f0a2-106">この例では、「[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="2f0a2-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-107">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2f0a2-108">例</span><span class="sxs-lookup"><span data-stu-id="2f0a2-108">Example</span></span>  
 <span data-ttu-id="2f0a2-109">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="2f0a2-110">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="2f0a2-111">この例では、XML ドキュメントの「[サンプル XML ファイル : 名前空間内の一般的な購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="2f0a2-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2f0a2-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f0a2-113">参照</span><span class="sxs-lookup"><span data-stu-id="2f0a2-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="2f0a2-114">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0a2-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="2f0a2-115">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0a2-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="2f0a2-116">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="2f0a2-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
