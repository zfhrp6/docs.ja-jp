---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b844c5a132d36a4ca9d660607bbfe0f39ceab718
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759635"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="11164-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="11164-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="11164-103">物理的なページングは、ORDER BY 句の LIMIT サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="11164-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="11164-104">LIMIT は ORDER BY 句と切り離して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="11164-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11164-105">構文</span><span class="sxs-lookup"><span data-stu-id="11164-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="11164-106">引数</span><span class="sxs-lookup"><span data-stu-id="11164-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="11164-107">選択する項目の数。</span><span class="sxs-lookup"><span data-stu-id="11164-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="11164-108">LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="11164-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="11164-109">たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。</span><span class="sxs-lookup"><span data-stu-id="11164-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="11164-110">LIMIT は機能的に TOP と等価ですが、LIMIT では ORDER BY 句が存在する必要がある点が異なります。</span><span class="sxs-lookup"><span data-stu-id="11164-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="11164-111">SKIP および LIMIT は ORDER BY 句と共に別々に使用できます。</span><span class="sxs-lookup"><span data-stu-id="11164-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11164-112">TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合には、Entity Sql クエリは無効と見なされます。</span><span class="sxs-lookup"><span data-stu-id="11164-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="11164-113">TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="11164-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11164-114">例</span><span class="sxs-lookup"><span data-stu-id="11164-114">Example</span></span>  
 <span data-ttu-id="11164-115">次の Entity SQL クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を LIMIT と共に使用します。</span><span class="sxs-lookup"><span data-stu-id="11164-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="11164-116">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="11164-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="11164-117">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="11164-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="11164-118">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="11164-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="11164-119">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="11164-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="11164-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="11164-120">See Also</span></span>  
 [<span data-ttu-id="11164-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="11164-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="11164-122">方法: 結果をクエリ ページング</span><span class="sxs-lookup"><span data-stu-id="11164-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="11164-123">ページング</span><span class="sxs-lookup"><span data-stu-id="11164-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="11164-124">TOP</span><span class="sxs-lookup"><span data-stu-id="11164-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
