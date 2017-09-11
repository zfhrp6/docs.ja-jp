---
title: "方法: 複雑なフィルターを使用してクエリを記述する (C#)"
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
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c5b212796df6e65263b8b35514b6807bcdf5797f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="5dda7-102">方法: 複雑なフィルターを使用してクエリを記述する (C#)</span><span class="sxs-lookup"><span data-stu-id="5dda7-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="5dda7-103">複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5dda7-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="5dda7-104">たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5dda7-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="5dda7-105">このトピックでは、複雑なフィルターを使用してクエリを記述する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="5dda7-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5dda7-106">例</span><span class="sxs-lookup"><span data-stu-id="5dda7-106">Example</span></span>  
 <span data-ttu-id="5dda7-107">この例では、`PurchaseOrder` 属性が "Shipping" で `Address` 子要素が "NY" である `Type` 子要素を含む `State` 要素をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="5dda7-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="5dda7-108">この例では、入れ子になったクエリを `Where` 句で使用しています。コレクションに要素が含まれる場合、`Any` 演算子は `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="5dda7-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="5dda7-109">メソッド ベースのクエリ構文の詳細については、「[LINQ でのクエリ構文とメソッド構文](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dda7-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="5dda7-110">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5dda7-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5dda7-111">`Any` 演算子の詳細については、「[量指定子操作 (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dda7-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where   
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="5dda7-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5dda7-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="5dda7-113">例</span><span class="sxs-lookup"><span data-stu-id="5dda7-113">Example</span></span>  
 <span data-ttu-id="5dda7-114">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="5dda7-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5dda7-115">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dda7-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="5dda7-116">この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5dda7-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="5dda7-117">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5dda7-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="5dda7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dda7-118">See Also</span></span>  
 <span data-ttu-id="5dda7-119"><xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="5dda7-119"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="5dda7-120"><xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="5dda7-120"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
 <span data-ttu-id="5dda7-121">[基本的なクエリ (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="5dda7-121">[Basic Queries (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
 <span data-ttu-id="5dda7-122">[射影操作 (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md) </span><span class="sxs-lookup"><span data-stu-id="5dda7-122">[Projection Operations (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md) </span></span>  
 [<span data-ttu-id="5dda7-123">量指定子操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="5dda7-123">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)

