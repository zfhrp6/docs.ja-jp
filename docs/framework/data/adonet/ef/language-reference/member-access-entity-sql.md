---
title: ". (メンバー アクセス) (Entity SQL) | Microsoft Docs"
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
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# . (メンバー アクセス) (Entity SQL)
ドット演算子 \(.\) は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] メンバー アクセス演算子です。  メンバー アクセス演算子を使用すると、構造型概念モデル型のインスタンスのプロパティ値またはフィールド値を生成できます。  
  
## 構文  
  
```  
expression.identifier  
```  
  
## 引数  
 `expression`  
 構造型概念モデル型のインスタンス。  
  
 `identifier`  
 オブジェクト インスタンスに属するプロパティまたはフィールド。  
  
## 解説  
 ドット \(.\) 演算子は、複合型またはエンティティ型のプロパティの抽出と同様に、レコードからフィールドを抽出するために使用できます。  たとえば、Name 型の n が Person 型のメンバーであり、p が Person 型のインスタンスである場合、  p.n は有効なメンバー アクセス式として Name 型の値を生成します。  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)