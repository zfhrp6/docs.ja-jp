---
title: "ワークフローの永続性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プログラミング [WF], 永続性"
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# ワークフローの永続性
ワークフローの永続化は、プロセスやコンピューターの情報とは独立した、ワークフロー インスタンスの状態の永続的なキャプチャです。永続化の目的は、システム生涯時にワークフロー インスタンスの既知の回復ポイントを提供するため、アクティブに作業を実行していないワークフロー インスタンスをアンロードしてメモリを節約するため、またはワークフロー インスタンスの状態をサーバー ファーム内のあるノードから別のノードに移行するためです。  
  
 永続化によって、プロセスの迅速性、拡張性、エラー時の回復、およびメモリをより効率的に管理できる機能を実現できます。永続化プロセスには永続化ポイントの指定や保存するデータの収集が含まれ、最終的にはデータの実際のストレージが永続化プロバイダーにデリゲートされます。  
  
 ワークフローの永続化を有効にするには、「[ワークフローとワークフロー サービスの永続化を有効にする方法](../../../docs/framework/windows-workflow-foundation//how-to-enable-persistence-for-workflows-and-workflow-services.md)」の説明に従って、インスタンス ストアを **WorkflowApplication** または **WorkflowServiceHost** に関連付ける必要があります。**WorkflowApplication** と **WorkflowServiceHost** は、それらに関連付けられているインスタンス ストアを使用して、ワークフロー インスタンスを永続化ストアに永続化し、永続化ストアに格納されているワークフロー インスタンス データに基づいてワークフロー インスタンスをメモリに読み込む処理を有効にします。  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] には **SqlWorkflowInstanceStore** クラスがあります。このクラスを使用すると、ワークフロー インスタンスに関するデータおよびメタデータを SQL Server 2005 または SQL Server 2008 のデータベースに永続化できます。詳細については、「[SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)」を参照してください。  
  
 アプリケーション固有のデータをワークフロー インスタンス関連の情報と共に格納し、読み込むために、<xref:System.Activities.Persistence.PersistenceParticipant> クラスを拡張する永続参加要素を作成できます。永続参加要素は永続化プロセスに参加して、カスタムのシリアル化可能なデータを永続化ストアに保存し、インスタンス ストアからメモリにデータを読み込み、永続化トランザクションで任意の追加ロジックを実行します。詳細については、「[永続参加要素](../../../docs/framework/windows-workflow-foundation//persistence-participants.md)」を参照してください。  
  
 Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric での永続化の概念](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## 暗黙的な永続化ポイント  
 次の一覧は、インスタンス ストアがワークフローに関連付けられている場合にワークフローが永続化される条件の例です。  
  
-   **TransactionScope** アクティビティまたは **TransactedReceiveScope** アクティビティが完了したとき。  
  
-   ワークフロー インスタンスがアイドルになり、**WorkflowIdleBehavior** がワークフロー ホストに設定されたとき。たとえば、メッセージング アクティビティ、つまり **Delay** アクティビティを使用すると、この処理が発生します。  
  
-   WorkflowApplication がアイドルになり、アプリケーションの **PersistableIdle** プロパティが **PersistableIdleAction.Persist** に設定されたとき。  
  
-   ホスト アプリケーションに対して、ワークフロー インスタンスの永続化またはアンロードが指示されたとき。  
  
-   ワークフロー インスタンスが終了したとき。  
  
-   **Persist** アクティビティが実行されたとき。  
  
-   以前のバージョンの Windows Workflow Foundation を使用して開発したワークフロー インスタンスが、相互運用可能な実行中に永続化ポイントに到達したとき。  
  
## このセクションの内容  
  
-   [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation//sql-workflow-instance-store.md)  
  
-   [インスタンス ストア](../../../docs/framework/windows-workflow-foundation//instance-stores.md)  
  
-   [永続参加要素](../../../docs/framework/windows-workflow-foundation//persistence-participants.md)  
  
-   [永続化のベスト プラクティス](../../../docs/framework/windows-workflow-foundation//persistence-best-practices.md)  
  
-   [非永続化ワークフロー インスタンス](../../../docs/framework/windows-workflow-foundation//non-persisted-workflow-instances.md)  
  
-   [ワークフローの一時停止と再開](../../../docs/framework/windows-workflow-foundation//pausing-and-resuming-a-workflow.md)