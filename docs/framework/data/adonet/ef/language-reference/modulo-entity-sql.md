---
title: (剰余) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: ad7b76c1479906e9dcd875407e75475b55d5ae16
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764542"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="999c1-102">(剰余) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="999c1-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="999c1-103">ある式を別の式で除算した結果の余りを返します。</span><span class="sxs-lookup"><span data-stu-id="999c1-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999c1-104">構文</span><span class="sxs-lookup"><span data-stu-id="999c1-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="999c1-105">引数</span><span class="sxs-lookup"><span data-stu-id="999c1-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="999c1-106">除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="999c1-106">The numeric expression to divide.</span></span> <span data-ttu-id="999c1-107">`dividend` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="999c1-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="999c1-108">被除数を除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="999c1-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="999c1-109">`divisor` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="999c1-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="999c1-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="999c1-110">Result Types</span></span>  
 <span data-ttu-id="999c1-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="999c1-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="999c1-112">例</span><span class="sxs-lookup"><span data-stu-id="999c1-112">Example</span></span>  
 <span data-ttu-id="999c1-113">次の Entity SQL クエリでは、% 算術演算子を使用して、特定の式を別の式で除算した結果の余りを返します。</span><span class="sxs-lookup"><span data-stu-id="999c1-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="999c1-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="999c1-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="999c1-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="999c1-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="999c1-116">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="999c1-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="999c1-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="999c1-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="999c1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="999c1-118">See Also</span></span>  
 [<span data-ttu-id="999c1-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="999c1-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
