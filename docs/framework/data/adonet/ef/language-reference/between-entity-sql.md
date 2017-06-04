---
title: "BETWEEN (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# BETWEEN (Entity SQL)
式の結果が指定の範囲内の値になるかどうかを判断します。[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の BETWEEN 式は、Transact\-SQL の BETWEEN 式と同じ効果を持ちます。  
  
## 構文  
  
```  
  
expression [ NOT ] BETWEEN begin_expression AND end_expression  
```  
  
## 引数  
 `expression`  
 `begin_expression` と `end_expression` で定義される範囲についてテストするための任意の有効な式。`expression` は、`begin_expression` と `end_expression` の両方と同じ型にする必要があります。  
  
 `begin_expression`  
 任意の有効な式。`begin_expression` は、`expression` と `end_expression` の両方と同じ型にする必要があります。`begin_expression` は、`end_expression` 未満でなければなりません。それ以外の場合、戻り値は否定されます。  
  
 `end_expression`  
 任意の有効な式。`end_expression` は、`expression` と `begin_expression` の両方と同じ型にする必要があります。  
  
 NOT  
 BETWEEN の結果を否定することを指定します。  
  
 AND  
 `expression` と `begin_expression` で表される範囲内で `end_expression` をテストする必要があることを示すプレースホルダーです。  
  
## 戻り値  
 `true` が、`expression` と `begin_expression` で指定される範囲内にある場合は `end_expression`。それ以外の場合は `false`。`null` が `expression` であるか、`null` または `begin_expression` が `end_expression` である場合は、`null` が返されます。  
  
## 解説  
 両端を除いた範囲を指定するには、BETWEEN の代わりに、より大きい \(\>\) とより小さい \(\<\) を意味する演算子を使用します。  
  
## 使用例  
 次の Entity SQL クエリでは、BETWEEN 演算子を使用して、式の結果が指定の範囲内の値になるかどうかを調べます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)