---
title: "FLATTEN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# FLATTEN (Entity SQL)
コレクションのコレクションをフラット化して単一のコレクションに変換します。 変換後のコレクションは、入れ子構造が失われるだけで、変換前のコレクションとまったく同じ要素を格納します。  
  
## 構文  
  
```  
  
FLATTEN ( collection )  
```  
  
## 引数  
 `collection`  
 値のコレクションのコレクションをフラット化して単一のコレクションとして返す有効な任意の式。  
  
## 解説  
 `FLATTEN` は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の優先順位に関する情報については、「[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)」をご覧ください。  
  
## 使用例  
 次の Entity SQL クエリでは、`FLATTEN` 演算子を使用して、コレクションのコレクションをフラット化されたコレクションに変換します。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)