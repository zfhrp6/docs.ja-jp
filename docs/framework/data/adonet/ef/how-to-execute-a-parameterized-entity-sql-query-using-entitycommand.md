---
title: "EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する方法 | Microsoft Docs"
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
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する方法
このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して、パラメーター付きの [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。  
  
### この例のコードを実行するには  
  
1.  [AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) をプロジェクトに追加して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトを構成します。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
2.  アプリケーションのコード ページで、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## 使用例  
 次の例では、2 つのパラメーターを持つクエリ文字列を作成する方法を示します。  次に、<xref:System.Data.EntityClient.EntityCommand> を作成した後、2 つのパラメーターを <xref:System.Data.EntityClient.EntityCommand> の <xref:System.Data.EntityClient.EntityParameter> コレクションに追加し、`Contact` アイテムのコレクションに対して反復処理を実行します。  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## 参照  
 [How to: Execute a Parameterized Query](http://msdn.microsoft.com/ja-jp/42048f03-c65c-4d98-b50a-3e7d537a63e8)   
 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)