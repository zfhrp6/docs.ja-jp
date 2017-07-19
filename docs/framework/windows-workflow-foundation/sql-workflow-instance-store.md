---
title: "SQL Workflow Instance Store | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# SQL Workflow Instance Store
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には SQL Workflow Instance Store が含まれます。これを使用すると、ワークフロー インスタンスに関する状態情報を SQL Server 2005 または SQL Server 2008 のデータベースに永続化できます。この機能は主に <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> クラスの形式で実装されます。このクラスは永続化フレームワークの <xref:System.Runtime.Persistence.InstanceStore> 抽象クラスから派生します。SQL Workflow Instance Store 機能によって SQL 永続性プロバイダーを構成します。このプロバイダーは、ホストが永続化コマンドをストアに送信するときに使用する永続化 API の具象実装です。  
  
 SQL Workflow Instance Store は、セルフホストされているワークフローや、<xref:System.Activities.WorkflowApplication> または <xref:System.ServiceModel.WorkflowServiceHost> を使用するワークフロー サービスだけでなく、<xref:System.ServiceModel.WorkflowServiceHost> を使用して WAS でホストされるサービスをサポートします。セルフホストされているサービスの SQL Workflow Instance Store 機能をプログラムで構成するには、この機能が公開しているオブジェクト モデルを使用します。プログラムでオブジェクト モデルや XML 構成ファイルを使用することにより、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるサービスについてこの機能を構成できます。  
  
 SQL Workflow Instance Store 機能 \(**SqlWorkflowInstanceStore** クラス\) は <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> を実装していないため、ワークフロー以外の継続的な WCF サービスをサポートする永続化は提供しません。また、<xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> を実装していないため、3.x ワークフローの永続化は提供しません。この機能は、WF 4.0 \(以降\) のワークフローとワークフロー サービスについてのみ永続化をサポートします。また、SQL Server 2005 と SQL Server 2008 以外のデータベースはサポートしません。  
  
 このセクションのトピックでは、SQL Workflow Instance Store のプロパティと機能、およびストアの構成方法の詳細を説明します。  
  
 Windows Server App Fabric は、インスタンス ストアの構成と使用を単純化する独自のインスタンス ストアとツールを提供します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] 「[Windows Server App Fabric Instance Store](http://go.microsoft.com/fwlink/?LinkId=201201)」を参照してください。App Fabric SQL Server 永続化データベース[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[App Fabric SQL Server 永続化データベース](http://go.microsoft.com/fwlink/?LinkId=201202)」を参照してください。  
  
## このセクションの内容  
  
-   [SQL Workflow Instance Store のプロパティ](../../../docs/framework/windows-workflow-foundation//properties-of-sql-workflow-instance-store.md)  
  
-   [ワークフローとワークフロー サービスの SQL 永続性を有効にする方法](../../../docs/framework/windows-workflow-foundation//how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [インスタンスのアクティブ化処理](../../../docs/framework/windows-workflow-foundation//instance-activation.md)  
  
-   [クエリのサポート](../../../docs/framework/windows-workflow-foundation//support-for-queries.md)  
  
-   [ストア拡張](../../../docs/framework/windows-workflow-foundation//store-extensibility.md)  
  
-   [セキュリティ](../../../docs/framework/windows-workflow-foundation//security.md)  
  
-   [SQL Server 永続性データベース](../../../docs/framework/windows-workflow-foundation//sql-server-persistence-database.md)  
  
## 参照  
 [永続化のサンプル](http://go.microsoft.com/fwlink/?LinkID=177735)