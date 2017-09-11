---
title: "方法: 軸メソッドの呼び出しを連結する (LINQ to XML) (C#)"
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
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 17793e0620969125de202de7edea89d748b98ee7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="f9242-102">方法: 軸メソッドの呼び出しを連結する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f9242-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f9242-103">コードで使用する一般的なパターンでは、軸メソッドを呼び出してから、拡張メソッド軸のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f9242-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="f9242-104">要素のコレクションを返す `Elements` という名前の軸には、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> メソッドと <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> メソッドの 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="f9242-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="f9242-105">この 2 つの軸を組み合わせて、ツリー内の指定した深さで指定した名前を持つ要素をすべて検索できます。</span><span class="sxs-lookup"><span data-stu-id="f9242-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9242-106">例</span><span class="sxs-lookup"><span data-stu-id="f9242-106">Example</span></span>  
 <span data-ttu-id="f9242-107">この例では、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> および <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> を使用して、すべての `Name` 要素内にあるすべての `Address` 要素内で `PurchaseOrder` 要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="f9242-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="f9242-108">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9242-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements("PurchaseOrder")  
        .Elements("Address")  
        .Elements("Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f9242-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9242-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="f9242-110">このように出力されるのは、`Elements` 軸の実装の 1 つが、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XContainer> に対する拡張メソッドとして存在しているためです。</span><span class="sxs-lookup"><span data-stu-id="f9242-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="f9242-111"><xref:System.Xml.Linq.XElement> は <xref:System.Xml.Linq.XContainer> から派生するため、<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> メソッドを呼び出した結果に対して <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f9242-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9242-112">例</span><span class="sxs-lookup"><span data-stu-id="f9242-112">Example</span></span>  
 <span data-ttu-id="f9242-113">祖先が介在する可能性と介在しないが可能性がある場合に、特定の要素の深さにあるすべての要素を取得しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f9242-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="f9242-114">たとえば、次のドキュメントで、`ConfigParameter` 要素の子である `Customer` 要素はすべて取得し、`ConfigParameter` 要素の子である `Root` は取得しないとします。</span><span class="sxs-lookup"><span data-stu-id="f9242-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="f9242-115">この操作を行うには、次のように <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> 軸を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9242-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="f9242-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9242-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="f9242-117">例</span><span class="sxs-lookup"><span data-stu-id="f9242-117">Example</span></span>  
 <span data-ttu-id="f9242-118">次の例は名前空間に含まれている XML 用の手法です。これらの手法は上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="f9242-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="f9242-119">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9242-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f9242-120">この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9242-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");  
IEnumerable<XElement> names =  
    from el in purchaseOrders  
        .Elements(aw + "PurchaseOrder")  
        .Elements(aw + "Address")  
        .Elements(aw + "Name")  
    select el;  
foreach (XElement e in names)  
    Console.WriteLine(e);  
```  
  
 <span data-ttu-id="f9242-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f9242-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9242-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9242-122">See Also</span></span>  
 [<span data-ttu-id="f9242-123">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="f9242-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

