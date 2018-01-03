---
title: SELECT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a33bd0d-ded1-41e7-ba3c-305502755e3b
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6e8c985436649af396c4fe9dc4dbbb484618c214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="select-entity-sql"></a><span data-ttu-id="a8f86-102">SELECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a8f86-102">SELECT (Entity SQL)</span></span>
<span data-ttu-id="a8f86-103">クエリで返される要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8f86-103">Specifies the elements returned by a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f86-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8f86-104">Syntax</span></span>  
  
```  
SELECT [ ALL | DISTINCT ] [ topSubclause ] aliasedExpr   
      [{ , aliasedExpr }] FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause ]  
or  
SELECT VALUE [ ALL | DISTINCT ] [ topSubclause ] expr FROM fromClause [ WHERE whereClause ] [ GROUP BY groupByClause [ HAVING havingClause ] ] [ ORDER BY orderByClause  
```  
  
## <a name="arguments"></a><span data-ttu-id="a8f86-105">引数</span><span class="sxs-lookup"><span data-stu-id="a8f86-105">Arguments</span></span>  
 <span data-ttu-id="a8f86-106">ALL</span><span class="sxs-lookup"><span data-stu-id="a8f86-106">ALL</span></span>  
 <span data-ttu-id="a8f86-107">結果セットに重複を含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8f86-107">Specifies that duplicates can appear in the result set.</span></span> <span data-ttu-id="a8f86-108">ALL は既定値です。</span><span class="sxs-lookup"><span data-stu-id="a8f86-108">ALL is the default.</span></span>  
  
 <span data-ttu-id="a8f86-109">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="a8f86-109">DISTINCT</span></span>  
 <span data-ttu-id="a8f86-110">結果セットに一意な結果のみを含むことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8f86-110">Specifies that only unique results can appear in the result set.</span></span>  
  
 <span data-ttu-id="a8f86-111">VALUE</span><span class="sxs-lookup"><span data-stu-id="a8f86-111">VALUE</span></span>  
 <span data-ttu-id="a8f86-112">1 つの項目のみを指定でき、row ラッパーを追加しません。</span><span class="sxs-lookup"><span data-stu-id="a8f86-112">Allows only one item to be specified, and does not add on a row wrapper.</span></span>  
  
 `topSubclause`  
 <span data-ttu-id="a8f86-113">`top (``expr``)`の形式で、クエリから返す最初の結果数を指定する有効な式。</span><span class="sxs-lookup"><span data-stu-id="a8f86-113">Any valid expression that indicates the number of first results to return from the query, of the form `top (``expr``)`.</span></span>  
  
 <span data-ttu-id="a8f86-114">LIMIT パラメーター、 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)演算子では、結果セット内の最初の n 個のアイテムを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-114">The LIMIT parameter of the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) operator also lets you select the first n items in the result set.</span></span>  
  
 `aliasedExpr`  
 <span data-ttu-id="a8f86-115">次の形式の式。</span><span class="sxs-lookup"><span data-stu-id="a8f86-115">An expression of the form:</span></span>  
  
 <span data-ttu-id="a8f86-116">`expr`として`identifier`&#124;です。`expr`</span><span class="sxs-lookup"><span data-stu-id="a8f86-116">`expr` as `identifier` &#124; `expr`</span></span>  
  
 `expr`  
 <span data-ttu-id="a8f86-117">リテラルまたは式。</span><span class="sxs-lookup"><span data-stu-id="a8f86-117">A literal or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8f86-118">コメント</span><span class="sxs-lookup"><span data-stu-id="a8f86-118">Remarks</span></span>  
 <span data-ttu-id="a8f86-119">SELECT 句が評価されます、 [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)、 [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)、および[HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)句が評価されました。</span><span class="sxs-lookup"><span data-stu-id="a8f86-119">The SELECT clause is evaluated after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), and [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md) clauses have been evaluated.</span></span> <span data-ttu-id="a8f86-120">SELECT 句は、FROM 句または外側のスコープから現在スコープ内にある項目のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-120">The SELECT clause can only refer to items currently in-scope (from the FROM clause, or from outer scopes).</span></span> <span data-ttu-id="a8f86-121">GROUP BY 句を指定した場合、SELECT 句は GROUP BY キーの別名のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-121">If a GROUP BY clause has been specified, the SELECT clause is only allowed to reference the aliases for the GROUP BY keys.</span></span> <span data-ttu-id="a8f86-122">FROM 句の項目への参照は、集計関数でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-122">Referring to the FROM clause items is only permitted in aggregate functions.</span></span>  
  
 <span data-ttu-id="a8f86-123">SELECT キーワードの後に続く 1 つまたは複数のクエリ式の一覧は、選択リスト (旧称、投影) と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-123">The list of one or more query expressions following the SELECT keyword is known as the select list, or more formally as the projection.</span></span> <span data-ttu-id="a8f86-124">投影のより一般的な形式は、単一クエリ式です。</span><span class="sxs-lookup"><span data-stu-id="a8f86-124">The most general form of projection is a single query expression.</span></span> <span data-ttu-id="a8f86-125">次の例に示すように、コレクション `member1` からメンバー `collection1`を選択すると、 `member1` の各オブジェクトに対応するすべての `collection1`値の新しいコレクションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-125">If you select a member `member1` from a collection `collection1`, you will produce a new collection of all the `member1` values for each object in `collection1`, as illustrated in the following example.</span></span>  
  
