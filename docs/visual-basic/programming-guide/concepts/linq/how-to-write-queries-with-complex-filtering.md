---
title: "方法: 複雑なフィルター (Visual Basic) クエリの作成 |Microsoft ドキュメント"
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
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f8f6dfc78fb94dcb719ca68841dba54fe92ec75
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="7dc82-102">方法: 複雑なフィルター (Visual Basic) クエリの作成</span><span class="sxs-lookup"><span data-stu-id="7dc82-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="7dc82-103">複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7dc82-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="7dc82-104">たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7dc82-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="7dc82-105">このトピックでは、複雑なフィルターを使用してクエリを記述する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dc82-106">例</span><span class="sxs-lookup"><span data-stu-id="7dc82-106">Example</span></span>  
 <span data-ttu-id="7dc82-107">この例では、`PurchaseOrder` 属性が "Shipping" で `Address` 子要素が "NY" である `Type` 子要素を含む `State` 要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="7dc82-108">この例では、入れ子になったクエリを `Where` 句で使用しています。コレクションに要素が含まれる場合、`Any` 演算子は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="7dc82-109">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 複数の発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7dc82-110">詳細については、`Any`演算子を参照してください[量指定子操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 <span data-ttu-id="7dc82-111">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7dc82-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="7dc82-112">例</span><span class="sxs-lookup"><span data-stu-id="7dc82-112">Example</span></span>  
 <span data-ttu-id="7dc82-113">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="7dc82-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7dc82-114">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="7dc82-115">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 複数の購買発注、Namespace で](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="7dc82-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7dc82-116">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7dc82-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="7dc82-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dc82-117">See Also</span></span>  
 <span data-ttu-id="7dc82-118"><xref:System.Xml.Linq.XElement.Attribute%2A></xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="7dc82-118"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="7dc82-119"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="7dc82-119"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
<span data-ttu-id="7dc82-120"> [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="7dc82-120"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
<span data-ttu-id="7dc82-121"> [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="7dc82-121"> [XML Child Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span></span>  
<span data-ttu-id="7dc82-122"> [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="7dc82-122"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="7dc82-123"> [XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span><span class="sxs-lookup"><span data-stu-id="7dc82-123"> [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span></span>  
<span data-ttu-id="7dc82-124"> [射影操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md) </span><span class="sxs-lookup"><span data-stu-id="7dc82-124"> [Projection Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md) </span></span>  
<span data-ttu-id="7dc82-125"> [量指定子操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)</span><span class="sxs-lookup"><span data-stu-id="7dc82-125"> [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)</span></span>
