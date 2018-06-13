---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 9b67e6824317b032f420501ffba385ec6fd651b9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762677"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="fa9e7-102">OVERLAPS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fa9e7-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="fa9e7-103">2 つのコレクションに共通の要素が存在するかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa9e7-104">構文</span><span class="sxs-lookup"><span data-stu-id="fa9e7-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa9e7-105">引数</span><span class="sxs-lookup"><span data-stu-id="fa9e7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fa9e7-106">コレクションを返す任意の有効なクエリ式。もう一方のクエリ式から返されたコレクションと比較されます。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="fa9e7-107">すべての式は、 `expression`と同じ型であるか、共通の基本型または派生型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa9e7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="fa9e7-108">Return Value</span></span>  
 <span data-ttu-id="fa9e7-109">2 つのコレクションに共通の要素がある場合は`true` 、それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-109">`true` if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa9e7-110">コメント</span><span class="sxs-lookup"><span data-stu-id="fa9e7-110">Remarks</span></span>  
 <span data-ttu-id="fa9e7-111">Overlaps の機能を次に該当するショートカットは。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-111">OVERLAPS provides functionally equivalent tothe following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="fa9e7-112">OVERLAPS は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="fa9e7-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="fa9e7-114">優先順位について、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set 演算子を参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa9e7-115">例</span><span class="sxs-lookup"><span data-stu-id="fa9e7-115">Example</span></span>  
 <span data-ttu-id="fa9e7-116">次の Entity SQL クエリでは、OVERLAPS 演算子を使用して、2 つのコレクションに共通の値が存在するかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="fa9e7-117">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fa9e7-118">これをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-118">To compile and run this, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fa9e7-119">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fa9e7-120">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="fa9e7-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="fa9e7-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa9e7-121">See Also</span></span>  
 [<span data-ttu-id="fa9e7-122">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="fa9e7-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
