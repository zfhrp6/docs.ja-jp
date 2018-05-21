---
title: カスタム結合操作の実行
description: カスタム結合操作を実行する方法。
ms.date: 12/1/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: df80f4382ad5fa96fcdc41b338cbb53a3d8e6cb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="7dcb1-103">カスタム結合操作の実行</span><span class="sxs-lookup"><span data-stu-id="7dcb1-103">Perform custom join operations</span></span>

<span data-ttu-id="7dcb1-104">この例では、`join` 句では実現できない結合操作を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-104">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="7dcb1-105">クエリ式の `join` 句は、最も一般的な種類の結合操作である等結合用に限定され、また、それを目的に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="7dcb1-106">等結合の実行時には、`join` 句を使用することで、ほとんどの場合に最適なパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="7dcb1-107">ただし、`join` 句は、次の場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-107">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="7dcb1-108">結合が非等値の式に基づいている場合 (非等結合)。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="7dcb1-109">結合が等値または非等値の複数の式に基づいている場合。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-109">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="7dcb1-110">結合操作の前に、右辺 (内部) のシーケンスに一時的な範囲変数を導入する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="7dcb1-111">等結合ではない結合を実行するには、複数の `from` 句を使用して、各データ ソースを個別に導入することができます。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-111">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="7dcb1-112">その後、`where` 句の述語式を各ソースの範囲変数に適用します。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="7dcb1-113">式は、メソッド呼び出しの形式にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-113">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7dcb1-114">このようなカスタム結合操作を、複数の `from` 句を使用した内部コレクションへのアクセスと混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-114">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="7dcb1-115">詳細については、「[join 句](../language-reference/keywords/join-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dcb1-116">例</span><span class="sxs-lookup"><span data-stu-id="7dcb1-116">Example</span></span>  
 <span data-ttu-id="7dcb1-117">次の例の最初のメソッドは、単純なクロス結合を示しています。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="7dcb1-118">クロス結合は、非常に大きな結果セットを生成することがあるので、注意して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="7dcb1-119">ただし、追加のクエリの実行対象となるソース シーケンスを作成するためのいくつかのシナリオでは便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="7dcb1-120">2 番目のメソッドは、左辺のカテゴリの一覧にカテゴリ ID が含まれているすべての製品のシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="7dcb1-121">`let` 句と `Contains` メソッドを使用して一時配列を作成していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="7dcb1-122">クエリの前に配列を作成し、最初の `from` 句を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7dcb1-123">例</span><span class="sxs-lookup"><span data-stu-id="7dcb1-123">Example</span></span>  
 <span data-ttu-id="7dcb1-124">次の例では、クエリは一致するキーに基づいて 2 つのシーケンスを結合する必要があります。内部 (右辺) シーケンスでは、join 句自体より前にキーを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="7dcb1-125">この結合が `join` 句を使用して実行された場合は、要素ごとに `Split` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="7dcb1-126">複数の `from` 句を使用すると、クエリは、メソッドを繰り返し呼び出すことのオーバーヘッドを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="7dcb1-127">ただし、`join` は最適化されるため、この特定の場合には、複数の `from` 句を使用するよりも処理が速くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="7dcb1-128">結果は、主に、メソッド呼び出しにかかる負荷に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="7dcb1-128">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7dcb1-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dcb1-129">See also</span></span>  
 [<span data-ttu-id="7dcb1-130">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="7dcb1-130">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="7dcb1-131">join 句</span><span class="sxs-lookup"><span data-stu-id="7dcb1-131">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="7dcb1-132">join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="7dcb1-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
