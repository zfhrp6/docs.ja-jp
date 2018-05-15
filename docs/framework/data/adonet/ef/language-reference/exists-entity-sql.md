---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: d42b1c227362b13124f4bb21e55b6fda07f9c5ff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="exists-entity-sql"></a><span data-ttu-id="ba3f9-102">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ba3f9-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="ba3f9-103">コレクションが空かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba3f9-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba3f9-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba3f9-105">引数</span><span class="sxs-lookup"><span data-stu-id="ba3f9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ba3f9-106">コレクションを返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="ba3f9-107">NOT</span><span class="sxs-lookup"><span data-stu-id="ba3f9-107">NOT</span></span>  
 <span data-ttu-id="ba3f9-108">EXISTS の結果を否定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba3f9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ba3f9-109">Return Value</span></span>  
 <span data-ttu-id="ba3f9-110">コレクションが空でない場合は `true`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba3f9-111">コメント</span><span class="sxs-lookup"><span data-stu-id="ba3f9-111">Remarks</span></span>  
 <span data-ttu-id="ba3f9-112">EXISTS は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ba3f9-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ba3f9-114">優先順位について、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set 演算子を参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba3f9-115">例</span><span class="sxs-lookup"><span data-stu-id="ba3f9-115">Example</span></span>  
 <span data-ttu-id="ba3f9-116">次の Entity SQL クエリでは、EXISTS 演算子を使用して、コレクションが空かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="ba3f9-117">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ba3f9-118">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-118">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ba3f9-119">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ba3f9-120">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ba3f9-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="ba3f9-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba3f9-121">See Also</span></span>  
 [<span data-ttu-id="ba3f9-122">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ba3f9-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
