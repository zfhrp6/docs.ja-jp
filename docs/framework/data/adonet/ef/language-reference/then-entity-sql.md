---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 5f0bbb0cadd736d476077685e08ba1a03b9c4001
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762885"
---
# <a name="then-entity-sql"></a><span data-ttu-id="0ae99-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0ae99-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="0ae99-103">WHEN 句が `true`として評価された場合の結果です。</span><span class="sxs-lookup"><span data-stu-id="0ae99-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ae99-104">構文</span><span class="sxs-lookup"><span data-stu-id="0ae99-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ae99-105">引数</span><span class="sxs-lookup"><span data-stu-id="0ae99-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="0ae99-106">任意の有効なブール式。</span><span class="sxs-lookup"><span data-stu-id="0ae99-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="0ae99-107">コレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="0ae99-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ae99-108">コメント</span><span class="sxs-lookup"><span data-stu-id="0ae99-108">Remarks</span></span>  
 <span data-ttu-id="0ae99-109">`when_expression` が `true`として評価された場合、対応する `then-expression`が評価されます。</span><span class="sxs-lookup"><span data-stu-id="0ae99-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="0ae99-110">WHEN の条件が満たされなかった場合は、 `else-expression` が評価されます。</span><span class="sxs-lookup"><span data-stu-id="0ae99-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="0ae99-111">ただし、 `else-expression`が存在しない場合、結果は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="0ae99-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="0ae99-112">例については、次を参照してください。[ケース](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ae99-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ae99-113">例</span><span class="sxs-lookup"><span data-stu-id="0ae99-113">Example</span></span>  
 <span data-ttu-id="0ae99-114">次の Entity SQL クエリでは、CASE 式を使用して、一連の `Boolean` 式を評価します。</span><span class="sxs-lookup"><span data-stu-id="0ae99-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="0ae99-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="0ae99-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0ae99-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0ae99-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0ae99-117">」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ae99-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="0ae99-118">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="0ae99-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="0ae99-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ae99-119">See Also</span></span>  
 [<span data-ttu-id="0ae99-120">CASE</span><span class="sxs-lookup"><span data-stu-id="0ae99-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="0ae99-121">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="0ae99-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
