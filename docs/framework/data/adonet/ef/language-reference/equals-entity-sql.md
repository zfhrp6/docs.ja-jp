---
title: = (等しい) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: bda314208a25426be321ba307be96067b1df2ac8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761400"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="0dc34-102">= (等しい) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0dc34-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="0dc34-103">2 つの式の等価性を比較します。</span><span class="sxs-lookup"><span data-stu-id="0dc34-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc34-104">構文</span><span class="sxs-lookup"><span data-stu-id="0dc34-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0dc34-105">引数</span><span class="sxs-lookup"><span data-stu-id="0dc34-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0dc34-106">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="0dc34-106">Any valid expression.</span></span> <span data-ttu-id="0dc34-107">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="0dc34-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0dc34-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="0dc34-108">Result Types</span></span>  
 <span data-ttu-id="0dc34-109">左の式が右の式と等しい場合は`true` 、等しくない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="0dc34-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dc34-110">コメント</span><span class="sxs-lookup"><span data-stu-id="0dc34-110">Remarks</span></span>  
 <span data-ttu-id="0dc34-111">== 演算子は = 演算子と同じです。</span><span class="sxs-lookup"><span data-stu-id="0dc34-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dc34-112">例</span><span class="sxs-lookup"><span data-stu-id="0dc34-112">Example</span></span>  
 <span data-ttu-id="0dc34-113">次の Entity SQL クエリでは、= 比較演算子を使用して 2 つの式の等価性を比較します。</span><span class="sxs-lookup"><span data-stu-id="0dc34-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="0dc34-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="0dc34-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0dc34-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0dc34-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0dc34-116">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0dc34-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0dc34-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="0dc34-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="0dc34-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dc34-118">See Also</span></span>  
 [<span data-ttu-id="0dc34-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="0dc34-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
