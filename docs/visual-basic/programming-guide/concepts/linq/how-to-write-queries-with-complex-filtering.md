---
title: '方法: クエリを記述複雑なフィルター (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 500cd9cdc62252eff3addc26006c4ce815ae1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a><span data-ttu-id="62af9-102">方法: クエリを記述複雑なフィルター (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62af9-102">How to: Write Queries with Complex Filtering (Visual Basic)</span></span>
<span data-ttu-id="62af9-103">複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="62af9-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="62af9-104">たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="62af9-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="62af9-105">このトピックでは、複雑なフィルターを使用してクエリを記述する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="62af9-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62af9-106">例</span><span class="sxs-lookup"><span data-stu-id="62af9-106">Example</span></span>  
 <span data-ttu-id="62af9-107">この例では、`PurchaseOrder` 属性が "Shipping" で `Address` 子要素が "NY" である `Type` 子要素を含む `State` 要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="62af9-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="62af9-108">この例では、入れ子になったクエリを `Where` 句で使用しています。コレクションに要素が含まれる場合、`Any` 演算子は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="62af9-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `True` if the collection has any elements in it.</span></span>  
  
 <span data-ttu-id="62af9-109">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="62af9-109">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="62af9-110">詳細については、`Any`演算子を参照してください[量指定子操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="62af9-110">For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="62af9-111">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="62af9-111">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="62af9-112">例</span><span class="sxs-lookup"><span data-stu-id="62af9-112">Example</span></span>  
 <span data-ttu-id="62af9-113">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="62af9-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="62af9-114">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の操作](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="62af9-114">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="62af9-115">この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="62af9-115">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="62af9-116">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="62af9-116">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="62af9-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="62af9-117">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="62af9-118">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62af9-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="62af9-119">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="62af9-119">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="62af9-120">XML 属性軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="62af9-120">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)  
 [<span data-ttu-id="62af9-121">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="62af9-121">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="62af9-122">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62af9-122">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
 [<span data-ttu-id="62af9-123">量指定子操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62af9-123">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
