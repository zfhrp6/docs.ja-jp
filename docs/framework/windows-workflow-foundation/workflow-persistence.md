---
title: "ワークフローの永続性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e65f07fc01d0d364d7271c4f1378b968b687881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-persistence"></a>ワークフローの永続性
ワークフローの永続化は、ワークフロー インスタンスの状態を、プロセスやコンピューターの情報に依存せず永続的にキャプチャしたものです。 永続化の目的は、システム生涯時にワークフロー インスタンスの既知の回復ポイントを提供するため、アクティブに作業を実行していないワークフロー インスタンスをアンロードしてメモリを節約するため、またはワークフロー インスタンスの状態をサーバー ファーム内のあるノードから別のノードに移行するためです。  
  
 永続化によって、プロセスの迅速性、拡張性、エラー時の回復、およびメモリをより効率的に管理できる機能を実現できます。 永続化プロセスには永続化ポイントの指定や保存するデータの収集が含まれ、最終的にはデータの実際のストレージが永続化プロバイダーにデリゲートされます。  
  
 ワークフローの永続化を有効にするには、インスタンス ストアに関連付ける必要があります、 **WorkflowApplication**または**WorkflowServiceHost**で示した[する方法: 永続化を有効にします。ワークフローとワークフロー サービス](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)です。 **WorkflowApplication**と**WorkflowServiceHost**それらに関連付けられたインスタンス ストアを使用して、永続化ストアおよびにワークフロー インスタンスの読み込みに永続化ワークフロー インスタンスを有効にするには永続化ストアに格納されているワークフロー インスタンスのデータに基づくメモリです。  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]が付属しています、 **SqlWorkflowInstanceStore**クラスは、SQL Server 2005 または SQL Server 2008 データベースにワークフロー インスタンスに関するデータおよびメタデータの永続化できます。 参照してください[SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)詳細についてはします。  
  
 アプリケーション固有のデータをワークフロー インスタンス関連の情報と共に格納し、読み込むために、<xref:System.Activities.Persistence.PersistenceParticipant> クラスを拡張する永続参加要素を作成できます。 永続参加要素は永続化プロセスに参加して、カスタムのシリアル化可能なデータを永続化ストアに保存し、インスタンス ストアからメモリにデータを読み込み、永続化トランザクションで任意の追加ロジックを実行します。 詳細については、次を参照してください。[永続参加要素](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)です。  
  
 Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric で永続化の概念](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>暗黙的な永続化ポイント  
 次の一覧は、インスタンス ストアがワークフローに関連付けられている場合にワークフローが永続化される条件の例です。  
  
-   ときに、 **TransactionScope**アクティビティの完了または**TransactedReceiveScope**アクティビティが完了します。  
  
-   ワークフロー インスタンスがアイドル状態になったと**WorkflowIdleBehavior**ワークフロー ホストに設定します。 これが発生した、たとえば、メッセージング アクティビティを使用する場合、または、**遅延**アクティビティ。  
  
-   WorkflowApplication がアイドル状態になったと**PersistableIdle**アプリケーションのプロパティに設定されて**PersistableIdleAction.Persist**です。  
  
-   ホスト アプリケーションに対して、ワークフロー インスタンスの永続化またはアンロードが指示されたとき。  
  
-   ワークフロー インスタンスが終了したとき。  
  
-   ときに、 **Persist**アクティビティを実行します。  
  
-   以前のバージョンの Windows Workflow Foundation を使用して開発したワークフロー インスタンスが、相互運用可能な実行中に永続化ポイントに到達したとき。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [インスタンス ストア](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [永続参加要素](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [永続化のベスト プラクティス](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [非永続化ワークフロー インスタンス](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [ワークフローの一時停止と再開](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
