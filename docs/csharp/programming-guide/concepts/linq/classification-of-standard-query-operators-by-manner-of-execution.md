---
title: "実行方法による標準クエリ演算子の分類 (C#)"
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
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4217cbce36bc055cf8c6dde446df4d7b7394430d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a><span data-ttu-id="24e1e-102">実行方法による標準クエリ演算子の分類 (C#)</span><span class="sxs-lookup"><span data-stu-id="24e1e-102">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>
<span data-ttu-id="24e1e-103">標準クエリ演算子メソッドの LINQ to Objects 実装は、主に 2 とおりの方法 (即時と遅延) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-103">The LINQ to Objects implementations of the standard query operator methods execute in one of two main ways: immediate or deferred.</span></span> <span data-ttu-id="24e1e-104">遅延実行を使用するクエリ演算子は、さらに 2 つのカテゴリ (ストリーミングと非ストリーミング) に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-104">The query operators that use deferred execution can be additionally divided into two categories: streaming and non-streaming.</span></span> <span data-ttu-id="24e1e-105">それぞれのクエリ演算子がどのように動作するかを把握しておくと、指定したクエリの結果を理解するうえで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-105">If you know how the different query operators execute, it may help you understand the results that you get from a given query.</span></span> <span data-ttu-id="24e1e-106">これは、データ ソースが変更される場合や、別のクエリに基づいてさらにクエリを作成する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="24e1e-106">This is especially true if the data source is changing or if you are building a query on top of another query.</span></span> <span data-ttu-id="24e1e-107">このトピックでは、標準クエリ演算子を、その実行方法に基づいて分類します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-107">This topic classifies the standard query operators according to their manner of execution.</span></span>  
  
## <a name="manners-of-execution"></a><span data-ttu-id="24e1e-108">実行方法</span><span class="sxs-lookup"><span data-stu-id="24e1e-108">Manners of Execution</span></span>  
  
### <a name="immediate"></a><span data-ttu-id="24e1e-109">イミディエイト</span><span class="sxs-lookup"><span data-stu-id="24e1e-109">Immediate</span></span>  
 <span data-ttu-id="24e1e-110">即時実行とは、クエリが宣言されたコード内の位置で、データ ソースが読み取られ、演算が実行されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-110">Immediate execution means that the data source is read and the operation is performed at the point in the code where the query is declared.</span></span> <span data-ttu-id="24e1e-111">列挙できない単一の結果を返す標準クエリ演算子は、すべて即時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-111">All the standard query operators that return a single, non-enumerable result execute immediately.</span></span>  
  
### <a name="deferred"></a><span data-ttu-id="24e1e-112">遅延</span><span class="sxs-lookup"><span data-stu-id="24e1e-112">Deferred</span></span>  
 <span data-ttu-id="24e1e-113">遅延実行とは、クエリが宣言されたコード内の位置では演算が実行されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-113">Deferred execution means that the operation is not performed at the point in the code where the query is declared.</span></span> <span data-ttu-id="24e1e-114">演算は、`foreach` ステートメントを使用するなどの方法により、クエリ変数が列挙されたときにのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-114">The operation is performed only when the query variable is enumerated, for example by using a `foreach` statement.</span></span> <span data-ttu-id="24e1e-115">つまり、クエリの実行結果は、クエリの定義時ではなくクエリの実行時のデータ ソースの内容に依存します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-115">This means that the results of executing the query depend on the contents of the data source when the query is executed rather than when the query is defined.</span></span> <span data-ttu-id="24e1e-116">クエリ変数が複数回列挙される場合は、そのたびに結果が変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="24e1e-116">If the query variable is enumerated multiple times, the results might differ every time.</span></span> <span data-ttu-id="24e1e-117">戻り値の型が <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IOrderedEnumerable%601> の標準クエリ演算子は、ほとんどが遅延実行されます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-117">Almost all the standard query operators whose return type is <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IOrderedEnumerable%601> execute in a deferred manner.</span></span>  
  
 <span data-ttu-id="24e1e-118">遅延実行を使用するクエリ演算子は、さらにストリーミングか非ストリーミングに分類できます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-118">Query operators that use deferred execution can be additionally classified as streaming or non-streaming.</span></span>  
  
#### <a name="streaming"></a><span data-ttu-id="24e1e-119">ストリーム</span><span class="sxs-lookup"><span data-stu-id="24e1e-119">Streaming</span></span>  
 <span data-ttu-id="24e1e-120">ストリーミング演算子では、要素を生成する前にすべてのソース データを読み取る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="24e1e-120">Streaming operators do not have to read all the source data before they yield elements.</span></span> <span data-ttu-id="24e1e-121">実行時に、ストリーミング演算子は読み取ったソース要素ごとに演算を実行し、必要に応じて要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-121">At the time of execution, a streaming operator performs its operation on each source element as it is read and yields the element if appropriate.</span></span> <span data-ttu-id="24e1e-122">ストリーミング演算子は、結果の要素を生成できるまでソース要素の読み取りを続行します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-122">A streaming operator continues to read source elements until a result element can be produced.</span></span> <span data-ttu-id="24e1e-123">つまり、結果の要素を 1 つ生成するために複数のソース要素が読み取られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24e1e-123">This means that more than one source element might be read to produce one result element.</span></span>  
  
#### <a name="non-streaming"></a><span data-ttu-id="24e1e-124">非ストリーミング</span><span class="sxs-lookup"><span data-stu-id="24e1e-124">Non-Streaming</span></span>  
 <span data-ttu-id="24e1e-125">非ストリーミング演算子では、結果の要素を生成する前にすべてのソース データを読み取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="24e1e-125">Non-streaming operators must read all the source data before they can yield a result element.</span></span> <span data-ttu-id="24e1e-126">並べ替えやグループ化などの演算はこのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="24e1e-126">Operations such as sorting or grouping fall into this category.</span></span> <span data-ttu-id="24e1e-127">実行時に、非ストリーミング クエリ演算子はすべてのソース データを読み取ってデータ構造に格納し、演算を実行して結果の要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="24e1e-127">At the time of execution, non-streaming query operators read all the source data, put it into a data structure, perform the operation, and yield the resulting elements.</span></span>  
  
## <a name="classification-table"></a><span data-ttu-id="24e1e-128">分類表</span><span class="sxs-lookup"><span data-stu-id="24e1e-128">Classification Table</span></span>  
 <span data-ttu-id="24e1e-129">次の表では、各標準クエリ演算子メソッドを、その実行方法に基づいて分類しています。</span><span class="sxs-lookup"><span data-stu-id="24e1e-129">The following table classifies each standard query operator method according to its method of execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24e1e-130">2 つの列にマークが付けられている演算子では、2 つの入力シーケンスが演算に使用され、各シーケンスの評価は異なります。</span><span class="sxs-lookup"><span data-stu-id="24e1e-130">If an operator is marked in two columns, two input sequences are involved in the operation, and each sequence is evaluated differently.</span></span> <span data-ttu-id="24e1e-131">この場合、遅延実行のストリーミングで評価されるのは、常にパラメーター リストの最初のシーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="24e1e-131">In these cases, it is always the first sequence in the parameter list that is evaluated in a deferred, streaming manner.</span></span>  
  
|<span data-ttu-id="24e1e-132">標準クエリ演算子</span><span class="sxs-lookup"><span data-stu-id="24e1e-132">Standard Query Operator</span></span>|<span data-ttu-id="24e1e-133">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="24e1e-133">Return Type</span></span>|<span data-ttu-id="24e1e-134">即時実行</span><span class="sxs-lookup"><span data-stu-id="24e1e-134">Immediate Execution</span></span>|<span data-ttu-id="24e1e-135">遅延実行 (ストリーミング)</span><span class="sxs-lookup"><span data-stu-id="24e1e-135">Deferred Streaming Execution</span></span>|<span data-ttu-id="24e1e-136">遅延実行 (非ストリーミング)</span><span class="sxs-lookup"><span data-stu-id="24e1e-136">Deferred Non-Streaming Execution</span></span>|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|<span data-ttu-id="24e1e-137">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-137">TSource</span></span>|<span data-ttu-id="24e1e-138">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-138">X</span></span>|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|<span data-ttu-id="24e1e-139">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-139">X</span></span>|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|<span data-ttu-id="24e1e-140">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-140">X</span></span>|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-141">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-141">X</span></span>||  
|<xref:System.Linq.Enumerable.Average%2A>|<span data-ttu-id="24e1e-142">1 つの数値</span><span class="sxs-lookup"><span data-stu-id="24e1e-142">Single numeric value</span></span>|<span data-ttu-id="24e1e-143">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-143">X</span></span>|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-144">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-144">X</span></span>||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-145">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-145">X</span></span>||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|<span data-ttu-id="24e1e-146">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-146">X</span></span>|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|<span data-ttu-id="24e1e-147">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-147">X</span></span>|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-148">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-148">X</span></span>||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-149">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-149">X</span></span>||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|<span data-ttu-id="24e1e-150">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-150">TSource</span></span>|<span data-ttu-id="24e1e-151">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-151">X</span></span>|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|<span data-ttu-id="24e1e-152">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-152">TSource</span></span>|<span data-ttu-id="24e1e-153">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-153">X</span></span>|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="24e1e-154">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-154">X</span></span>|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-155">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-155">X</span></span>|<span data-ttu-id="24e1e-156">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-156">X</span></span>|  
|<xref:System.Linq.Enumerable.First%2A>|<span data-ttu-id="24e1e-157">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-157">TSource</span></span>|<span data-ttu-id="24e1e-158">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-158">X</span></span>|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|<span data-ttu-id="24e1e-159">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-159">TSource</span></span>|<span data-ttu-id="24e1e-160">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-160">X</span></span>|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||<span data-ttu-id="24e1e-161">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-161">X</span></span>|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-162">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-162">X</span></span>|<span data-ttu-id="24e1e-163">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-163">X</span></span>|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-164">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-164">X</span></span>|<span data-ttu-id="24e1e-165">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-165">X</span></span>|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-166">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-166">X</span></span>|<span data-ttu-id="24e1e-167">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-167">X</span></span>|  
|<xref:System.Linq.Enumerable.Last%2A>|<span data-ttu-id="24e1e-168">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-168">TSource</span></span>|<span data-ttu-id="24e1e-169">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-169">X</span></span>|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|<span data-ttu-id="24e1e-170">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-170">TSource</span></span>|<span data-ttu-id="24e1e-171">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-171">X</span></span>|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|<span data-ttu-id="24e1e-172">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-172">X</span></span>|||  
|<xref:System.Linq.Enumerable.Max%2A>|<span data-ttu-id="24e1e-173">1 つの数値、TSource、または TResult</span><span class="sxs-lookup"><span data-stu-id="24e1e-173">Single numeric value, TSource, or TResult</span></span>|<span data-ttu-id="24e1e-174">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-174">X</span></span>|||  
|<xref:System.Linq.Enumerable.Min%2A>|<span data-ttu-id="24e1e-175">1 つの数値、TSource、または TResult</span><span class="sxs-lookup"><span data-stu-id="24e1e-175">Single numeric value, TSource, or TResult</span></span>|<span data-ttu-id="24e1e-176">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-176">X</span></span>|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-177">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-177">X</span></span>||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||<span data-ttu-id="24e1e-178">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-178">X</span></span>|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||<span data-ttu-id="24e1e-179">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-179">X</span></span>|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-180">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-180">X</span></span>||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-181">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-181">X</span></span>||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||<span data-ttu-id="24e1e-182">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-182">X</span></span>|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-183">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-183">X</span></span>||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-184">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-184">X</span></span>||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|<span data-ttu-id="24e1e-185">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-185">X</span></span>|||  
|<xref:System.Linq.Enumerable.Single%2A>|<span data-ttu-id="24e1e-186">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-186">TSource</span></span>|<span data-ttu-id="24e1e-187">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-187">X</span></span>|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|<span data-ttu-id="24e1e-188">TSource</span><span class="sxs-lookup"><span data-stu-id="24e1e-188">TSource</span></span>|<span data-ttu-id="24e1e-189">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-189">X</span></span>|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-190">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-190">X</span></span>||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-191">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-191">X</span></span>||  
|<xref:System.Linq.Enumerable.Sum%2A>|<span data-ttu-id="24e1e-192">1 つの数値</span><span class="sxs-lookup"><span data-stu-id="24e1e-192">Single numeric value</span></span>|<span data-ttu-id="24e1e-193">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-193">X</span></span>|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-194">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-194">X</span></span>||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-195">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-195">X</span></span>||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||<span data-ttu-id="24e1e-196">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-196">X</span></span>|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||<span data-ttu-id="24e1e-197">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-197">X</span></span>|  
|<xref:System.Linq.Enumerable.ToArray%2A>|<span data-ttu-id="24e1e-198">TSource 配列</span><span class="sxs-lookup"><span data-stu-id="24e1e-198">TSource array</span></span>|<span data-ttu-id="24e1e-199">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-199">X</span></span>|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="24e1e-200">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-200">X</span></span>|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|<span data-ttu-id="24e1e-201">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-201">X</span></span>|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|<span data-ttu-id="24e1e-202">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-202">X</span></span>|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-203">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-203">X</span></span>||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||<span data-ttu-id="24e1e-204">X</span><span class="sxs-lookup"><span data-stu-id="24e1e-204">X</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="24e1e-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="24e1e-205">See Also</span></span>  
 <span data-ttu-id="24e1e-206"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="24e1e-206"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="24e1e-207">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="24e1e-207">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="24e1e-208">[標準クエリ演算子のクエリ式構文 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span><span class="sxs-lookup"><span data-stu-id="24e1e-208">[Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md) </span></span>  
 [<span data-ttu-id="24e1e-209">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="24e1e-209">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)

