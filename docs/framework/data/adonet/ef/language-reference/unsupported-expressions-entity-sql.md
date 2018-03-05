---
title: "サポートされていない式 (Entity SQL)"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-ado
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
dev_langs:
- sql
ms.openlocfilehash: 075daf0e4f0477dda50231760fbb3d990a9f8468
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="unsupported-expressions"></a><span data-ttu-id="9d04b-102">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="9d04b-102">Unsupported expressions</span></span>

<span data-ttu-id="9d04b-103">このトピックでは、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] でサポートされていない [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 式について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d04b-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="9d04b-104">詳細については、次を参照してください。[エンティティの SQL と TRANSACT-SQL の異なる](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d04b-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>

## <a name="quantified-predicates"></a><span data-ttu-id="9d04b-105">定量化された述語</span><span class="sxs-lookup"><span data-stu-id="9d04b-105">Quantified predicates</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="9d04b-106">次の形式のコンストラクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d04b-106">allows constructs of the following form:</span></span>

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="9d04b-107">、ただし、たとえばコンス トラクターはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9d04b-107">, however, does not support such constructs.</span></span> <span data-ttu-id="9d04b-108">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="9d04b-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a><span data-ttu-id="9d04b-109">\* 演算子</span><span class="sxs-lookup"><span data-stu-id="9d04b-109">\* operator</span></span>

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] <span data-ttu-id="9d04b-110">使用をサポートしている、\* をすべての列を予測するかを示すために、SELECT 句内の演算子。これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9d04b-110">supports the use of the \* operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="9d04b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d04b-111">See also</span></span>

[<span data-ttu-id="9d04b-112">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="9d04b-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[<span data-ttu-id="9d04b-113">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="9d04b-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
