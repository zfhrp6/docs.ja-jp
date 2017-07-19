---
title: "WHERE (Entity SQL) | Microsoft Docs"
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
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# WHERE (Entity SQL)
WHERE 句は、[FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) 句の直後に適用されます。  
  
## 構文  
  
```  
[ WHERE expression ]  
```  
  
## 引数  
 `expression`  
 ブール型です。  
  
## 解説  
 WHERE 句は、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] で設定された場合と同じセマンティクスを持ちます。  ソース コレクションの要素を条件を満たすものに制限することで、クエリ式によって生成されるオブジェクトを制限します。  
  
```  
select c from cs as c where e  
```  
  
 式 `e` には Boolean 型が含まれる必要があります。  
  
 WHERE 句は、FROM 句の直後、およびグループ化、順序付け、または投影が実行される前に適用されます。  FROM 句で定義されたすべての要素名は、WHERE 句の式に対して表示されます。  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [クエリ式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)