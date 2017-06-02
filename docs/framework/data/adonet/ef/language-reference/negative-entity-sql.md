---
title: "- (負符号) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# - (負符号) (Entity SQL)
数値式の負の値を返します。  
  
## 構文  
  
```  
  
-  
expression  
  
```  
  
## 引数  
 `expression`  
 任意の数値データ型の有効な式。  
  
## 戻り値の型  
 `expression` のデータ型。  
  
## 解説  
 符号なしの型を `expression` に指定した場合、戻り値の型は、`expression` の型と最も関連性の高い符号付きの型になります。 たとえば、`expression` に Byte 型を指定した場合、Int16 型の値が返されます。  
  
## 使用例  
 次の Entity SQL クエリでは、\- 算術演算子を使用して、数値式の負の値を返します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)