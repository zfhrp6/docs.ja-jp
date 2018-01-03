---
title: "= (等しい) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c6b258bd06fd3e7e348e190b0897d66036006873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="dadb0-102">= (等しい) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dadb0-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="dadb0-103">2 つの式の等価性を比較します。</span><span class="sxs-lookup"><span data-stu-id="dadb0-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dadb0-104">構文</span><span class="sxs-lookup"><span data-stu-id="dadb0-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="dadb0-105">引数</span><span class="sxs-lookup"><span data-stu-id="dadb0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="dadb0-106">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="dadb0-106">Any valid expression.</span></span> <span data-ttu-id="dadb0-107">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="dadb0-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dadb0-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="dadb0-108">Result Types</span></span>  
 <span data-ttu-id="dadb0-109">左の式が右の式と等しい場合は`true` 、等しくない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="dadb0-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dadb0-110">コメント</span><span class="sxs-lookup"><span data-stu-id="dadb0-110">Remarks</span></span>  
 <span data-ttu-id="dadb0-111">== 演算子は = 演算子と同じです。</span><span class="sxs-lookup"><span data-stu-id="dadb0-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dadb0-112">例</span><span class="sxs-lookup"><span data-stu-id="dadb0-112">Example</span></span>  
 <span data-ttu-id="dadb0-113">次の Entity SQL クエリでは、= 比較演算子を使用して 2 つの式の等価性を比較します。</span><span class="sxs-lookup"><span data-stu-id="dadb0-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="dadb0-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="dadb0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dadb0-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="dadb0-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="dadb0-116">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="dadb0-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="dadb0-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="dadb0-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="dadb0-118">参照</span><span class="sxs-lookup"><span data-stu-id="dadb0-118">See Also</span></span>  
 [<span data-ttu-id="dadb0-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="dadb0-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
