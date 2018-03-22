---
title: '! (NOT) (Entity SQL)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f3786724280cc077574f37e4d373c85faf5340f3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="-not-entity-sql"></a><span data-ttu-id="cbc8c-103">!</span><span class="sxs-lookup"><span data-stu-id="cbc8c-103">!</span></span> <span data-ttu-id="cbc8c-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cbc8c-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="cbc8c-105">`Boolean` 型の式を否定します。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc8c-106">構文</span><span class="sxs-lookup"><span data-stu-id="cbc8c-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cbc8c-107">引数</span><span class="sxs-lookup"><span data-stu-id="cbc8c-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="cbc8c-108">ブール値を返す任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbc8c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="cbc8c-109">Remarks</span></span>  
 <span data-ttu-id="cbc8c-110">感嘆符 (!) には、NOT 演算子と同じ機能があります。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbc8c-111">例</span><span class="sxs-lookup"><span data-stu-id="cbc8c-111">Example</span></span>  
 <span data-ttu-id="cbc8c-112">次の Entity SQL クエリでは、NOT 演算子を使用して `Boolean` 型の式を否定します。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="cbc8c-113">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cbc8c-114">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cbc8c-115">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cbc8c-116">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="cbc8c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="cbc8c-117">参照</span><span class="sxs-lookup"><span data-stu-id="cbc8c-117">See Also</span></span>  
 [<span data-ttu-id="cbc8c-118">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="cbc8c-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
