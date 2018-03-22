---
title: '* (乗算)(Entity SQL)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c7e2bcf15ab8d0cf24fdc6cb7e9db025784bd435
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="e26bf-102">\* (乗算) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e26bf-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="e26bf-103">2 つの式を乗算します。</span><span class="sxs-lookup"><span data-stu-id="e26bf-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e26bf-104">構文</span><span class="sxs-lookup"><span data-stu-id="e26bf-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e26bf-105">引数</span><span class="sxs-lookup"><span data-stu-id="e26bf-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e26bf-106">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="e26bf-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e26bf-107">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="e26bf-107">Result Types</span></span>  
 <span data-ttu-id="e26bf-108">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="e26bf-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="e26bf-109">暗黙的な型の昇格の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="e26bf-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e26bf-110">例</span><span class="sxs-lookup"><span data-stu-id="e26bf-110">Example</span></span>  
 <span data-ttu-id="e26bf-111">次の Entity SQL クエリでは、\* 算術演算子を使用して 2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="e26bf-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="e26bf-112">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e26bf-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e26bf-113">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e26bf-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e26bf-114">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e26bf-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e26bf-115">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e26bf-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="e26bf-116">参照</span><span class="sxs-lookup"><span data-stu-id="e26bf-116">See Also</span></span>  
 [<span data-ttu-id="e26bf-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="e26bf-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
