---
title: "EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する方法 | Microsoft Docs"
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
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する方法
このトピックでは、<xref:System.Data.EntityClient.EntityCommand> クラスを使用して、パラメーター化されたストアド プロシージャを実行する方法を示します。  
  
### この例のコードを実行するには  
  
1.  [School Model](http://msdn.microsoft.com/ja-jp/859a9587-81ea-4a45-9bc0-f8d330e1adac) をプロジェクトに追加して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトを構成します。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
2.  アプリケーションのコード ページで、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  `GetStudentGrades` ストアド プロシージャをインポートし、戻り値の型として `CourseGrade` エンティティを指定します。  ストアド プロシージャのインポート方法の詳細については、「[How to: Import a Stored Procedure](http://msdn.microsoft.com/ja-jp/24e68bf4-bd6d-428d-bc35-92d7b8e3736d)」を参照してください。  
  
## 使用例  
 次のコードでは、`GetStudentGrades` ストアド プロシージャが実行されます。`StudentId` は必須パラメーターです。  結果は <xref:System.Data.EntityClient.EntityDataReader> によって読み取られます。  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## 参照  
 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)