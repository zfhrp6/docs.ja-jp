---
title: "クエリ式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ad130797be55b33b319ca4e85de09ec3e00a554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="c2994-102">クエリ式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c2994-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="c2994-103">クエリ式とは、さまざまなクエリ演算子を組み合わせて 1 つの構文にしたものです。</span><span class="sxs-lookup"><span data-stu-id="c2994-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="c2994-104">たとえば、次の式のさまざまな種類が用意されて:[リテラル](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)、[パラメーター](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)、[変数](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)、演算子、[関数](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)、set 演算子、およびなどです。</span><span class="sxs-lookup"><span data-stu-id="c2994-104"> provides various kinds of expressions, including the following: [literals](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parameters](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operators, [functions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="c2994-105">詳細については、次を参照してください。 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2994-105">For more information, see [Entity SQL Reference](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="c2994-106">句</span><span class="sxs-lookup"><span data-stu-id="c2994-106">Clauses</span></span>  
 <span data-ttu-id="c2994-107">クエリ式は、オブジェクトのコレクションに連続した操作を適用する一連の句で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c2994-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="c2994-108">SQL select ステートメントの標準で検出されたのと同じ句に基づいている:[選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)、 [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md)、[場所](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md)、 [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)、 [を持つ](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md)、および[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2994-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), and [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="c2994-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="c2994-109">Scope</span></span>  
 <span data-ttu-id="c2994-110">FROM 句で定義された名前は、出現順 (左から右の順) に FROM スコープに導入されます。</span><span class="sxs-lookup"><span data-stu-id="c2994-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="c2994-111">JOIN リストでは、式は既にリストで定義されている名前を参照できます。</span><span class="sxs-lookup"><span data-stu-id="c2994-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="c2994-112">FROM 句で指定された要素のパブリック プロパティは FROM スコープには追加されません。それらは常に別名で修飾された名前で参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2994-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="c2994-113">通常は、SELECT 式のすべての部分が FROM スコープに含まれると見なされます。</span><span class="sxs-lookup"><span data-stu-id="c2994-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2994-114">参照</span><span class="sxs-lookup"><span data-stu-id="c2994-114">See Also</span></span>  
 [<span data-ttu-id="c2994-115">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="c2994-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
