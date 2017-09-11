---
title: "セット操作 (C#)"
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
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
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
ms.openlocfilehash: 121dcd4d41dcfea332c45031a5fbed594e2f1e3e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="set-operations-c"></a><span data-ttu-id="24a78-102">セット操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="24a78-102">Set Operations (C#)</span></span>
<span data-ttu-id="24a78-103">LINQ のセット操作は、同一または別個のコレクション (またはセット) に等しい要素があるかどうかに基づいて、結果を生成するクエリ操作です。</span><span class="sxs-lookup"><span data-stu-id="24a78-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="24a78-104">次のセクションでは、セット操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="24a78-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24a78-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="24a78-105">Methods</span></span>  
  
|<span data-ttu-id="24a78-106">メソッド名</span><span class="sxs-lookup"><span data-stu-id="24a78-106">Method Name</span></span>|<span data-ttu-id="24a78-107">説明</span><span class="sxs-lookup"><span data-stu-id="24a78-107">Description</span></span>|<span data-ttu-id="24a78-108">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="24a78-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="24a78-109">説明</span><span class="sxs-lookup"><span data-stu-id="24a78-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="24a78-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="24a78-110">Distinct</span></span>|<span data-ttu-id="24a78-111">コレクションから重複する値を削除します。</span><span class="sxs-lookup"><span data-stu-id="24a78-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="24a78-112">該当なし。</span><span class="sxs-lookup"><span data-stu-id="24a78-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName>|  
|<span data-ttu-id="24a78-113">除く</span><span class="sxs-lookup"><span data-stu-id="24a78-113">Except</span></span>|<span data-ttu-id="24a78-114">差集合 (一方のコレクションにだけ存在し、もう一方のコレクションには出現しない要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="24a78-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="24a78-115">該当なし。</span><span class="sxs-lookup"><span data-stu-id="24a78-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=fullName>|  
|<span data-ttu-id="24a78-116">交差</span><span class="sxs-lookup"><span data-stu-id="24a78-116">Intersect</span></span>|<span data-ttu-id="24a78-117">積集合 (2 つのコレクションのそれぞれに出現する要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="24a78-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="24a78-118">該当なし。</span><span class="sxs-lookup"><span data-stu-id="24a78-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName>|  
|<span data-ttu-id="24a78-119">和集合</span><span class="sxs-lookup"><span data-stu-id="24a78-119">Union</span></span>|<span data-ttu-id="24a78-120">和集合 (2 つのコレクションのどちらかに出現する一意の要素) を返します。</span><span class="sxs-lookup"><span data-stu-id="24a78-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="24a78-121">該当なし。</span><span class="sxs-lookup"><span data-stu-id="24a78-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=fullName>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="24a78-122">セット操作の比較</span><span class="sxs-lookup"><span data-stu-id="24a78-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="24a78-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="24a78-123">Distinct</span></span>  
 <span data-ttu-id="24a78-124">次の図は、文字のシーケンスに対する <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> メソッドの動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="24a78-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> method on a sequence of characters.</span></span> <span data-ttu-id="24a78-125">返されたシーケンスには、入力シーケンスからの一意の要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="24a78-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="24a78-126">![Distinct&#40;&#41; の動作を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="24a78-126">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="24a78-127">除く</span><span class="sxs-lookup"><span data-stu-id="24a78-127">Except</span></span>  
 <span data-ttu-id="24a78-128"><xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName> の動作を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="24a78-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="24a78-129">返されたシーケンスには、1 つ目の入力シーケンスのうち、2 つ目の入力シーケンスには存在しない要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="24a78-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="24a78-130">![Except&#40;&#41; のアクションを示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span><span class="sxs-lookup"><span data-stu-id="24a78-130">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="24a78-131">交差</span><span class="sxs-lookup"><span data-stu-id="24a78-131">Intersect</span></span>  
 <span data-ttu-id="24a78-132"><xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName> の動作を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="24a78-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="24a78-133">返されたシーケンスには、両方の入力シーケンスに共通する要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="24a78-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="24a78-134">![2 つのシーケンスの交差部分を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="24a78-134">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="24a78-135">和集合</span><span class="sxs-lookup"><span data-stu-id="24a78-135">Union</span></span>  
 <span data-ttu-id="24a78-136">次の図は、2 つの文字シーケンスに対する和集合演算を示しています。</span><span class="sxs-lookup"><span data-stu-id="24a78-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="24a78-137">返されたシーケンスには、両方の入力シーケンスからの一意の要素が格納されています。</span><span class="sxs-lookup"><span data-stu-id="24a78-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="24a78-138">![2 つのシーケンスの結合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="24a78-138">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a78-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="24a78-139">See Also</span></span>  
 <span data-ttu-id="24a78-140"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="24a78-140"><xref:System.Linq></span></span>   
 <span data-ttu-id="24a78-141">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="24a78-141">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="24a78-142">[方法: 文字列コレクションを結合および比較する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span><span class="sxs-lookup"><span data-stu-id="24a78-142">[How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md) </span></span>  
 [<span data-ttu-id="24a78-143">方法: 2 つのリストの差集合を見つける (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24a78-143">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)

