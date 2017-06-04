---
title: "EntityConnection の接続文字列を作成する方法 | Microsoft Docs"
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
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# EntityConnection の接続文字列を作成する方法
このトピックでは、<xref:System.Data.EntityClient.EntityConnection> を作成する方法について説明します。  
  
### この例のコードを実行するには  
  
1.  [AdventureWorks Sales Model](http://msdn.microsoft.com/ja-jp/f16cd988-673f-4376-b034-129ca93c7832) をプロジェクトに追加して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を使用するようにプロジェクトを構成します。  詳細については、「[How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/ja-jp/dadb058a-c5d9-4c5c-8b01-28044112231d)」を参照してください。  
  
2.  アプリケーションのコード ページで、次の `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## 使用例  
 次の例では、基になるプロバイダーの <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> を初期化した後、<xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=fullName> オブジェクトを初期化して、このオブジェクトを <xref:System.Data.EntityClient.EntityConnection> のコンストラクターに渡しています。  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## 参照  
 [How to: Use EntityConnection with an Object Context](http://msdn.microsoft.com/ja-jp/2140fe7b-b88b-47c8-a749-d7f142eb1080)   
 [Entity Framework 用の EntityClient プロバイダー](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)