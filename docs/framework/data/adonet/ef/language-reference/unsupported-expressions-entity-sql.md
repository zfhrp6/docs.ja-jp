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
# <a name="unsupported-expressions"></a>サポートされていない式

このトピックでは、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] でサポートされていない [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 式について説明します。 詳細については、次を参照してください。[エンティティの SQL と TRANSACT-SQL の異なる](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)です。

## <a name="quantified-predicates"></a>定量化された述語

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 次の形式のコンストラクトを使用できます。

```sql
sal > all (select salary from employees)
sal > any (select salary from employees)
```

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]、ただし、たとえばコンス トラクターはサポートされません。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。

```sql
not exists(select 0 from employees as e where sal > e.salary)
exists(select 0 from employees as e where sal > e.salary)
```

## <a name="-operator"></a>* 演算子

[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 使用をサポートしている、* をすべての列を予測するかを示すために、SELECT 句内の演算子。これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。

## <a name="see-also"></a>関連項目

[Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
[Entity SQL と Transact-SQL の相違点](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
