---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 43c038e9ff0acfdeff88492aa2ca34fbf4ada94a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764315"
---
# <a name="where-entity-sql"></a><span data-ttu-id="36cf2-102">WHERE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="36cf2-102">WHERE (Entity SQL)</span></span>
<span data-ttu-id="36cf2-103">WHERE 句が後に直接適用される、 [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)句。</span><span class="sxs-lookup"><span data-stu-id="36cf2-103">The WHERE clause is applied directly after the [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36cf2-104">構文</span><span class="sxs-lookup"><span data-stu-id="36cf2-104">Syntax</span></span>  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="36cf2-105">引数</span><span class="sxs-lookup"><span data-stu-id="36cf2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="36cf2-106">ブール型です。</span><span class="sxs-lookup"><span data-stu-id="36cf2-106">A Boolean type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36cf2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="36cf2-107">Remarks</span></span>  
 <span data-ttu-id="36cf2-108">WHERE 句は、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] で設定された場合と同じセマンティクスを持ちます。</span><span class="sxs-lookup"><span data-stu-id="36cf2-108">The WHERE clause has the same semantics as described for [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="36cf2-109">ソース コレクションの要素を条件を満たすものに制限することで、クエリ式によって生成されるオブジェクトを制限します。</span><span class="sxs-lookup"><span data-stu-id="36cf2-109">It restricts the objects produced by the query expression by limiting the elements of the source collections to those that pass the condition.</span></span>  
  
```  
select c from cs as c where e  
```  
  
 <span data-ttu-id="36cf2-110">式 `e` には Boolean 型が含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="36cf2-110">The expression `e` must have the type Boolean.</span></span>  
  
 <span data-ttu-id="36cf2-111">WHERE 句は、FROM 句の直後、およびグループ化、順序付け、または投影が実行される前に適用されます。</span><span class="sxs-lookup"><span data-stu-id="36cf2-111">The WHERE clause is applied directly after the FROM clause and before any grouping, ordering, or projection takes place.</span></span> <span data-ttu-id="36cf2-112">FROM 句で定義されたすべての要素名は、WHERE 句の式に対して表示されます。</span><span class="sxs-lookup"><span data-stu-id="36cf2-112">All element names defined in the FROM clause are visible to the expression of the WHERE clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36cf2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="36cf2-113">See Also</span></span>  
 [<span data-ttu-id="36cf2-114">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="36cf2-114">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="36cf2-115">クエリ式</span><span class="sxs-lookup"><span data-stu-id="36cf2-115">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
