---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: c35cac018392aa9688866e280ff64fdf6a1453f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="key-entity-sql"></a><span data-ttu-id="27db7-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="27db7-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="27db7-103">参照またはエンティティ式のキーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="27db7-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27db7-104">構文</span><span class="sxs-lookup"><span data-stu-id="27db7-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="27db7-105">コメント</span><span class="sxs-lookup"><span data-stu-id="27db7-105">Remarks</span></span>  
 <span data-ttu-id="27db7-106">エンティティ キーには、指定されたエンティティまたはエンティティ参照の正しい順序でキー値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="27db7-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="27db7-107">複数のエンティティ セットが同じ型に基づくことができるので、同じキーがそれぞれのエンティティ セットで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="27db7-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="27db7-108">一意の参照を取得するには、 `REF`を使用します。</span><span class="sxs-lookup"><span data-stu-id="27db7-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="27db7-109">KEY 演算子の戻り値の型は、同じ順序でエンティティの各キーの 1 つのフィールドを含む行型です。</span><span class="sxs-lookup"><span data-stu-id="27db7-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="27db7-110">次の例では、キー演算子は、BadOrder エンティティへの参照に渡され、その参照のキー部分を返します。</span><span class="sxs-lookup"><span data-stu-id="27db7-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="27db7-111">この場合、 `Id` プロパティに対応する 1 つだけのフィールドを持つレコード型です。</span><span class="sxs-lookup"><span data-stu-id="27db7-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="27db7-112">例</span><span class="sxs-lookup"><span data-stu-id="27db7-112">Example</span></span>  
 <span data-ttu-id="27db7-113">次の Entity SQL クエリは、KEY 演算子を使用して、型参照を持つ式のキー部分を抽出します。</span><span class="sxs-lookup"><span data-stu-id="27db7-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="27db7-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="27db7-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="27db7-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="27db7-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="27db7-116">「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="27db7-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="27db7-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="27db7-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="27db7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="27db7-118">See Also</span></span>  
 [<span data-ttu-id="27db7-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="27db7-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="27db7-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="27db7-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="27db7-121">REF</span><span class="sxs-lookup"><span data-stu-id="27db7-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="27db7-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="27db7-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