```  
SELECT collection1.member1 FROM collection1  
```  
  
 <span data-ttu-id="a8f86-126">たとえば、 `customers` が、タイプ `Customer` のコレクションで、このコレクションに、タイプ `Name` であるプロパティ `string`が含まれる場合、 `Name` から `customers` を選択すると、文字列のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-126">For example, if `customers` is a collection of type `Customer` that has a property `Name` that is of type `string`, selecting `Name` from `customers` will yield a collection of strings, as illustrated in the following example.</span></span>  
  
```  
SELECT customers.Name FROM customers AS c  
```  
  
 <span data-ttu-id="a8f86-127">JOIN 構文 (FULL、INNER、LEFT、OUTER、ON、および RIGHT) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-127">It is also possible to use JOIN syntax (FULL, INNER, LEFT, OUTER, ON, and RIGHT).</span></span> <span data-ttu-id="a8f86-128">内部結合に対しては ON が必要ですが、クロス結合に対しては ON を使用できません。</span><span class="sxs-lookup"><span data-stu-id="a8f86-128">ON is required for inner joins and is nto allowed for cross joins.</span></span>  
  
## <a name="row-and-value-select-clauses"></a><span data-ttu-id="a8f86-129">ROW 句および VALUE SELECT 句</span><span class="sxs-lookup"><span data-stu-id="a8f86-129">Row and Value Select Clauses</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="a8f86-130"> は、SELECT 句の 2 つのバリアントをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a8f86-130"> supports two variants of the SELECT clause.</span></span> <span data-ttu-id="a8f86-131">最初のバリアント、row select は、SELECT キーワードによって識別され、このバリアントを使用して、投影する必要がある 1 つまたは複数の値を指定できます。row ラッパーは、返された値の前後に暗黙的に追加されるため、クエリ式の結果は常に、行のマルチセットになります。</span><span class="sxs-lookup"><span data-stu-id="a8f86-131">The first variant, row select, is identified by the SELECT keyword, and can be used to specify one or more values that should be projected out. Because a row wrapper is implicitly added around the values returned, the result of the query expression is always a multiset of rows.</span></span>  
  
 <span data-ttu-id="a8f86-132">row select の各クエリ式は、別名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8f86-132">Each query expression in a row select must specify an alias.</span></span> <span data-ttu-id="a8f86-133">別名を指定しないと、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は別名生成規則を使用して別名の生成を試みます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-133">If no alias is specified,[!INCLUDE[esql](../../../../../../includes/esql-md.md)] attempts to generate an alias by using the alias generation rules.</span></span>  
  
 <span data-ttu-id="a8f86-134">SELECT 句のもう 1 つのバリアント、value select は SELECT VALUE キーワードによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-134">The other variant of the SELECT clause, value select, is identified by the SELECT VALUE keyword.</span></span> <span data-ttu-id="a8f86-135">このバリアントは、1 つの値のみを指定でき、row ラッパーを追加しません。</span><span class="sxs-lookup"><span data-stu-id="a8f86-135">It allows only one value to be specified, and does not add a row wrapper.</span></span>  
  
 <span data-ttu-id="a8f86-136">次の例に示すように、row select は常に VALUE SELECT として表現できます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-136">A row select is always expressible in terms of VALUE SELECT, as illustrated in the following example.</span></span>  
  
