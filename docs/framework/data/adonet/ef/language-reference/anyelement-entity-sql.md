---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 11d1dd4b09ff07519f3435d313de72c5b9a3edf4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761845"
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="d0b43-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d0b43-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="d0b43-103">複数値のコレクションから要素を抽出します。</span><span class="sxs-lookup"><span data-stu-id="d0b43-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b43-104">構文</span><span class="sxs-lookup"><span data-stu-id="d0b43-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d0b43-105">引数</span><span class="sxs-lookup"><span data-stu-id="d0b43-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d0b43-106">要素の抽出元のコレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="d0b43-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0b43-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d0b43-107">Return Value</span></span>  
 <span data-ttu-id="d0b43-108">コレクションに複数の要素が存在する場合はコレクション内の単一の要素 (任意の要素) が、コレクションが空の場合は `null`が返されます。</span><span class="sxs-lookup"><span data-stu-id="d0b43-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="d0b43-109">場合`collection`型のコレクションは、 `Collection<T>`、し`ANYELEMENT(collection)`型のインスタンスを生成する有効な式です`T`です。</span><span class="sxs-lookup"><span data-stu-id="d0b43-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0b43-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d0b43-110">Remarks</span></span>  
 <span data-ttu-id="d0b43-111">ANYELEMENT では、複数値のコレクションから任意の要素が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="d0b43-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="d0b43-112">たとえば、次の例では、 `Customers`という集合から単一の要素が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="d0b43-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="d0b43-113">例</span><span class="sxs-lookup"><span data-stu-id="d0b43-113">Example</span></span>  
 <span data-ttu-id="d0b43-114">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、ANYELEMENT 演算子を使用して、複数値のコレクションから要素を抽出します。</span><span class="sxs-lookup"><span data-stu-id="d0b43-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="d0b43-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d0b43-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d0b43-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="d0b43-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d0b43-117">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d0b43-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d0b43-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="d0b43-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b43-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0b43-119">See Also</span></span>  
 [<span data-ttu-id="d0b43-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="d0b43-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d0b43-121">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="d0b43-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
