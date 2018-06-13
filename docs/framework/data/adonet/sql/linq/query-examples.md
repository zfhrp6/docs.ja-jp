---
title: クエリの例
ms.date: 03/30/2017
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
ms.openlocfilehash: b7fe03a951b6b8cfccc0c0bc4a1ccfc90e903dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362628"
---
# <a name="query-examples"></a><span data-ttu-id="7174d-102">クエリの例</span><span class="sxs-lookup"><span data-stu-id="7174d-102">Query Examples</span></span>
<span data-ttu-id="7174d-103">このセクションでは、一般的な Visual Basic および c# の例を示します[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]クエリ。</span><span class="sxs-lookup"><span data-stu-id="7174d-103">This section provides Visual Basic and C# examples of typical [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries.</span></span> <span data-ttu-id="7174d-104">Visual Studio を使用している開発者は、サンプルのセクションで、使用可能なサンプル ソリューションでより多くの例を参照できます。</span><span class="sxs-lookup"><span data-stu-id="7174d-104">Developers using Visual Studio can find many more examples in a sample solution available in the Samples section.</span></span> <span data-ttu-id="7174d-105">詳細については、次を参照してください。[サンプル](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7174d-105">For more information, see [Samples](../../../../../../docs/framework/data/adonet/sql/linq/samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7174d-106">*db*のコード例でよく使用されて[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメント。</span><span class="sxs-lookup"><span data-stu-id="7174d-106">*db* is often used in code examples in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation.</span></span> <span data-ttu-id="7174d-107">*db*のインスタンスであると見なされます、 *Northwind*から継承されるクラスが<xref:System.Data.Linq.DataContext>です。</span><span class="sxs-lookup"><span data-stu-id="7174d-107">*db* is assumed to be an instance of a *Northwind* class, which inherits from <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7174d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7174d-108">In This Section</span></span>  
 [<span data-ttu-id="7174d-109">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="7174d-109">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <span data-ttu-id="7174d-110"><xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> などの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-110">Describes how to use <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, and so forth.</span></span>  
  
 [<span data-ttu-id="7174d-111">シーケンスの最初の要素の取得</span><span class="sxs-lookup"><span data-stu-id="7174d-111">Return the First Element in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <span data-ttu-id="7174d-112"><xref:System.Linq.Enumerable.First%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-112">Provides examples of using <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-113">シーケンスの要素の取得またはスキップ</span><span class="sxs-lookup"><span data-stu-id="7174d-113">Return Or Skip Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <span data-ttu-id="7174d-114"><xref:System.Linq.Enumerable.Take%2A> および <xref:System.Linq.Enumerable.Skip%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-114">Provides examples of using <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-115">シーケンスの要素の並べ替え</span><span class="sxs-lookup"><span data-stu-id="7174d-115">Sort Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <span data-ttu-id="7174d-116"><xref:System.Linq.Enumerable.OrderBy%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-116">Provides examples of using <xref:System.Linq.Enumerable.OrderBy%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-117">シーケンスの要素のグループ化</span><span class="sxs-lookup"><span data-stu-id="7174d-117">Group Elements in a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <span data-ttu-id="7174d-118"><xref:System.Linq.Enumerable.GroupBy%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-118">Provides examples of using <xref:System.Linq.Enumerable.GroupBy%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-119">シーケンスからの重複する要素の削除</span><span class="sxs-lookup"><span data-stu-id="7174d-119">Eliminate Duplicate Elements from a Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <span data-ttu-id="7174d-120"><xref:System.Linq.Enumerable.Distinct%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-120">Provides examples of using <xref:System.Linq.Enumerable.Distinct%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-121">シーケンスのすべての要素が条件を満たしているかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="7174d-121">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <span data-ttu-id="7174d-122"><xref:System.Linq.Enumerable.All%2A> および <xref:System.Linq.Enumerable.Any%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-122">Provides examples of using <xref:System.Linq.Enumerable.All%2A> and <xref:System.Linq.Enumerable.Any%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-123">2 つのシーケンスの連結</span><span class="sxs-lookup"><span data-stu-id="7174d-123">Concatenate Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <span data-ttu-id="7174d-124"><xref:System.Linq.Enumerable.Concat%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-124">Provides examples of using <xref:System.Linq.Enumerable.Concat%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-125">2 つのシーケンスの差集合の取得</span><span class="sxs-lookup"><span data-stu-id="7174d-125">Return the Set Difference Between Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <span data-ttu-id="7174d-126"><xref:System.Linq.Enumerable.Except%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-126">Provides examples of using <xref:System.Linq.Enumerable.Except%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-127">2 つのシーケンスの積集合の取得</span><span class="sxs-lookup"><span data-stu-id="7174d-127">Return the Set Intersection of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <span data-ttu-id="7174d-128"><xref:System.Linq.Enumerable.Intersect%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-128">Provides examples of using <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-129">2 つのシーケンスの和集合の取得</span><span class="sxs-lookup"><span data-stu-id="7174d-129">Return the Set Union of Two Sequences</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <span data-ttu-id="7174d-130"><xref:System.Linq.Enumerable.Union%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-130">Provides examples of using <xref:System.Linq.Enumerable.Union%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-131">方法 : シーケンスを配列に変換する</span><span class="sxs-lookup"><span data-stu-id="7174d-131">Convert a Sequence to an Array</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <span data-ttu-id="7174d-132"><xref:System.Linq.Enumerable.ToArray%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-132">Provides examples of using <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-133">ジェネリック リストへのシーケンスの変換</span><span class="sxs-lookup"><span data-stu-id="7174d-133">Convert a Sequence to a Generic List</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <span data-ttu-id="7174d-134"><xref:System.Linq.Enumerable.ToList%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-134">Provides examples of using <xref:System.Linq.Enumerable.ToList%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-135">汎用 IEnumerable への型の変換</span><span class="sxs-lookup"><span data-stu-id="7174d-135">Convert a Type to a Generic IEnumerable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <span data-ttu-id="7174d-136"><xref:System.Linq.Enumerable.AsEnumerable%2A> の使用例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-136">Provides examples of using <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span></span>  
  
 [<span data-ttu-id="7174d-137">結合およびクロス積クエリの作成</span><span class="sxs-lookup"><span data-stu-id="7174d-137">Formulate Joins and Cross-Product Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 <span data-ttu-id="7174d-138">`from` 句、`where` 句、および `select` 句で外部キーを移動する方法の例を示して説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-138">Provides examples of using foreign-key navigation in the `from`, `where`, and `select` clauses.</span></span>  
  
 [<span data-ttu-id="7174d-139">射影の作成</span><span class="sxs-lookup"><span data-stu-id="7174d-139">Formulate Projections</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 <span data-ttu-id="7174d-140">結合の例を示します`select`と他の機能 (たとえば、*匿名型*) クエリ射影を作成します。</span><span class="sxs-lookup"><span data-stu-id="7174d-140">Provides examples of combining `select` with other features (for example, *anonymous types*) to form query projections.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7174d-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="7174d-141">Related Sections</span></span>  
 [<span data-ttu-id="7174d-142">標準クエリ演算子の概要</span><span class="sxs-lookup"><span data-stu-id="7174d-142">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 <span data-ttu-id="7174d-143">標準クエリ演算子の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-143">Explains the concept of standard query operators.</span></span>  
  
 [<span data-ttu-id="7174d-144">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="7174d-144">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 <span data-ttu-id="7174d-145">クエリに関する概念が [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でどのように使用されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="7174d-145">Explains how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uses concepts that apply to queries.</span></span>  
  
 [<span data-ttu-id="7174d-146">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7174d-146">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="7174d-147">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に関連するプログラミングの概念を説明するトピックへのポータルです。</span><span class="sxs-lookup"><span data-stu-id="7174d-147">Provides a portal to topics that explain programming concepts related to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
