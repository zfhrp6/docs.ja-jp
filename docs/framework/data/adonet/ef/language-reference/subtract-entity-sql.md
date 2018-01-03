---
title: "- (減算)(Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 20b9fd7dda34d3f6f19551d8f7e313196e0acc12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="5f7a3-102">- (減算) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5f7a3-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="5f7a3-103">2 つの値の間で減算をします。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="5f7a3-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f7a3-105">引数</span><span class="sxs-lookup"><span data-stu-id="5f7a3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5f7a3-106">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5f7a3-107">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="5f7a3-107">Result Types</span></span>  
 <span data-ttu-id="5f7a3-108">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="5f7a3-109">暗黙的な型の昇格の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f7a3-110">例</span><span class="sxs-lookup"><span data-stu-id="5f7a3-110">Example</span></span>  
 <span data-ttu-id="5f7a3-111">次の Entity SQL クエリでは、- 算術演算子を使用して 2 つの数値の間で減算をします。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="5f7a3-112">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5f7a3-113">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5f7a3-114">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="5f7a3-115">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="5f7a3-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="5f7a3-116">参照</span><span class="sxs-lookup"><span data-stu-id="5f7a3-116">See Also</span></span>  
 [<span data-ttu-id="5f7a3-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="5f7a3-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
