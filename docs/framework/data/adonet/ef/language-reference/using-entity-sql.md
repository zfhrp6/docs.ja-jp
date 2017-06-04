---
title: "USING (Entity SQL) | Microsoft Docs"
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
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# USING (Entity SQL)
クエリ式で使用する名前空間を指定します。  
  
## 構文  
  
```  
USING [ alias = ] namespace  
```  
  
## 引数  
 `alias`  
 名前空間を修飾する短い別名。  
  
 `namespace`  
 任意の有効な名前空間。  
  
## 使用例  
 次の Entity SQL クエリでは、USING 演算子を使用して、クエリ式に使用する名前空間が指定されています。  このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[PrimitiveType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
```  
using SqlServer; RAND()  
```  
  
## 参照  
 [名前空間](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)   
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)