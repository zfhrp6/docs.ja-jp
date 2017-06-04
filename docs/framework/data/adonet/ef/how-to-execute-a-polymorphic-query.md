---
title: "ポリモーフィック クエリを実行する方法 | Microsoft Docs"
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
  - "jsharp"
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ポリモーフィック クエリを実行する方法
このトピックでは、[OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) 演算子を使ってポリモーフィックな [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。  
  
### この例のコードを実行するには  
  
1.  [School Model](http://msdn.microsoft.com/ja-jp/859a9587-81ea-4a45-9bc0-f8d330e1adac) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
2.  アプリケーションのコード ページで、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  概念モデルを変更して、Table\-Per\-Hierarchy 継承を持つようにします。そのためには、「[Walkthrough: Mapping Inheritance \- Table\-per\-Hierarchy](http://msdn.microsoft.com/ja-jp/49b685cf-9db8-4d6d-b885-8837ed238f55)」で説明されている手順に従います。  
  
## 使用例  
 次の例では、OFTYPE 演算子を使用し、`Courses` のコレクションから `OnsiteCourses` のコレクションだけを取得して表示します。  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## 参照  
 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)   
 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)