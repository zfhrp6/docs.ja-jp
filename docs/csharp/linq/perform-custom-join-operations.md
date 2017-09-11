---
title: "カスタム結合操作の実行"
description: "カスタム結合操作を実行する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 51bdae75346022a7564fdb50e582c143e7762a1f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="0da11-104">カスタム結合操作の実行</span><span class="sxs-lookup"><span data-stu-id="0da11-104">Perform custom join operations</span></span>

<span data-ttu-id="0da11-105">この例では、`join` 句では実現できない結合操作を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0da11-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="0da11-106">クエリ式の `join` 句は、最も一般的な種類の結合操作である等結合用に限定され、また、それを目的に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="0da11-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="0da11-107">等結合の実行時には、`join` 句を使用することで、ほとんどの場合に最適なパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="0da11-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="0da11-108">ただし、`join` 句は、次の場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="0da11-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="0da11-109">結合が非等値の式に基づいている場合 (非等結合)。</span><span class="sxs-lookup"><span data-stu-id="0da11-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="0da11-110">結合が等値または非等値の複数の式に基づいている場合。</span><span class="sxs-lookup"><span data-stu-id="0da11-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="0da11-111">結合操作の前に、右辺 (内部) のシーケンスに一時的な範囲変数を導入する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="0da11-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="0da11-112">等結合ではない結合を実行するには、複数の `from` 句を使用して、各データ ソースを個別に導入することができます。</span><span class="sxs-lookup"><span data-stu-id="0da11-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="0da11-113">その後、`where` 句の述語式を各ソースの範囲変数に適用します。</span><span class="sxs-lookup"><span data-stu-id="0da11-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="0da11-114">式は、メソッド呼び出しの形式にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0da11-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0da11-115">このようなカスタム結合操作を、複数の `from` 句を使用した内部コレクションへのアクセスと混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="0da11-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="0da11-116">詳細については、「[join 句](../language-reference/keywords/join-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0da11-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da11-117">例</span><span class="sxs-lookup"><span data-stu-id="0da11-117">Example</span></span>  
 <span data-ttu-id="0da11-118">次の例の最初のメソッドは、単純なクロス結合を示しています。</span><span class="sxs-lookup"><span data-stu-id="0da11-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="0da11-119">クロス結合は、非常に大きな結果セットを生成することがあるので、注意して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da11-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="0da11-120">ただし、追加のクエリの実行対象となるソース シーケンスを作成するためのいくつかのシナリオでは便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="0da11-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="0da11-121">2 番目のメソッドは、左辺のカテゴリの一覧にカテゴリ ID が含まれているすべての製品のシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="0da11-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="0da11-122">`let` 句と `Contains` メソッドを使用して一時配列を作成していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0da11-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="0da11-123">クエリの前に配列を作成し、最初の `from` 句を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="0da11-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 <span data-ttu-id="0da11-124">[!code-cs[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0da11-124">[!code-cs[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da11-125">例</span><span class="sxs-lookup"><span data-stu-id="0da11-125">Example</span></span>  
 <span data-ttu-id="0da11-126">次の例では、クエリは一致するキーに基づいて 2 つのシーケンスを結合する必要があります。内部 (右辺) シーケンスでは、join 句自体より前にキーを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="0da11-126">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="0da11-127">この結合が `join` 句を使用して実行された場合は、要素ごとに `Split` メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0da11-127">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="0da11-128">複数の `from` 句を使用すると、クエリは、メソッドを繰り返し呼び出すことのオーバーヘッドを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="0da11-128">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="0da11-129">ただし、`join` は最適化されるため、この特定の場合には、複数の `from` 句を使用するよりも処理が速くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="0da11-129">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="0da11-130">結果は、主に、メソッド呼び出しにかかる負荷に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="0da11-130">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 <span data-ttu-id="0da11-131">[!code-cs[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0da11-131">[!code-cs[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da11-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0da11-132">See also</span></span>  
 <span data-ttu-id="0da11-133">[LINQ クエリ式](index.md) </span><span class="sxs-lookup"><span data-stu-id="0da11-133">[LINQ query expressions](index.md) </span></span>  
 <span data-ttu-id="0da11-134">[join 句](../language-reference/keywords/join-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0da11-134">[join clause](../language-reference/keywords/join-clause.md) </span></span>  
 [<span data-ttu-id="0da11-135">join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="0da11-135">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)

