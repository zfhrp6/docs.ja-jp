---
title: "From 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ecdc8b70fb1ae164a6c78998ce11db9938fbb56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="19031-102">From 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19031-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="19031-103">1 つまたは複数の範囲変数およびコレクションのクエリを指定します。</span><span class="sxs-lookup"><span data-stu-id="19031-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19031-104">構文</span><span class="sxs-lookup"><span data-stu-id="19031-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="19031-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="19031-105">Parts</span></span>  
  
|<span data-ttu-id="19031-106">用語</span><span class="sxs-lookup"><span data-stu-id="19031-106">Term</span></span>|<span data-ttu-id="19031-107">定義</span><span class="sxs-lookup"><span data-stu-id="19031-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="19031-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="19031-108">Required.</span></span> <span data-ttu-id="19031-109">A*範囲変数*コレクションの要素を反復処理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="19031-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="19031-110">各メンバーを参照する、範囲変数が使用される、`collection`を反復処理クエリとして、`collection`です。</span><span class="sxs-lookup"><span data-stu-id="19031-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="19031-111">列挙可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="19031-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="19031-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="19031-112">Optional.</span></span> <span data-ttu-id="19031-113">`element` の型。</span><span class="sxs-lookup"><span data-stu-id="19031-113">The type of `element`.</span></span> <span data-ttu-id="19031-114">ない場合は`type`が指定されているの種類`element`から推論される`collection`です。</span><span class="sxs-lookup"><span data-stu-id="19031-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="19031-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="19031-115">Required.</span></span> <span data-ttu-id="19031-116">コレクションを参照するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="19031-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="19031-117">列挙可能な型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="19031-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19031-118">コメント</span><span class="sxs-lookup"><span data-stu-id="19031-118">Remarks</span></span>  
 <span data-ttu-id="19031-119">`From`句を使用して、ソース データ クエリと、ソース コレクションから要素を参照するために使用される変数を識別します。</span><span class="sxs-lookup"><span data-stu-id="19031-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="19031-120">これらの変数といいます*範囲変数*です。</span><span class="sxs-lookup"><span data-stu-id="19031-120">These variables are called *range variables*.</span></span> <span data-ttu-id="19031-121">`From`句が必要な場合を除き、クエリ、`Aggregate`句を使用する集計された結果だけを返します。 クエリを識別します。</span><span class="sxs-lookup"><span data-stu-id="19031-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="19031-122">詳細については、次を参照してください。 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="19031-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="19031-123">複数を指定する`From`結合する複数のコレクションを識別するクエリ内の句。</span><span class="sxs-lookup"><span data-stu-id="19031-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="19031-124">複数のコレクションを指定すると、それらは別々 に反復処理、または関連している場合に参加することができます。</span><span class="sxs-lookup"><span data-stu-id="19031-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="19031-125">使用してコレクションに暗黙的に参加することができます、`Select`句、またはを使用して明示的に、`Join`または`Group Join`句。</span><span class="sxs-lookup"><span data-stu-id="19031-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="19031-126">代わりで指定できる複数の範囲変数とコレクション、1 つ`From`句は、各関連の範囲変数と、他のユーザーから、コンマで区切られたコレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="19031-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="19031-127">次のコード例は、両方の構文のオプションを示しています、`From`句。</span><span class="sxs-lookup"><span data-stu-id="19031-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 <span data-ttu-id="19031-128">`From`句のスコープに似ていますが、クエリのスコープを定義する、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="19031-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="19031-129">したがって、各`element`クエリのスコープの範囲変数は一意の名前を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="19031-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="19031-130">倍数を指定することができますので`From`、クエリは、後続の句`From`句できます内の範囲変数を参照してください、`From`以前、句、またはこれらの範囲変数を参照してできます`From`句。</span><span class="sxs-lookup"><span data-stu-id="19031-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="19031-131">たとえば、次の例、入れ子になった`From`2 番目の句内のコレクションは、最初の句の範囲変数のプロパティをに基づいて句。</span><span class="sxs-lookup"><span data-stu-id="19031-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 <span data-ttu-id="19031-132">各`From`句の後に、クエリを絞り込む追加のクエリ句の任意の組み合わせをできます。</span><span class="sxs-lookup"><span data-stu-id="19031-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="19031-133">次の方法でクエリを絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="19031-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="19031-134">使用して暗黙的に複数のコレクションを組み合わせて、`From`と`Select`句、またはを使用して明示的に、`Join`または`Group Join`句。</span><span class="sxs-lookup"><span data-stu-id="19031-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="19031-135">使用して、`Where`句をクエリの結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="19031-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="19031-136">使用して、結果を並べ替える、`Order By`句。</span><span class="sxs-lookup"><span data-stu-id="19031-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="19031-137">使用して同様の結果をグループ化、`Group By`句。</span><span class="sxs-lookup"><span data-stu-id="19031-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="19031-138">使用して、`Aggregate`句全体のクエリの結果を評価する集計関数を識別します。</span><span class="sxs-lookup"><span data-stu-id="19031-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="19031-139">使用して、`Let`句を反復変数の値は、コレクションではなく式によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="19031-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="19031-140">使用して、`Distinct`重複するクエリの結果を無視する句。</span><span class="sxs-lookup"><span data-stu-id="19031-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="19031-141">使用して返される結果の部分を特定、 `Skip`、 `Take`、 `Skip While`、および`Take While`句。</span><span class="sxs-lookup"><span data-stu-id="19031-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19031-142">例</span><span class="sxs-lookup"><span data-stu-id="19031-142">Example</span></span>  
 <span data-ttu-id="19031-143">次のクエリ式は、`From`範囲変数を宣言する句`cust`各`Customer`内のオブジェクト、`customers`コレクション。</span><span class="sxs-lookup"><span data-stu-id="19031-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="19031-144">`Where`句では、範囲変数を使用して、顧客に指定した領域から出力を制限します。</span><span class="sxs-lookup"><span data-stu-id="19031-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="19031-145">`For Each`ループでは、クエリ結果の各顧客の会社名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="19031-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19031-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="19031-146">See Also</span></span>  
 [<span data-ttu-id="19031-147">クエリ</span><span class="sxs-lookup"><span data-stu-id="19031-147">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="19031-148">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="19031-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="19031-149">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="19031-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="19031-150">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="19031-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="19031-151">Select 句</span><span class="sxs-lookup"><span data-stu-id="19031-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="19031-152">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="19031-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="19031-153">Aggregate 句</span><span class="sxs-lookup"><span data-stu-id="19031-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="19031-154">Distinct 句</span><span class="sxs-lookup"><span data-stu-id="19031-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="19031-155">Join 句</span><span class="sxs-lookup"><span data-stu-id="19031-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="19031-156">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="19031-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="19031-157">Order By 句</span><span class="sxs-lookup"><span data-stu-id="19031-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="19031-158">Let 句</span><span class="sxs-lookup"><span data-stu-id="19031-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="19031-159">Skip 句</span><span class="sxs-lookup"><span data-stu-id="19031-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="19031-160">Take 句</span><span class="sxs-lookup"><span data-stu-id="19031-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="19031-161">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="19031-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="19031-162">Take While 句</span><span class="sxs-lookup"><span data-stu-id="19031-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
