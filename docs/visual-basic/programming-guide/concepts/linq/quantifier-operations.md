---
title: "量指定子操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
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
ms.openlocfilehash: 4e0c982508640ef1ecb47d477d3e9330198474ca
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="50199-102">量指定子操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50199-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="50199-103">量指定子操作を返す、<xref:System.Boolean>シーケンス内の要素の一部またはすべてが、条件を満たすかどうかを示す値</xref:System.Boolean>。</span><span class="sxs-lookup"><span data-stu-id="50199-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="50199-104">次の図は、2 つの異なるソース シーケンス上の&2; つの異なる量指定子操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="50199-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="50199-105">最初の操作が文字 'A' の&1; つ以上の要素のかどうか、結果を要求する`true`です。</span><span class="sxs-lookup"><span data-stu-id="50199-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="50199-106">2 番目の操作要求のかどうかは、すべての要素は文字 'A' され、結果は`true`です。</span><span class="sxs-lookup"><span data-stu-id="50199-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="50199-107">![LINQ 量指定子操作](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="50199-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="50199-108">量指定子操作を実行する標準クエリ演算子メソッドは、次のように記載されています。</span><span class="sxs-lookup"><span data-stu-id="50199-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50199-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="50199-109">Methods</span></span>  
  
|<span data-ttu-id="50199-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="50199-110">Method Name</span></span>|<span data-ttu-id="50199-111">説明</span><span class="sxs-lookup"><span data-stu-id="50199-111">Description</span></span>|<span data-ttu-id="50199-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="50199-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="50199-113">説明</span><span class="sxs-lookup"><span data-stu-id="50199-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="50199-114">すべて</span><span class="sxs-lookup"><span data-stu-id="50199-114">All</span></span>|<span data-ttu-id="50199-115">シーケンス内のすべての要素が条件を満たすかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="50199-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<span data-ttu-id="50199-116"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50199-116"><xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="50199-117"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50199-117"><xref:System.Linq.Queryable.All%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="50199-118">どれでも可</span><span class="sxs-lookup"><span data-stu-id="50199-118">Any</span></span>|<span data-ttu-id="50199-119">シーケンス内の各要素が条件を満たすかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="50199-119">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<span data-ttu-id="50199-120"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50199-120"><xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="50199-121"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50199-121"><xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="50199-122">内容</span><span class="sxs-lookup"><span data-stu-id="50199-122">Contains</span></span>|<span data-ttu-id="50199-123">指定した要素を格納するシーケンスがサポートされるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="50199-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="50199-124">該当なし。</span><span class="sxs-lookup"><span data-stu-id="50199-124">Not applicable.</span></span>|<span data-ttu-id="50199-125"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50199-125"><xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="50199-126"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50199-126"><xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="50199-127">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="50199-127">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="50199-128">これらの例を使用して、 `Aggregate` LINQ クエリでフィルター条件の一部として Visual Basic での句。</span><span class="sxs-lookup"><span data-stu-id="50199-128">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="50199-129">次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.All%2A>を持つペットは、指定された保有期間より古いすべての人をコレクションから返す拡張メソッド</xref:System.Linq.Enumerable.All%2A>。</span><span class="sxs-lookup"><span data-stu-id="50199-129">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 <span data-ttu-id="50199-130">[!code-vb[CsLINQAnyAll&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="50199-130">[!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]</span></span>  
  
 <span data-ttu-id="50199-131">次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.Any%2A>を少なくとも&1; つを所有するユーザーには pet をコレクションから返す拡張メソッドは、指定された保有期間より古い</xref:System.Linq.Enumerable.Any%2A>。</span><span class="sxs-lookup"><span data-stu-id="50199-131">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 <span data-ttu-id="50199-132">[!code-vb[CsLINQAnyAll&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="50199-132">[!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50199-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="50199-133">See Also</span></span>  
 <span data-ttu-id="50199-134"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="50199-134"><xref:System.Linq></span></span>   
<span data-ttu-id="50199-135"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="50199-135"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="50199-136"> [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="50199-136"> [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="50199-137"> [方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)</span><span class="sxs-lookup"><span data-stu-id="50199-137"> [How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)</span></span>
