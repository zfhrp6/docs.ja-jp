---
title: "方法: 軸メソッドの呼び出し (LINQ to XML) を連結する (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 4997f7e91f968f080c22ca9d3a204c748758f832
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="4199d-102">方法: 軸メソッドの呼び出し (LINQ to XML) を連結する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4199d-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4199d-103">コードで使用する一般的なパターンでは、軸メソッドを呼び出してから、拡張メソッド軸のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4199d-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="4199d-104">2 つの軸の名前がある`Elements`要素のコレクションを返す:<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>メソッドおよび<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>メソッド</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="4199d-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="4199d-105">この&2; つの軸を組み合わせて、ツリー内の指定した深さで指定した名前を持つ要素をすべて検索できます。</span><span class="sxs-lookup"><span data-stu-id="4199d-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4199d-106">例</span><span class="sxs-lookup"><span data-stu-id="4199d-106">Example</span></span>  
 <span data-ttu-id="4199d-107">この例では<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>と<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>すべてを検索する`Name`内のすべての要素`Address`内のすべての要素`PurchaseOrder`要素</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="4199d-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="4199d-108">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 複数の発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="4199d-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="4199d-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4199d-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="4199d-110">これは、数式のための実装の&1; つ、`Elements`軸は<xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer></xref:System.Collections.Generic.IEnumerable%601>の拡張メソッドとして、。</span><span class="sxs-lookup"><span data-stu-id="4199d-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="4199d-111"><xref:System.Xml.Linq.XElement>派生<xref:System.Xml.Linq.XContainer>呼び出すことができますので、<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>メソッドの呼び出しの結果を<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>メソッド</xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="4199d-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4199d-112">例</span><span class="sxs-lookup"><span data-stu-id="4199d-112">Example</span></span>  
 <span data-ttu-id="4199d-113">祖先が介在する可能性と介在しないが可能性がある場合に、特定の要素の深さにあるすべての要素を取得しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4199d-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="4199d-114">たとえば、次のドキュメントで、`ConfigParameter` 要素の子である `Customer` 要素はすべて取得し、`ConfigParameter` 要素の子である `Root` は取得しないとします。</span><span class="sxs-lookup"><span data-stu-id="4199d-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="4199d-115">これを行うには、使用することができます、<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>次のように、軸:</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4199d-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="4199d-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4199d-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="4199d-117">例</span><span class="sxs-lookup"><span data-stu-id="4199d-117">Example</span></span>  
 <span data-ttu-id="4199d-118">次の例は名前空間に含まれている XML 用の手法です。これらの手法は上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="4199d-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="4199d-119">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="4199d-119">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="4199d-120">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 複数の購買発注、Namespace で](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="4199d-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="4199d-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4199d-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4199d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="4199d-122">See Also</span></span>  
 [<span data-ttu-id="4199d-123">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4199d-123">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
