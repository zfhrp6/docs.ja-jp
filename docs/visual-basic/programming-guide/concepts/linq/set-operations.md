---
title: "セット操作 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="8104a-102">セット操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8104a-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="8104a-103">LINQ のセット操作は、同一または別個のコレクション (またはセット) に等しい要素があるかどうかに基づいて、結果を生成するクエリ操作です。</span><span class="sxs-lookup"><span data-stu-id="8104a-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="8104a-104">次のセクションでは、セット操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="8104a-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8104a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8104a-105">Methods</span></span>  
  
|<span data-ttu-id="8104a-106">メソッド名</span><span class="sxs-lookup"><span data-stu-id="8104a-106">Method Name</span></span>|<span data-ttu-id="8104a-107">説明</span><span class="sxs-lookup"><span data-stu-id="8104a-107">Description</span></span>|<span data-ttu-id="8104a-108">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="8104a-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8104a-109">説明</span><span class="sxs-lookup"><span data-stu-id="8104a-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="8104a-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="8104a-110">Distinct</span></span>|<span data-ttu-id="8104a-111">コレクションから重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="8104a-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8104a-112">除く</span><span class="sxs-lookup"><span data-stu-id="8104a-112">Except</span></span>|<span data-ttu-id="8104a-113">差集合 (一方のコレクションにだけ存在し、もう一方のコレクションには出現しない要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="8104a-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="8104a-114">該当なし。</span><span class="sxs-lookup"><span data-stu-id="8104a-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8104a-115">交差</span><span class="sxs-lookup"><span data-stu-id="8104a-115">Intersect</span></span>|<span data-ttu-id="8104a-116">積集合 (2 つのコレクションのそれぞれに出現する要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="8104a-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="8104a-117">該当なし。</span><span class="sxs-lookup"><span data-stu-id="8104a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8104a-118">和集合</span><span class="sxs-lookup"><span data-stu-id="8104a-118">Union</span></span>|<span data-ttu-id="8104a-119">和集合 (2 つのコレクションのどちらかに出現する一意の要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="8104a-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="8104a-120">該当なし。</span><span class="sxs-lookup"><span data-stu-id="8104a-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="8104a-121">セット操作の比較</span><span class="sxs-lookup"><span data-stu-id="8104a-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="8104a-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="8104a-122">Distinct</span></span>  
 <span data-ttu-id="8104a-123">次の図は、文字のシーケンスに対する <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> メソッドの動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="8104a-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="8104a-124">返されたシーケンスには、入力シーケンスからの一意の要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="8104a-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="8104a-125">![Distinct&#40;&#41; の動作を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="8104a-125">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="8104a-126">除く</span><span class="sxs-lookup"><span data-stu-id="8104a-126">Except</span></span>  
 <span data-ttu-id="8104a-127"><xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> の動作を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="8104a-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8104a-128">返されたシーケンスには、1 つ目の入力シーケンスのうち、2 つ目の入力シーケンスには存在しない要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="8104a-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="8104a-129">![Except&#40;&#41; のアクションを示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="8104a-129">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="8104a-130">交差</span><span class="sxs-lookup"><span data-stu-id="8104a-130">Intersect</span></span>  
 <span data-ttu-id="8104a-131"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> の動作を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="8104a-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8104a-132">返されたシーケンスには、両方の入力シーケンスに共通する要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="8104a-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="8104a-133">![2 つのシーケンスの交差部分を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="8104a-133">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="8104a-134">和集合</span><span class="sxs-lookup"><span data-stu-id="8104a-134">Union</span></span>  
 <span data-ttu-id="8104a-135">次の図は、2 つの文字シーケンスに対する和集合演算を示しています。</span><span class="sxs-lookup"><span data-stu-id="8104a-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="8104a-136">返されたシーケンスには、両方の入力シーケンスからの一意の要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="8104a-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="8104a-137">![2 つのシーケンスの結合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="8104a-137">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="8104a-138">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="8104a-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="8104a-139">次の例では、`Distinct`を整数のリストから一意の番号を返す LINQ クエリ内の句。</span><span class="sxs-lookup"><span data-stu-id="8104a-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8104a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="8104a-140">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="8104a-141">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8104a-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="8104a-142">Distinct 句</span><span class="sxs-lookup"><span data-stu-id="8104a-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="8104a-143">方法: 結合および比較文字列のコレクションに (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8104a-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="8104a-144">方法: 2 つのリスト (LINQ) (Visual Basic) の差集合を検索</span><span class="sxs-lookup"><span data-stu-id="8104a-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
