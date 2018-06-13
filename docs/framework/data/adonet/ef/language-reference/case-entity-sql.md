---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: ee878409e7698300b7bebbdac760422013f3b7de
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761465"
---
# <a name="case-entity-sql"></a><span data-ttu-id="c7089-102">CASE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c7089-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="c7089-103">一連の `Boolean` 式を評価して結果を決定します。</span><span class="sxs-lookup"><span data-stu-id="c7089-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7089-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7089-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7089-105">引数</span><span class="sxs-lookup"><span data-stu-id="c7089-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="c7089-106">複数の WHEN `Boolean_expression` THEN `result_expression` 句が使用できることを示すプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="c7089-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="c7089-107">THEN `result_expression`</span><span class="sxs-lookup"><span data-stu-id="c7089-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="c7089-108">`Boolean_expression` が `true`に評価されると返される式です。</span><span class="sxs-lookup"><span data-stu-id="c7089-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="c7089-109">`result expression` は、任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="c7089-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="c7089-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="c7089-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="c7089-111">比較操作の評価がいずれも `true`でなかった場合に返される式です。</span><span class="sxs-lookup"><span data-stu-id="c7089-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="c7089-112">この引数を省略し、比較演算のいずれも `true`に評価されなかった場合、CASE は NULL を返します。</span><span class="sxs-lookup"><span data-stu-id="c7089-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="c7089-113">`else_result_expression` は、任意の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="c7089-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="c7089-114">`else_result_expression` と任意の `result_expression` のデータ型は同一であるか、暗黙的な変換によって同一の型になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7089-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="c7089-115">WHEN `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="c7089-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="c7089-116">検索 CASE 形式を使用した場合に評価される `Boolean` 式です。</span><span class="sxs-lookup"><span data-stu-id="c7089-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="c7089-117">`Boolean_expression` は、任意の有効な `Boolean` 式です。</span><span class="sxs-lookup"><span data-stu-id="c7089-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7089-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="c7089-118">Return Value</span></span>  
 <span data-ttu-id="c7089-119">`result_expression` およびオプションの `else_result_expression`の一連の型の中から、最も優先順位の高い型を返します。</span><span class="sxs-lookup"><span data-stu-id="c7089-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7089-120">コメント</span><span class="sxs-lookup"><span data-stu-id="c7089-120">Remarks</span></span>  
 <span data-ttu-id="c7089-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の case 式は、 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] の case 式と似ています。</span><span class="sxs-lookup"><span data-stu-id="c7089-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="c7089-122">case 式を使用すると、適切な結果が得られる式を、一連の条件判定によって決めることができます。</span><span class="sxs-lookup"><span data-stu-id="c7089-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="c7089-123">この形式の case 式では、1 つまたは複数の `Boolean` 式によって、最終的に使用される式が決定されます。</span><span class="sxs-lookup"><span data-stu-id="c7089-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="c7089-124">CASE 関数は、各 WHEN 句の `Boolean_expression` を指定された順序で評価し、 `result_expression` として評価された最初の `Boolean_expression` の `true`を返します。</span><span class="sxs-lookup"><span data-stu-id="c7089-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="c7089-125">残りの式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="c7089-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="c7089-126">`Boolean_expression` の評価がいずれも `true`でなかった場合、データベース エンジンは、ELSE 句が指定されていれば `else_result_expression` を、ELSE 句が指定されていない場合は NULL 値を返します。</span><span class="sxs-lookup"><span data-stu-id="c7089-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="c7089-127">CASE ステートメントでマルチセットを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="c7089-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7089-128">例</span><span class="sxs-lookup"><span data-stu-id="c7089-128">Example</span></span>  
 <span data-ttu-id="c7089-129">次の Entity SQL クエリでは、CASE 式を使用して、一連の `Boolean` 式を評価し、結果を取得しています。</span><span class="sxs-lookup"><span data-stu-id="c7089-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="c7089-130">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="c7089-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c7089-131">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c7089-131">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c7089-132">」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="c7089-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="c7089-133">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="c7089-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="c7089-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7089-134">See Also</span></span>  
 [<span data-ttu-id="c7089-135">THEN</span><span class="sxs-lookup"><span data-stu-id="c7089-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [<span data-ttu-id="c7089-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="c7089-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="c7089-137">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c7089-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
