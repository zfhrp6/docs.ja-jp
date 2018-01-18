---
title: EXISTS (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 225487f6a0d7ec29689c01dd6355e7ba1aa6883e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="exists-entity-sql"></a><span data-ttu-id="4f198-102">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4f198-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="4f198-103">コレクションが空かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="4f198-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f198-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f198-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4f198-105">引数</span><span class="sxs-lookup"><span data-stu-id="4f198-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4f198-106">コレクションを返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="4f198-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="4f198-107">NOT</span><span class="sxs-lookup"><span data-stu-id="4f198-107">NOT</span></span>  
 <span data-ttu-id="4f198-108">EXISTS の結果を否定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f198-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f198-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f198-109">Return Value</span></span>  
 <span data-ttu-id="4f198-110">コレクションが空でない場合は `true`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="4f198-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f198-111">コメント</span><span class="sxs-lookup"><span data-stu-id="4f198-111">Remarks</span></span>  
 <span data-ttu-id="4f198-112">EXISTS は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="4f198-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4f198-113">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4f198-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4f198-114">優先順位について、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set 演算子を参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f198-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f198-115">例</span><span class="sxs-lookup"><span data-stu-id="4f198-115">Example</span></span>  
 <span data-ttu-id="4f198-116">次の Entity SQL クエリでは、EXISTS 演算子を使用して、コレクションが空かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="4f198-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="4f198-117">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="4f198-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4f198-118">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f198-118">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4f198-119">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4f198-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4f198-120">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="4f198-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="4f198-121">参照</span><span class="sxs-lookup"><span data-stu-id="4f198-121">See Also</span></span>  
 [<span data-ttu-id="4f198-122">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="4f198-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
