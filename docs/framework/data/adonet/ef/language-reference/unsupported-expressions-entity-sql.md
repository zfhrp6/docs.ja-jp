---
title: "サポートされていない式 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# サポートされていない式 (Entity SQL)
このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていない [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] 式について説明します。詳細については、「[Entity SQL と Transact\-SQL の相違点](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)」を参照してください。  
  
## 定量化された述語  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] では、次の形式のコンストラクターを使用できます。  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 ただし、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、このようなコンストラクターがサポートされていません。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## \* 演算子  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] では、すべての列を投影する必要があることを示すために、SELECT 句で \* 演算子を使用できます。  これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。  
  
## 参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)   
 [Entity SQL と Transact\-SQL の相違点](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)