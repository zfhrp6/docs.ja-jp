---
title: '!= (等しくない) (Entity SQL)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 237dae641c272260e37fa7757792247700784d17
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="ee97e-102">!= (等しくない) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ee97e-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="ee97e-103">2 つの式を比較して、左の式の値が右の式の値と等しくないかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="ee97e-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="ee97e-104">!= (等しくない) 演算子は、機能的には <> 演算子と同じです。</span><span class="sxs-lookup"><span data-stu-id="ee97e-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee97e-105">構文</span><span class="sxs-lookup"><span data-stu-id="ee97e-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee97e-106">引数</span><span class="sxs-lookup"><span data-stu-id="ee97e-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ee97e-107">任意の有効な式。</span><span class="sxs-lookup"><span data-stu-id="ee97e-107">Any valid expression.</span></span> <span data-ttu-id="ee97e-108">両方の式とも、暗黙的に変換可能なデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ee97e-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ee97e-109">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ee97e-109">Result Types</span></span>  
 <span data-ttu-id="ee97e-110">左の式が右の式と等しくない場合は`true` 、等しい場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="ee97e-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee97e-111">例</span><span class="sxs-lookup"><span data-stu-id="ee97e-111">Example</span></span>  
 <span data-ttu-id="ee97e-112">次の Entity SQL クエリは != 演算子を使用して 2 つの式を比較し、左の式が右の式と等しくないかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="ee97e-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="ee97e-113">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ee97e-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ee97e-114">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee97e-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ee97e-115">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ee97e-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ee97e-116">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ee97e-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ee97e-117">参照</span><span class="sxs-lookup"><span data-stu-id="ee97e-117">See Also</span></span>  
 [<span data-ttu-id="ee97e-118">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ee97e-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
