---
title: "DEREF (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DEREF (Entity SQL)
参照値を逆参照し、その逆参照の結果を生成します。  
  
## 構文  
  
```  
  
SELECT DEREF ( o.expression) from Table as o;  
```  
  
## 引数  
 `expression`  
 コレクションを返す任意の有効なクエリ式。  
  
## 戻り値  
 参照されるエンティティの値。  
  
## 解説  
 DEREF 演算子は参照値を逆参照し、その逆参照の結果を生成します。 たとえば、 `r`  が ref\<T\> 型の参照である場合、 `Deref` `(r)`  は  `r` によって参照されるエンティティを生成する  `T`  型の式です。 参照値が null または未解決 \(つまり、参照先が存在しない\) の場合、DEREF 演算子の結果は null になります。  
  
## 使用例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、DEREF 演算子を使用して参照値を逆参照し、その逆参照の結果を生成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[PrimitiveType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として ExecutePrimitiveTypeQuery メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)   
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)   
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)   
 [NULL 値が許容される構造化型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)