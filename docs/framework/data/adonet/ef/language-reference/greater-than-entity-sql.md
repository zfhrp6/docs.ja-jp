---
title: '&gt; (より大きい) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: b9cf4d5445060bbd013ae2d769c407e7f9ee9314
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="gt-greater-than-entity-sql"></a><span data-ttu-id="80511-102">&gt; (より大きい) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="80511-102">&gt; (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="80511-103">2 つの式を比較して、左の式の値が右の式の値よりも大きいかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="80511-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80511-104">構文</span><span class="sxs-lookup"><span data-stu-id="80511-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="80511-105">引数</span><span class="sxs-lookup"><span data-stu-id="80511-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="80511-106">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="80511-106">Any valid expression.</span></span> <span data-ttu-id="80511-107">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="80511-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="80511-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="80511-108">Result Types</span></span>  
 <span data-ttu-id="80511-109">左の式の値が右の式の値よりも大きい場合は`true` 、そうでない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="80511-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80511-110">例</span><span class="sxs-lookup"><span data-stu-id="80511-110">Example</span></span>  
 <span data-ttu-id="80511-111">次の Entity SQL クエリは「>」比較演算子を使用して 2 つの式を比較し、左の式の値が右の式の値よりも大きいかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="80511-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="80511-112">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="80511-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="80511-113">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="80511-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="80511-114">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="80511-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="80511-115">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="80511-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="80511-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="80511-116">See Also</span></span>  
 [<span data-ttu-id="80511-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="80511-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
