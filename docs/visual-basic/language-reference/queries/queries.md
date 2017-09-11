---
title: "クエリ (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic]
- LINQ, queries
ms.assetid: 8edc717c-4a24-4cbc-9c16-11f479c935db
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4a178714055076537033fbda32d7c7c1c544351d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="queries-visual-basic"></a><span data-ttu-id="b74e1-102">クエリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b74e1-102">Queries (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="b74e1-103">作成することができます[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]コード内の式。</span><span class="sxs-lookup"><span data-stu-id="b74e1-103"> enables you to create [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressions in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b74e1-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b74e1-104">In This Section</span></span>  
 [<span data-ttu-id="b74e1-105">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-105">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 <span data-ttu-id="b74e1-106">説明、`Aggregate`句は、1 つまたは複数の集計関数をコレクションに適用します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-106">Describes the `Aggregate` clause, which applies one or more aggregate functions to a collection.</span></span>  
  
 [<span data-ttu-id="b74e1-107">Distinct 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-107">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 <span data-ttu-id="b74e1-108">説明、`Distinct`句は、クエリ結果内で重複する値を排除する現在の範囲変数の値を制限します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-108">Describes the `Distinct` clause, which restricts the values of the current range variable to eliminate duplicate values in query results.</span></span>  
  
 [<span data-ttu-id="b74e1-109">From 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-109">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 <span data-ttu-id="b74e1-110">説明、`From`句は、コレクションとクエリの範囲変数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-110">Describes the `From` clause, which specifies a collection and a range variable for a query.</span></span>  
  
 [<span data-ttu-id="b74e1-111">Group By 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-111">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)  
 <span data-ttu-id="b74e1-112">説明、`Group By`句では、クエリ結果の要素をグループ化され、各グループに集計関数を適用するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b74e1-112">Describes the `Group By` clause, which groups the elements of a query result and can be used to apply aggregate functions to each group.</span></span>  
  
 [<span data-ttu-id="b74e1-113">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-113">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 <span data-ttu-id="b74e1-114">説明、`Group Join`句は、2 つのコレクションを&1; つの階層コレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-114">Describes the `Group Join` clause, which combines two collections into a single hierarchical collection.</span></span>  
  
 [<span data-ttu-id="b74e1-115">Join 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-115">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 <span data-ttu-id="b74e1-116">説明、`Join`句は、2 つのコレクションを&1; つのコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-116">Describes the `Join` clause, which combines two collections into a single collection.</span></span>  
  
 [<span data-ttu-id="b74e1-117">Let 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-117">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 <span data-ttu-id="b74e1-118">説明、`Let`句では、値を計算し、クエリ内の新しい変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b74e1-118">Describes the `Let` clause, which computes a value and assigns it to a new variable in the query.</span></span>  
  
 [<span data-ttu-id="b74e1-119">Order By 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-119">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 <span data-ttu-id="b74e1-120">説明、`Order By`句は、クエリ内の列の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-120">Describes the `Order By` clause, which specifies the sort order for columns in a query.</span></span>  
  
 [<span data-ttu-id="b74e1-121">Select 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-121">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 <span data-ttu-id="b74e1-122">説明、`Select`句は、クエリの範囲変数のセットを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-122">Describes the `Select` clause, which declares a set of range variables for a query.</span></span>  
  
 [<span data-ttu-id="b74e1-123">Skip 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-123">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 <span data-ttu-id="b74e1-124">説明、`Skip`句では、指定したコレクション内の要素数をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-124">Describes the `Skip` clause, which bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="b74e1-125">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 <span data-ttu-id="b74e1-126">説明、`Skip While`句は、指定された条件がである限り、コレクション内の要素をバイパス`true`し、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-126">Describes the `Skip While` clause, which bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
 [<span data-ttu-id="b74e1-127">Take 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-127">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 <span data-ttu-id="b74e1-128">説明、`Take`句は、コレクションの先頭から指定した数の連続する要素を返します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-128">Describes the `Take` clause, which returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
 [<span data-ttu-id="b74e1-129">Take While 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-129">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 <span data-ttu-id="b74e1-130">説明、`Take While`句は、指定された条件が限り、コレクション内の要素を含む`true`し、残りの要素をバイパスします。</span><span class="sxs-lookup"><span data-stu-id="b74e1-130">Describes the `Take While` clause, which includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
 [<span data-ttu-id="b74e1-131">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="b74e1-131">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 <span data-ttu-id="b74e1-132">説明、`Where`句は、クエリのフィルター条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="b74e1-132">Describes the `Where` clause, which specifies a filtering condition for a query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74e1-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b74e1-133">See Also</span></span>  
 <span data-ttu-id="b74e1-134">[LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="b74e1-134">[LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="b74e1-135"> [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b74e1-135"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
