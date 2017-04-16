---
title: "COLLECTION (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# COLLECTION (Entity SQL)
COLLECTION キーワードは、インライン関数を定義する場合にのみ使用します。 コレクション関数は、値のコレクションを操作してスカラー出力を生成する関数です。  
  
## 構文  
  
```  
  
COLLECTION(type_definition)   
```  
  
## 引数  
 `type_definition`  
 サポートされる型、行、または参照のコレクションを返す式。  
  
## 解説  
 COLLECTION キーワードについて詳しくは、「[型定義](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)」をご覧ください。  
  
## 使用例  
 次の例は、COLLECTION キーワードを使用して 10 進数のコレクションをインライン クエリ関数の引数として宣言する方法を示します。  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)