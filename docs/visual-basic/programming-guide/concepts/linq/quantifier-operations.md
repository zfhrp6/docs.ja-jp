---
title: 量指定子操作 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0a0a5fae35a14ab6451f2f56fb2eedd92ac437e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="7e943-102">量指定子操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e943-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="7e943-103">量指定子操作は、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示す <xref:System.Boolean> 値を返します。</span><span class="sxs-lookup"><span data-stu-id="7e943-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="7e943-104">次の図は、2 つの異なるソース シーケンスに対する、2 つの異なる量指定子操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="7e943-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="7e943-105">最初の操作では、1 つ以上の要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="7e943-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="7e943-106">2 番目の操作では、すべての要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="7e943-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="7e943-107">![LINQ 量指定子操作](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="7e943-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="7e943-108">次のセクションでは、量指定子操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7e943-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e943-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="7e943-109">Methods</span></span>  
  
|<span data-ttu-id="7e943-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="7e943-110">Method Name</span></span>|<span data-ttu-id="7e943-111">説明</span><span class="sxs-lookup"><span data-stu-id="7e943-111">Description</span></span>|<span data-ttu-id="7e943-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="7e943-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="7e943-113">説明</span><span class="sxs-lookup"><span data-stu-id="7e943-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="7e943-114">すべて</span><span class="sxs-lookup"><span data-stu-id="7e943-114">All</span></span>|<span data-ttu-id="7e943-115">シーケンス内のすべての要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7e943-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e943-116">どれでも可</span><span class="sxs-lookup"><span data-stu-id="7e943-116">Any</span></span>|<span data-ttu-id="7e943-117">シーケンス内のいずれかの要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7e943-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7e943-118">内容</span><span class="sxs-lookup"><span data-stu-id="7e943-118">Contains</span></span>|<span data-ttu-id="7e943-119">指定した要素がシーケンスに格納されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7e943-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="7e943-120">該当なし。</span><span class="sxs-lookup"><span data-stu-id="7e943-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="7e943-121">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="7e943-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="7e943-122">これらの例を使用して、 `Aggregate` LINQ クエリのフィルター条件の一部として Visual Basic での句。</span><span class="sxs-lookup"><span data-stu-id="7e943-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="7e943-123">次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.All%2A>のペットは指定された有効期間より古いすべての人をコレクションから取得する拡張メソッド。</span><span class="sxs-lookup"><span data-stu-id="7e943-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="7e943-124">次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.Any%2A>を少なくとも 1 つ所有するユーザーにペットをコレクションから返す拡張メソッドが指定した期限を過ぎています。</span><span class="sxs-lookup"><span data-stu-id="7e943-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7e943-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e943-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="7e943-126">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e943-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="7e943-127">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="7e943-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="7e943-128">方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。</span><span class="sxs-lookup"><span data-stu-id="7e943-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
