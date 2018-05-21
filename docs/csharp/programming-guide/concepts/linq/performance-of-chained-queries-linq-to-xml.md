---
title: 連結クエリのパフォーマンス (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a><span data-ttu-id="691e7-102">連結クエリのパフォーマンス (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="691e7-102">Performance of Chained Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="691e7-103">LINQ (および LINQ to XML) の重要な利点の 1 つは、連結クエリが、大きい複雑な単一クエリと同様のパフォーマンスを発揮できるという点です。</span><span class="sxs-lookup"><span data-stu-id="691e7-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="691e7-104">連結クエリとは、別のクエリをソースとして使用するクエリです。</span><span class="sxs-lookup"><span data-stu-id="691e7-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="691e7-105">たとえば、次の単純なコードでは、`query2` のソースとして `query1` があります。</span><span class="sxs-lookup"><span data-stu-id="691e7-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 <span data-ttu-id="691e7-106">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="691e7-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="691e7-107">この連結クエリは、リンク リストの反復と同じパフォーマンス プロファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="691e7-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="691e7-108"><xref:System.Xml.Linq.XContainer.Elements%2A> 軸のパフォーマンスは、基本的にリンク リストの反復と同じです。</span><span class="sxs-lookup"><span data-stu-id="691e7-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="691e7-109"><xref:System.Xml.Linq.XContainer.Elements%2A> は、遅延実行のある反復子として実装されます。</span><span class="sxs-lookup"><span data-stu-id="691e7-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="691e7-110">つまり、リンク リストの反復の他に、反復子オブジェクトの割り当てや実行状態の追跡などの作業をします。</span><span class="sxs-lookup"><span data-stu-id="691e7-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="691e7-111">この作業は、反復子の設定時に行われる作業と、各反復中に行われる作業の 2 つのカテゴリに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="691e7-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="691e7-112">設定作業は一定量の小さい作業であり、各反復中に行われる作業はソース コレクションの項目数に比例します。</span><span class="sxs-lookup"><span data-stu-id="691e7-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="691e7-113">`query1` では、`where` 句によってクエリは <xref:System.Linq.Enumerable.Where%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="691e7-113">In `query1`, the `where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="691e7-114">このメソッドも反復子として実装されています。</span><span class="sxs-lookup"><span data-stu-id="691e7-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="691e7-115">設定作業は、ラムダ式を参照するデリゲートのインスタンス化と、反復子の通常の設定から成ります。</span><span class="sxs-lookup"><span data-stu-id="691e7-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="691e7-116">反復ごとに、デリゲートが呼び出されて述語を実行します。</span><span class="sxs-lookup"><span data-stu-id="691e7-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="691e7-117">設定作業と、各反復中に行われる作業は、軸の反復中に行われる作業に似ています。</span><span class="sxs-lookup"><span data-stu-id="691e7-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="691e7-118">`query1` では、SELECT 句によってクエリが <xref:System.Linq.Enumerable.Select%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="691e7-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="691e7-119">このメソッドには <xref:System.Linq.Enumerable.Where%2A> メソッドと同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="691e7-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="691e7-120">`query2` では、`where` 句と `select` 句の両方に `query1` と同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="691e7-120">In `query2`, both the `where` clause and the `select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="691e7-121">したがって、`query2` の反復は最初のクエリのソースにある項目数に直接比例します。つまり線形時間となります。</span><span class="sxs-lookup"><span data-stu-id="691e7-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span> <span data-ttu-id="691e7-122">対応する Visual Basic の例でも、同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="691e7-122">A corresponding Visual Basic example would have the same performance profile.</span></span>  
  
 <span data-ttu-id="691e7-123">反復子の詳細については、「[yield](../../../../csharp/language-reference/keywords/yield.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691e7-123">For more information on iterators, see [yield](../../../../csharp/language-reference/keywords/yield.md).</span></span>  
  
 <span data-ttu-id="691e7-124">クエリの連結に関する詳細なチュートリアルについては、「[チュートリアル: クエリの連結](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="691e7-124">For a more detailed tutorial on chaining queries together, see [Tutorial: Chaining Queries Together](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="691e7-125">参照</span><span class="sxs-lookup"><span data-stu-id="691e7-125">See Also</span></span>  
 [<span data-ttu-id="691e7-126">パフォーマンス (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="691e7-126">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