```  
SELECT 1 AS a, "abc" AS b FROM C  
SELECT VALUE ROW(1 AS a, "abc" AS b) FROM C   
```  
  
## <a name="all-and-distinct-modifiers"></a><span data-ttu-id="a8f86-137">ALL 修飾子および DISTINCT 修飾子</span><span class="sxs-lookup"><span data-stu-id="a8f86-137">All and Distinct Modifiers</span></span>  
 <span data-ttu-id="a8f86-138">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の SELECT のどちらのバリアントも ALL 修飾子または DISTINCT 修飾子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-138">Both variants of SELECT in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allow the specification of an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="a8f86-139">DISTINCT 修飾子を指定した場合、SELECT 句まで (SELECT 句を含めて) のクエリ式によって生成されたコレクションから重複が除外されます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-139">If the DISTINCT modifier is specified, duplicates are eliminated from the collection produced by the query expression (up to and including the SELECT clause).</span></span> <span data-ttu-id="a8f86-140">ALL 修飾子が指定された場合、重複は除外されません。ALL 修飾子は既定値です。</span><span class="sxs-lookup"><span data-stu-id="a8f86-140">If the ALL modifier is specified, no duplicate elimination is performed; ALL is the default.</span></span>  
  
## <a name="differences-from-transact-sql"></a><span data-ttu-id="a8f86-141">Transact-SQL との違い</span><span class="sxs-lookup"><span data-stu-id="a8f86-141">Differences from Transact-SQL</span></span>  
 <span data-ttu-id="a8f86-142">Transact-SQL とは異なり、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では SELECT 句で * 引数を使用できません。</span><span class="sxs-lookup"><span data-stu-id="a8f86-142">Unlike Transact-SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not support use of the * argument in the SELECT clause.</span></span>  <span data-ttu-id="a8f86-143">代わりに、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、次の例に示すように、FROM 句からコレクションの別名を参照して、レコード全体にクエリを投影できます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-143">Instead, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows queries to project out entire records by referencing the collection aliases from the FROM clause, as illustrated in the following example.</span></span>  
  
```  
SELECT * FROM T1, T2  
```  
  
 <span data-ttu-id="a8f86-144">上の [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] クエリ式は次の方法で [!INCLUDE[esql](../../../../../../includes/esql-md.md)] で表現されます。</span><span class="sxs-lookup"><span data-stu-id="a8f86-144">The previous [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] query expression is expressed in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] in the following way.</span></span>  
  
```  
SELECT a1, a2 FROM T1 AS a1, T2 AS a2  
```  
  
## <a name="example"></a><span data-ttu-id="a8f86-145">例</span><span class="sxs-lookup"><span data-stu-id="a8f86-145">Example</span></span>  
 <span data-ttu-id="a8f86-146">次の Entity SQL クエリは、SELECT 演算子を使用して、クエリによって返される要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8f86-146">The following Entity SQL query uses the SELECT operator to specify the elements to be returned by a query.</span></span> <span data-ttu-id="a8f86-147">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a8f86-147">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a8f86-148">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8f86-148">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a8f86-149">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a8f86-149">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a8f86-150">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="a8f86-150">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f86-151">参照</span><span class="sxs-lookup"><span data-stu-id="a8f86-151">See Also</span></span>  
 [<span data-ttu-id="a8f86-152">クエリ式</span><span class="sxs-lookup"><span data-stu-id="a8f86-152">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="a8f86-153">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="a8f86-153">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a8f86-154">TOP</span><span class="sxs-lookup"><span data-stu-id="a8f86-154">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
