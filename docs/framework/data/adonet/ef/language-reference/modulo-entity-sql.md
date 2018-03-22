---
title: (剰余) (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e204612904aa55b4a0ae9aa65f2bbfd644bbc396
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="19e31-102">(剰余) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="19e31-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="19e31-103">ある式を別の式で除算した結果の余りを返します。</span><span class="sxs-lookup"><span data-stu-id="19e31-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19e31-104">構文</span><span class="sxs-lookup"><span data-stu-id="19e31-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="19e31-105">引数</span><span class="sxs-lookup"><span data-stu-id="19e31-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="19e31-106">除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="19e31-106">The numeric expression to divide.</span></span> <span data-ttu-id="19e31-107">`dividend` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="19e31-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="19e31-108">被除数を除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="19e31-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="19e31-109">`divisor` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="19e31-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="19e31-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="19e31-110">Result Types</span></span>  
 <span data-ttu-id="19e31-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="19e31-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="19e31-112">例</span><span class="sxs-lookup"><span data-stu-id="19e31-112">Example</span></span>  
 <span data-ttu-id="19e31-113">次の Entity SQL クエリでは、% 算術演算子を使用して、特定の式を別の式で除算した結果の余りを返します。</span><span class="sxs-lookup"><span data-stu-id="19e31-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="19e31-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="19e31-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="19e31-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="19e31-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="19e31-116">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="19e31-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="19e31-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="19e31-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="19e31-118">参照</span><span class="sxs-lookup"><span data-stu-id="19e31-118">See Also</span></span>  
 [<span data-ttu-id="19e31-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="19e31-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
