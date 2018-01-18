---
title: "+ (追加)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f743d1f6adf7b6d4440f2ebcf2fb89d2ee1b9831
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="-add"></a><span data-ttu-id="77218-102">+ (加算)</span><span class="sxs-lookup"><span data-stu-id="77218-102">+ (Add)</span></span>
<span data-ttu-id="77218-103">2 つの値を加算します。</span><span class="sxs-lookup"><span data-stu-id="77218-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77218-104">構文</span><span class="sxs-lookup"><span data-stu-id="77218-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="77218-105">引数</span><span class="sxs-lookup"><span data-stu-id="77218-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="77218-106">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="77218-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="77218-107">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="77218-107">Result Types</span></span>  
 <span data-ttu-id="77218-108">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="77218-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="77218-109">暗黙的な型の昇格の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="77218-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77218-110">コメント</span><span class="sxs-lookup"><span data-stu-id="77218-110">Remarks</span></span>  
 <span data-ttu-id="77218-111">EDM.String 型の場合は、値が連結されます。</span><span class="sxs-lookup"><span data-stu-id="77218-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77218-112">例</span><span class="sxs-lookup"><span data-stu-id="77218-112">Example</span></span>  
 <span data-ttu-id="77218-113">次の Entity SQL クエリでは、+ 算術演算子を使用して 2 つの数値を加算します。</span><span class="sxs-lookup"><span data-stu-id="77218-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="77218-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="77218-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="77218-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="77218-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="77218-116">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="77218-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="77218-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="77218-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="77218-118">参照</span><span class="sxs-lookup"><span data-stu-id="77218-118">See Also</span></span>  
 [<span data-ttu-id="77218-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="77218-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="77218-120">概念モデルの型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="77218-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)
