---
title: '&amp;&amp; (と)(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 649b805c1d728c45120adf85f02533d36f7bcdff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="e2ee9-102">&amp;&amp; (と)(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2ee9-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="e2ee9-103">両方の式が `true` の場合は `true`を返します。それ以外の場合は `false` または `NULL`を返します。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ee9-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2ee9-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2ee9-105">引数</span><span class="sxs-lookup"><span data-stu-id="e2ee9-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="e2ee9-106">ブール値を返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2ee9-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e2ee9-107">Remarks</span></span>  
 <span data-ttu-id="e2ee9-108">二重のアンパサンド (&&) は、AND 演算子と同じ効果を持ちます。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="e2ee9-109">使用可能な入力値と戻り値の型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="e2ee9-110">TRUE</span><span class="sxs-lookup"><span data-stu-id="e2ee9-110">TRUE</span></span>|<span data-ttu-id="e2ee9-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="e2ee9-111">FALSE</span></span>|<span data-ttu-id="e2ee9-112">NULL</span><span class="sxs-lookup"><span data-stu-id="e2ee9-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="e2ee9-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="e2ee9-113">FALSE</span></span>|<span data-ttu-id="e2ee9-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="e2ee9-114">FALSE</span></span>|<span data-ttu-id="e2ee9-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="e2ee9-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="e2ee9-116">NULL</span><span class="sxs-lookup"><span data-stu-id="e2ee9-116">NULL</span></span>|<span data-ttu-id="e2ee9-117">false</span><span class="sxs-lookup"><span data-stu-id="e2ee9-117">FALSE</span></span>|<span data-ttu-id="e2ee9-118">NULL</span><span class="sxs-lookup"><span data-stu-id="e2ee9-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2ee9-119">例</span><span class="sxs-lookup"><span data-stu-id="e2ee9-119">Example</span></span>  
 <span data-ttu-id="e2ee9-120">次の Entity SQL クエリは、AND 演算子の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="e2ee9-121">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e2ee9-122">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e2ee9-123">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e2ee9-124">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e2ee9-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="e2ee9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2ee9-125">See Also</span></span>  
 [<span data-ttu-id="e2ee9-126">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="e2ee9-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
