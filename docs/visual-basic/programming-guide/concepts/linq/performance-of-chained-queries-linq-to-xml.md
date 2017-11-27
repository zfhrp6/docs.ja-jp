---
title: "連結クエリ (LINQ to XML) のパフォーマンス (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 281eb8ea62760507da991ea878270befe458bb38
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="f2f1c-102">連結クエリ (LINQ to XML) のパフォーマンス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f1c-102">Performance of Chained Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f2f1c-103">LINQ (および LINQ to XML) の重要な利点の 1 つは、連結クエリが、大きい複雑な単一クエリと同様のパフォーマンスを発揮できるという点です。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-103">One of the most important benefits of LINQ (and LINQ to XML) is that chained queries can perform as well as a single larger, more complicated query.</span></span>  
  
 <span data-ttu-id="f2f1c-104">連結クエリとは、別のクエリをソースとして使用するクエリです。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-104">A chained query is a query that uses another query as its source.</span></span> <span data-ttu-id="f2f1c-105">たとえば、次の単純なコードでは、`query2` のソースとして `query1` があります。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-105">For example, in the following simple code, `query2` has `query1` as its source:</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 <span data-ttu-id="f2f1c-106">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-106">This example produces the following output:</span></span>  
  
```  
4  
```  
  
 <span data-ttu-id="f2f1c-107">この連結クエリは、リンク リストの反復と同じパフォーマンス プロファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-107">This chained query provides the same performance profile as iterating through a linked list.</span></span>  
  
-   <span data-ttu-id="f2f1c-108"><xref:System.Xml.Linq.XContainer.Elements%2A> 軸のパフォーマンスは、基本的にリンク リストの反復と同じです。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-108">The <xref:System.Xml.Linq.XContainer.Elements%2A> axis has essentially the same performance as iterating through a linked list.</span></span> <span data-ttu-id="f2f1c-109"><xref:System.Xml.Linq.XContainer.Elements%2A> は、遅延実行のある反復子として実装されます。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-109"><xref:System.Xml.Linq.XContainer.Elements%2A> is implemented as an iterator with deferred execution.</span></span> <span data-ttu-id="f2f1c-110">つまり、リンク リストの反復の他に、反復子オブジェクトの割り当てや実行状態の追跡などの作業をします。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-110">This means that it does some work in addition to iterating through the linked list, such as allocating the iterator object and keeping track of execution state.</span></span> <span data-ttu-id="f2f1c-111">この作業は、反復子の設定時に行われる作業と、各反復中に行われる作業の 2 つのカテゴリに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-111">This work can be divided into two categories: the work that is done at the time the iterator is set up, and the work that is done during each iteration.</span></span> <span data-ttu-id="f2f1c-112">設定作業は一定量の小さい作業であり、各反復中に行われる作業はソース コレクションの項目数に比例します。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-112">The setup work is a small, fixed amount of work and the work done during each iteration is proportional to the number of items in the source collection.</span></span>  
  
-   <span data-ttu-id="f2f1c-113">`query1` では、`Where` 句によってクエリは <xref:System.Linq.Enumerable.Where%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-113">In `query1`, the `Where` clause causes the query to call the <xref:System.Linq.Enumerable.Where%2A> method.</span></span> <span data-ttu-id="f2f1c-114">このメソッドも反復子として実装されています。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-114">This method is also implemented as an iterator.</span></span> <span data-ttu-id="f2f1c-115">設定作業は、ラムダ式を参照するデリゲートのインスタンス化と、反復子の通常の設定から成ります。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-115">The setup work consists of instantiating the delegate that will reference the lambda expression, plus the normal setup for an iterator.</span></span> <span data-ttu-id="f2f1c-116">反復ごとに、デリゲートが呼び出されて述語を実行します。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-116">With each iteration, the delegate is called to execute the predicate.</span></span> <span data-ttu-id="f2f1c-117">設定作業と、各反復中に行われる作業は、軸の反復中に行われる作業に似ています。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-117">The setup work and the work done during each iteration is the similar to the work done while iterating through the axis.</span></span>  
  
-   <span data-ttu-id="f2f1c-118">`query1` では、SELECT 句によってクエリが <xref:System.Linq.Enumerable.Select%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-118">In `query1`, the select clause causes the query to call the <xref:System.Linq.Enumerable.Select%2A> method.</span></span> <span data-ttu-id="f2f1c-119">このメソッドには <xref:System.Linq.Enumerable.Where%2A> メソッドと同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-119">This method has the same performance profile as the <xref:System.Linq.Enumerable.Where%2A> method.</span></span>  
  
-   <span data-ttu-id="f2f1c-120">`query2` では、`Where` 句と `Select` 句の両方に `query1` と同じパフォーマンス プロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-120">In `query2`, both the `Where` clause and the `Select` clause have the same performance profile as in `query1`.</span></span>  
  
 <span data-ttu-id="f2f1c-121">したがって、`query2` の反復は最初のクエリのソースにある項目数に直接比例します。つまり線形時間となります。</span><span class="sxs-lookup"><span data-stu-id="f2f1c-121">The iteration through `query2` is therefore directly proportional to the number of items in the source of the first query, in other words, linear time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f1c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2f1c-122">See Also</span></span>  
 [<span data-ttu-id="f2f1c-123">パフォーマンス (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2f1c-123">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
