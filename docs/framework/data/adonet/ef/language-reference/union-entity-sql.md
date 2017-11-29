---
title: UNION (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b62d874a9885ed864282c765cf428f3c2a445745
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="union-entity-sql"></a><span data-ttu-id="30886-102">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="30886-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="30886-103">複数のクエリの結果を 1 つのコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="30886-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30886-104">構文</span><span class="sxs-lookup"><span data-stu-id="30886-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="30886-105">引数</span><span class="sxs-lookup"><span data-stu-id="30886-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="30886-106">コレクションと結合するコレクションを返す任意の有効なクエリ式。すべての式は、 `expression`と同じ型であるか、共通の基本データ型または派生型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="30886-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="30886-107">UNION</span><span class="sxs-lookup"><span data-stu-id="30886-107">UNION</span></span>  
 <span data-ttu-id="30886-108">複数のコレクションを結合し、1 つのコレクションとして返すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="30886-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="30886-109">ALL</span><span class="sxs-lookup"><span data-stu-id="30886-109">ALL</span></span>  
 <span data-ttu-id="30886-110">複数のコレクションを結合し、重複も含めて 1 つのコレクションとして返すことを指定します。</span><span class="sxs-lookup"><span data-stu-id="30886-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="30886-111">指定しない場合、重複は結果コレクションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="30886-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30886-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="30886-112">Return Value</span></span>  
 <span data-ttu-id="30886-113">`expression`と同じ型であるか、共通の基本データ型または派生型であるコレクション。</span><span class="sxs-lookup"><span data-stu-id="30886-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30886-114">コメント</span><span class="sxs-lookup"><span data-stu-id="30886-114">Remarks</span></span>  
 <span data-ttu-id="30886-115">UNION は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="30886-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="30886-116">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。</span><span class="sxs-lookup"><span data-stu-id="30886-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="30886-117">優先順位について、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set 演算子を参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="30886-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30886-118">例</span><span class="sxs-lookup"><span data-stu-id="30886-118">Example</span></span>  
 <span data-ttu-id="30886-119">次の Entity SQL クエリでは、UNION ALL 演算子を使用して、2 つのクエリの結果を 1 つのコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="30886-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="30886-120">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="30886-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="30886-121">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="30886-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="30886-122">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="30886-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="30886-123">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="30886-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="30886-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="30886-124">See Also</span></span>  
 [<span data-ttu-id="30886-125">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="30886-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
