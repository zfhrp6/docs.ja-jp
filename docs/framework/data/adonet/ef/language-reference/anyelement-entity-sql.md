---
title: "ANYELEMENT (Entity SQL) | Microsoft Docs"
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
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ANYELEMENT (Entity SQL)
複数値のコレクションから要素を抽出します。  
  
## 構文  
  
```  
  
ANYELEMENT (expression)  
```  
  
## 引数  
 `expression`  
 要素の抽出元のコレクションを返す任意の有効なクエリ式。  
  
## 戻り値  
 コレクションに複数の要素が存在する場合はコレクション内の単一の要素 \(任意の要素\) が、コレクションが空の場合は `null` が返されます。```collection``` が `Collection<T>` 型のコレクションである場合、 `ANYELEMENT(collection)`  は、`T` 型のインスタンスを生成する正しい式です。  
  
## 解説  
 ANYELEMENT では、複数値のコレクションから任意の要素が抽出されます。 たとえば、次の例では、 `Customers` という集合から単一の要素が抽出されます。  
  
```  
ANYELEMENT(Customers)  
```  
  
## 使用例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、ANYELEMENT 演算子を使用して、複数値のコレクションから要素を抽出します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [NULL 値が許容される構造化型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)