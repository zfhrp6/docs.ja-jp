---
title: サポートされていない式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
dev_langs:
- sql
ms.openlocfilehash: 6d1746bb51af4795f09c47f808cf9a29d0370f18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="92d8e-102">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="92d8e-102">Unsupported expressions</span></span>

<span data-ttu-id="92d8e-103">このトピックでは、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] でサポートされていない [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 式について説明します。</span><span class="sxs-lookup"><span data-stu-id="92d8e-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="92d8e-104">詳細については、次を参照してください。[エンティティの SQL と TRANSACT-SQL の異なる](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="92d8e-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="92d8e-105">定量化された述語</span><span class="sxs-lookup"><span data-stu-id="92d8e-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="92d8e-106"> では、次の形式のコンストラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="92d8e-106"> allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

<span data-ttu-id="92d8e-107">ただし、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、このようなコンストラクターがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92d8e-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="92d8e-108">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="92d8e-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="92d8e-109">\* 演算子</span><span class="sxs-lookup"><span data-stu-id="92d8e-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="92d8e-110"> では、すべての列を投影する必要があることを示すために、SELECT 句で \* 演算子を使用できます。これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="92d8e-110"> supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="92d8e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="92d8e-111">See also</span></span>

[<span data-ttu-id="92d8e-112">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="92d8e-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="92d8e-113">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="92d8e-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
