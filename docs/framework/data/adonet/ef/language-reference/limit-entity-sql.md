---
title: LIMIT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c890bf6950f94c04350902276193f5a43239f63f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="limit-entity-sql"></a><span data-ttu-id="f9e9c-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f9e9c-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="f9e9c-103">物理的なページングは、ORDER BY 句の LIMIT サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="f9e9c-104">LIMIT は ORDER BY 句と切り離して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e9c-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9e9c-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9e9c-106">引数</span><span class="sxs-lookup"><span data-stu-id="f9e9c-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="f9e9c-107">選択する項目の数。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="f9e9c-108">LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="f9e9c-109">たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="f9e9c-110">LIMIT は機能的に TOP と等価ですが、LIMIT では ORDER BY 句が存在する必要がある点が異なります。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="f9e9c-111">SKIP および LIMIT は ORDER BY 句と共に別々に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9e9c-112">TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合には、Entity Sql クエリは無効と見なされます。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="f9e9c-113">TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9e9c-114">例</span><span class="sxs-lookup"><span data-stu-id="f9e9c-114">Example</span></span>  
 <span data-ttu-id="f9e9c-115">次の Entity SQL クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を LIMIT と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="f9e9c-116">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f9e9c-117">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f9e9c-118">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f9e9c-119">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f9e9c-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="f9e9c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9e9c-120">See Also</span></span>  
 [<span data-ttu-id="f9e9c-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="f9e9c-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="f9e9c-122">方法: 結果をクエリ ページング</span><span class="sxs-lookup"><span data-stu-id="f9e9c-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="f9e9c-123">ページング</span><span class="sxs-lookup"><span data-stu-id="f9e9c-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="f9e9c-124">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="f9e9c-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
