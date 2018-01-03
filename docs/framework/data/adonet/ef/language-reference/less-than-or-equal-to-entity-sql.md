---
title: "&lt;= (以下) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ca900cde1845083e515fa4e8e884b57f8ae689a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="2e4c5-102">&lt;= (以下) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2e4c5-102">&lt;= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="2e4c5-103">2 つの式を比較して、左の式の値が右の式の値以下であるかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e4c5-104">構文</span><span class="sxs-lookup"><span data-stu-id="2e4c5-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e4c5-105">引数</span><span class="sxs-lookup"><span data-stu-id="2e4c5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2e4c5-106">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-106">Any valid expression.</span></span> <span data-ttu-id="2e4c5-107">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2e4c5-108">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="2e4c5-108">Result Types</span></span>  
 <span data-ttu-id="2e4c5-109">左の式の値が右の式の値以下である場合は`true` 、そうでない場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e4c5-110">例</span><span class="sxs-lookup"><span data-stu-id="2e4c5-110">Example</span></span>  
 <span data-ttu-id="2e4c5-111">次の Entity SQL クエリは「<=」比較演算子を使用して 2 つの式を比較し、左の式の値が右の式の値以下であるかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="2e4c5-112">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2e4c5-113">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="2e4c5-114">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="2e4c5-115">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="2e4c5-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="2e4c5-116">参照</span><span class="sxs-lookup"><span data-stu-id="2e4c5-116">See Also</span></span>  
 [<span data-ttu-id="2e4c5-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="2e4c5-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
