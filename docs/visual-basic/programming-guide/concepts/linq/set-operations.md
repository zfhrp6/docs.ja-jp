---
title: "セット操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2b9fd7ec122fff2601296ae3a46bb7607b2b32ef
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="80e92-102">集合演算 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80e92-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="80e92-103">LINQ のセット操作は、同じまたは別のコレクション (またはセット) 内に等しい要素が存在するかに基づいて、結果セットを生成するクエリ操作を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80e92-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="80e92-104">次のセクションでは、集合演算を実行する標準クエリ演算子のメソッドが一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="80e92-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80e92-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="80e92-105">Methods</span></span>  
  
|<span data-ttu-id="80e92-106">メソッド名</span><span class="sxs-lookup"><span data-stu-id="80e92-106">Method Name</span></span>|<span data-ttu-id="80e92-107">説明</span><span class="sxs-lookup"><span data-stu-id="80e92-107">Description</span></span>|<span data-ttu-id="80e92-108">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="80e92-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="80e92-109">説明</span><span class="sxs-lookup"><span data-stu-id="80e92-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="80e92-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="80e92-110">Distinct</span></span>|<span data-ttu-id="80e92-111">重複するコレクションから値を削除します。</span><span class="sxs-lookup"><span data-stu-id="80e92-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<span data-ttu-id="80e92-112"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-112"><xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="80e92-113"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-113"><xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="80e92-114">除く</span><span class="sxs-lookup"><span data-stu-id="80e92-114">Except</span></span>|<span data-ttu-id="80e92-115">差集合を&1; つのコレクションのうち、2 番目のコレクションに表示されない要素を返します。</span><span class="sxs-lookup"><span data-stu-id="80e92-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="80e92-116">該当なし。</span><span class="sxs-lookup"><span data-stu-id="80e92-116">Not applicable.</span></span>|<span data-ttu-id="80e92-117"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-117"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="80e92-118"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-118"><xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="80e92-119">交差</span><span class="sxs-lookup"><span data-stu-id="80e92-119">Intersect</span></span>|<span data-ttu-id="80e92-120">積集合、2 つのコレクションのそれぞれに出現する要素を返します。</span><span class="sxs-lookup"><span data-stu-id="80e92-120">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="80e92-121">該当なし。</span><span class="sxs-lookup"><span data-stu-id="80e92-121">Not applicable.</span></span>|<span data-ttu-id="80e92-122"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-122"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="80e92-123"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-123"><xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="80e92-124">和集合</span><span class="sxs-lookup"><span data-stu-id="80e92-124">Union</span></span>|<span data-ttu-id="80e92-125">和集合を&2; つのコレクションのいずれかで表示されている一意の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="80e92-125">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="80e92-126">該当なし。</span><span class="sxs-lookup"><span data-stu-id="80e92-126">Not applicable.</span></span>|<span data-ttu-id="80e92-127"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-127"><xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="80e92-128"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="80e92-128"><xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></span></span>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="80e92-129">セット操作の比較</span><span class="sxs-lookup"><span data-stu-id="80e92-129">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="80e92-130">Distinct</span><span class="sxs-lookup"><span data-stu-id="80e92-130">Distinct</span></span>  
 <span data-ttu-id="80e92-131">次の図の動作を示しています、<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>メソッドを文字のシーケンス</xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="80e92-131">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> method on a sequence of characters.</span></span> <span data-ttu-id="80e92-132">返されるシーケンスには、入力シーケンスから一意の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="80e92-132">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="80e92-133">![Distinct() の動作を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "個別")</span><span class="sxs-lookup"><span data-stu-id="80e92-133">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="80e92-134">除く</span><span class="sxs-lookup"><span data-stu-id="80e92-134">Except</span></span>  
 <span data-ttu-id="80e92-135">次の図は、 <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>。</xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="80e92-135">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="80e92-136">返されるシーケンスには、2 番目の入力シーケンスに含まれていない最初の入力シーケンスから要素のみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="80e92-136">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="80e92-137">![Except() のアクションを示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="80e92-137">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="80e92-138">交差</span><span class="sxs-lookup"><span data-stu-id="80e92-138">Intersect</span></span>  
 <span data-ttu-id="80e92-139">次の図は、 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>。</xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="80e92-139">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="80e92-140">返されるシーケンスには、入力シーケンスの両方に共通する要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="80e92-140">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="80e92-141">![2 つのシーケンスの積集合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "交差しています。")</span><span class="sxs-lookup"><span data-stu-id="80e92-141">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="80e92-142">和集合</span><span class="sxs-lookup"><span data-stu-id="80e92-142">Union</span></span>  
 <span data-ttu-id="80e92-143">次の図は、文字の&2; つのシーケンスの和集合演算を示しています。</span><span class="sxs-lookup"><span data-stu-id="80e92-143">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="80e92-144">返されるシーケンスには、両方の入力シーケンスから一意の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="80e92-144">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="80e92-145">![2 つのシーケンスの和集合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="80e92-145">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="80e92-146">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="80e92-146">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="80e92-147">次の例では、`Distinct`整数のリストから一意の番号を返す LINQ クエリ句で使用します。</span><span class="sxs-lookup"><span data-stu-id="80e92-147">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 <span data-ttu-id="80e92-148">[!code-vb[CsLINQSetOps&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="80e92-148">[!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e92-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="80e92-149">See Also</span></span>  
 <span data-ttu-id="80e92-150"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="80e92-150"><xref:System.Linq></span></span>   
<span data-ttu-id="80e92-151"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="80e92-151"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="80e92-152"> [Distinct 句](../../../../visual-basic/language-reference/queries/distinct-clause.md) </span><span class="sxs-lookup"><span data-stu-id="80e92-152"> [Distinct Clause](../../../../visual-basic/language-reference/queries/distinct-clause.md) </span></span>  
<span data-ttu-id="80e92-153"> [方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span><span class="sxs-lookup"><span data-stu-id="80e92-153"> [How to: Combine and Compare String Collections (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span></span>  
<span data-ttu-id="80e92-154"> [方法:&2; つのリスト (LINQ) (Visual Basic) の差集合を検索](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span><span class="sxs-lookup"><span data-stu-id="80e92-154"> [How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)</span></span>
