---
title: クエリ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [Visual Basic]
- LINQ, queries
ms.assetid: 8edc717c-4a24-4cbc-9c16-11f479c935db
ms.openlocfilehash: abe54fe163919c6ad6b746d70baac2482e80b948
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="queries-visual-basic"></a><span data-ttu-id="65f33-102">クエリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65f33-102">Queries (Visual Basic)</span></span>
<span data-ttu-id="65f33-103">Visual Basic では、作成することができます[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]コード内の式。</span><span class="sxs-lookup"><span data-stu-id="65f33-103">Visual Basic enables you to create [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="65f33-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="65f33-104">In This Section</span></span>  
 [<span data-ttu-id="65f33-105">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="65f33-105">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 <span data-ttu-id="65f33-106">について説明します、`Aggregate`句は、1 つまたは複数の集計関数をコレクションに適用します。</span><span class="sxs-lookup"><span data-stu-id="65f33-106">Describes the `Aggregate` clause, which applies one or more aggregate functions to a collection.</span></span>  
  
 [<span data-ttu-id="65f33-107">Distinct 句</span><span class="sxs-lookup"><span data-stu-id="65f33-107">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 <span data-ttu-id="65f33-108">について説明します、`Distinct`句は、クエリの結果で、重複を回避するのには、現在の範囲変数の値を制限します。</span><span class="sxs-lookup"><span data-stu-id="65f33-108">Describes the `Distinct` clause, which restricts the values of the current range variable to eliminate duplicate values in query results.</span></span>  
  
 [<span data-ttu-id="65f33-109">From 句</span><span class="sxs-lookup"><span data-stu-id="65f33-109">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 <span data-ttu-id="65f33-110">について説明します、`From`句は、コレクションと、クエリの範囲変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="65f33-110">Describes the `From` clause, which specifies a collection and a range variable for a query.</span></span>  
  
 [<span data-ttu-id="65f33-111">Group By 句</span><span class="sxs-lookup"><span data-stu-id="65f33-111">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)  
 <span data-ttu-id="65f33-112">について説明します、`Group By`句では、クエリ結果の要素をグループ化し、各グループに集計関数を適用するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="65f33-112">Describes the `Group By` clause, which groups the elements of a query result and can be used to apply aggregate functions to each group.</span></span>  
  
 [<span data-ttu-id="65f33-113">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="65f33-113">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 <span data-ttu-id="65f33-114">について説明します、`Group Join`句は、次の 2 つのコレクションを単一の階層コレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="65f33-114">Describes the `Group Join` clause, which combines two collections into a single hierarchical collection.</span></span>  
  
 [<span data-ttu-id="65f33-115">Join 句</span><span class="sxs-lookup"><span data-stu-id="65f33-115">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 <span data-ttu-id="65f33-116">について説明します、`Join`句は、次の 2 つのコレクションを 1 つのコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="65f33-116">Describes the `Join` clause, which combines two collections into a single collection.</span></span>  
  
 [<span data-ttu-id="65f33-117">Let 句</span><span class="sxs-lookup"><span data-stu-id="65f33-117">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 <span data-ttu-id="65f33-118">について説明します、`Let`句では、値を計算し、クエリ内の新しい変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="65f33-118">Describes the `Let` clause, which computes a value and assigns it to a new variable in the query.</span></span>  
  
 [<span data-ttu-id="65f33-119">Order By 句</span><span class="sxs-lookup"><span data-stu-id="65f33-119">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 <span data-ttu-id="65f33-120">について説明します、`Order By`句は、クエリ内の列の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="65f33-120">Describes the `Order By` clause, which specifies the sort order for columns in a query.</span></span>  
  
 [<span data-ttu-id="65f33-121">Select 句</span><span class="sxs-lookup"><span data-stu-id="65f33-121">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 <span data-ttu-id="65f33-122">について説明します、`Select`句は、クエリの範囲変数のセットを宣言します。</span><span class="sxs-lookup"><span data-stu-id="65f33-122">Describes the `Select` clause, which declares a set of range variables for a query.</span></span>  
  
 [<span data-ttu-id="65f33-123">Skip 句</span><span class="sxs-lookup"><span data-stu-id="65f33-123">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 <span data-ttu-id="65f33-124">について説明します、`Skip`句では、指定したコレクション内の要素数をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="65f33-124">Describes the `Skip` clause, which bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="65f33-125">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="65f33-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 <span data-ttu-id="65f33-126">について説明します、`Skip While`句は、指定した条件である限り、コレクション内の要素をバイパス`true`し、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="65f33-126">Describes the `Skip While` clause, which bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="65f33-127">Take 句</span><span class="sxs-lookup"><span data-stu-id="65f33-127">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 <span data-ttu-id="65f33-128">について説明します、`Take`句は、コレクションの先頭から指定した数の連続する要素を返します。</span><span class="sxs-lookup"><span data-stu-id="65f33-128">Describes the `Take` clause, which returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
 [<span data-ttu-id="65f33-129">Take While 句</span><span class="sxs-lookup"><span data-stu-id="65f33-129">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 <span data-ttu-id="65f33-130">について説明します、`Take While`句は、指定された条件が限り、コレクション内の要素を含む`true`し、残りの要素をバイパスします。</span><span class="sxs-lookup"><span data-stu-id="65f33-130">Describes the `Take While` clause, which includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
 [<span data-ttu-id="65f33-131">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="65f33-131">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 <span data-ttu-id="65f33-132">について説明します、`Where`句は、クエリのフィルター処理条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="65f33-132">Describes the `Where` clause, which specifies a filtering condition for a query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f33-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="65f33-133">See Also</span></span>  
 [<span data-ttu-id="65f33-134">LINQ</span><span class="sxs-lookup"><span data-stu-id="65f33-134">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="65f33-135">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="65f33-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
