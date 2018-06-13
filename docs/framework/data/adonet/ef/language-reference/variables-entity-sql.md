---
title: 変数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: f271ffc31875e7d94a27f4752b71bfe508fcb620
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765517"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="11f9f-102">変数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="11f9f-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="11f9f-103">変数</span><span class="sxs-lookup"><span data-stu-id="11f9f-103">Variable</span></span>  
 <span data-ttu-id="11f9f-104">変数式は、現在のスコープで定義されている名前付きの式への参照です。</span><span class="sxs-lookup"><span data-stu-id="11f9f-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="11f9f-105">変数の参照を有効にする必要があります[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別子で定義されている[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="11f9f-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="11f9f-106">次の例は、式における変数の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="11f9f-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="11f9f-107">FROM 句の `c` は変数の定義です。</span><span class="sxs-lookup"><span data-stu-id="11f9f-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="11f9f-108">SELECT 句内で使用された `c` は、変数参照を表します。</span><span class="sxs-lookup"><span data-stu-id="11f9f-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="11f9f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="11f9f-109">See Also</span></span>  
 [<span data-ttu-id="11f9f-110">識別子</span><span class="sxs-lookup"><span data-stu-id="11f9f-110">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [<span data-ttu-id="11f9f-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11f9f-111">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [<span data-ttu-id="11f9f-112">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="11f9f-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
