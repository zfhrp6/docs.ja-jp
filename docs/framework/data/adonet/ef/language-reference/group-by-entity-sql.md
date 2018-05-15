---
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 3b5edee08afef8418f19df433223818218ae909d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="group-by-entity-sql"></a><span data-ttu-id="b6508-102">GROUP BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6508-102">GROUP BY (Entity SQL)</span></span>
<span data-ttu-id="b6508-103">クエリ ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) 式によって返されるオブジェクトをグループ化するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="b6508-103">Specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6508-104">構文</span><span class="sxs-lookup"><span data-stu-id="b6508-104">Syntax</span></span>  
  
```  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6508-105">引数</span><span class="sxs-lookup"><span data-stu-id="b6508-105">Arguments</span></span>  
 `aliasedExpression`  
 <span data-ttu-id="b6508-106">グループ化の実行対象となる有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="b6508-106">Any valid query expression on which grouping is performed.</span></span> <span data-ttu-id="b6508-107">`expression` には、プロパティを指定することも、FROM 句から返されたプロパティを参照する非集計式を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6508-107">`expression` can be a property or a non-aggregate expression that references a property returned by the FROM clause.</span></span> <span data-ttu-id="b6508-108">GROUP BY 句内の各式は、等価かどうかを比較できる型に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6508-108">Each expression in a GROUP BY clause must evaluate to a type that can be compared for equality.</span></span> <span data-ttu-id="b6508-109">通常、これらの型は数値、文字列、日付などのスカラー プリミティブです。</span><span class="sxs-lookup"><span data-stu-id="b6508-109">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="b6508-110">コレクション別にグループ化することはできません。</span><span class="sxs-lookup"><span data-stu-id="b6508-110">You cannot group by a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6508-111">コメント</span><span class="sxs-lookup"><span data-stu-id="b6508-111">Remarks</span></span>  
 <span data-ttu-id="b6508-112">SELECT 句で集計関数が含まれている場合\<選択リスト >、GROUP by によって各グループの集計値を計算します。</span><span class="sxs-lookup"><span data-stu-id="b6508-112">If aggregate functions are included in the SELECT clause \<select list>, GROUP BY calculates a summary value for each group.</span></span> <span data-ttu-id="b6508-113">GROUP BY を指定する場合は、選択リスト内の非集計式内の各プロパティ名が GROUP BY リストに含まれるか、GROUP BY 式が選択リスト式に正確に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6508-113">When GROUP BY is specified, either each property name in any nonaggregate expression in the select list should be included in the GROUP BY list, or the GROUP BY expression must exactly match the select list expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6508-114">ORDER BY 句を指定しない場合、GROUP BY 句でグループが返される順序には特に決まりはありません。</span><span class="sxs-lookup"><span data-stu-id="b6508-114">If the ORDER BY clause is not specified, groups returned by the GROUP BY clause are not in any particular order.</span></span> <span data-ttu-id="b6508-115">データの特定の順序を指定するには、常に ORDER BY 句を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b6508-115">To specify a particular ordering of the data, we recommend that you always use the ORDER BY clause.</span></span>  
  
 <span data-ttu-id="b6508-116">GROUP BY 句を明示的または暗黙的に指定した場合 (たとえばクエリ内の HAVING 句)、現在のスコープは非表示になり、新しいスコープが導入されます。</span><span class="sxs-lookup"><span data-stu-id="b6508-116">When a GROUP BY clause is specified, either explicitly or implicitly (for example, by a HAVING clause in the query), the current scope is hidden, and a new scope is introduced.</span></span>  
  
 <span data-ttu-id="b6508-117">SELECT 句、HAVING 句、および ORDER BY 句は、FROM 句で指定された要素名を参照することはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="b6508-117">The SELECT clause, the HAVING clause, and the ORDER BY clause will no longer be able to refer to element names specified in the FROM clause.</span></span> <span data-ttu-id="b6508-118">ユーザーが参照できるのは、グループ化式自体だけです。</span><span class="sxs-lookup"><span data-stu-id="b6508-118">You can only refer to the grouping expressions themselves.</span></span> <span data-ttu-id="b6508-119">このためには、新しい名前 (別名) を各グループ化式に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b6508-119">To do this, you can assign new names (aliases) to each grouping expression.</span></span> <span data-ttu-id="b6508-120">グループ化式に別名が指定されていない場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、次の例に示すように別名生成規則を使用することによって別名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b6508-120">If no alias is specified for a grouping expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate one by using the alias generation rules, as illustrated in the following example.</span></span>  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 <span data-ttu-id="b6508-121">GROUP BY 句の式は、同じ GROUP BY 句で前に定義された名前を参照できません。</span><span class="sxs-lookup"><span data-stu-id="b6508-121">Expressions in the GROUP BY clause cannot refer to names defined earlier in the same GROUP BY clause.</span></span>  
  
 <span data-ttu-id="b6508-122">名前のグループ化に加え、SELECT 句、HAVING 句、および ORDER BY 句で集計を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6508-122">In addition to grouping names, you can also specify aggregates in the SELECT clause, HAVING clause, and the ORDER BY clause.</span></span> <span data-ttu-id="b6508-123">集計には、グループの各要素について評価される式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b6508-123">An aggregate contains an expression that is evaluated for each element of the group.</span></span> <span data-ttu-id="b6508-124">集計演算子により、これらのすべての式の値の数が減少します (ただし、必ずしも単一の値になるとは限りません)。</span><span class="sxs-lookup"><span data-stu-id="b6508-124">The aggregate operator reduces the values of all these expressions (usually, but not always, into a single value).</span></span> <span data-ttu-id="b6508-125">集計式は、現在のスコープに表示される基の要素名、または GROUP BY 句自体によって導入された新しい任意の名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="b6508-125">The aggregate expression can make references to the original element names visible in the parent scope, or to any of the new names introduced by the GROUP BY clause itself.</span></span> <span data-ttu-id="b6508-126">集計は SELECT 句、HAVING 句、および ORDER BY 句に含まれますが、次の例で示すとおり、実際にはグループ化式と同じスコープで評価されます。</span><span class="sxs-lookup"><span data-stu-id="b6508-126">Although the aggregates appear in the SELECT clause, HAVING clause, and ORDER BY clause, they are actually evaluated under the same scope as the grouping expressions, as illustrated in the following example.</span></span>  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 <span data-ttu-id="b6508-127">このクエリは GROUP BY 句を使用して、注文した全製品の価格のレポートを製品別に分類して生成します。</span><span class="sxs-lookup"><span data-stu-id="b6508-127">This query uses the GROUP BY clause to produce a report of the cost of all products ordered, broken down by product.</span></span> <span data-ttu-id="b6508-128">グループ化式の一部として、製品に `name` という名前を付け、SELECT リストでその名前を参照します。</span><span class="sxs-lookup"><span data-stu-id="b6508-128">It gives the name `name` to the product as part of the grouping expression, and then references that name in the SELECT list.</span></span> <span data-ttu-id="b6508-129">さらに、注文明細の価格と数量を内部で参照する SELECT リスト内の集計 `sum` を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6508-129">It also specifies the aggregate `sum` in the SELECT list that internally references the price and quantity of the order line.</span></span>  
  
 <span data-ttu-id="b6508-130">各 GROUP By キー式には、入力スコープへの参照が少なくとも 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="b6508-130">Each GROUP By key expression must have at least one reference to the input scope:</span></span>  
  
```  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 <span data-ttu-id="b6508-131">GROUP BY を使用する場合の例については、「 [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b6508-131">For an example of using GROUP BY, see [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6508-132">例</span><span class="sxs-lookup"><span data-stu-id="b6508-132">Example</span></span>  
 <span data-ttu-id="b6508-133">次の Entity SQL クエリでは、GROUP BY 演算子を使用して、クエリによって返されるオブジェクトをグループ化するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="b6508-133">The following Entity SQL query uses the GROUP BY operator to specify groups into which objects are returned by a query.</span></span> <span data-ttu-id="b6508-134">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="b6508-134">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b6508-135">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="b6508-135">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b6508-136">」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="b6508-136">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="b6508-137">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="b6508-137">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GROUPBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#groupby)]  
  
## <a name="see-also"></a><span data-ttu-id="b6508-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6508-138">See Also</span></span>  
 [<span data-ttu-id="b6508-139">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="b6508-139">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b6508-140">クエリ式</span><span class="sxs-lookup"><span data-stu-id="b6508-140">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
