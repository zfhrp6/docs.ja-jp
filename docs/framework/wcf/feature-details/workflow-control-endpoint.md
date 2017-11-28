---
title: "ワークフロー コントロール エンドポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b3a4c1cbfd2ca95d3fc4d674fa6566e09fd9682
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-control-endpoint"></a>ワークフロー コントロール エンドポイント
ワークフロー コントロール エンドポイントは、開発者が管理操作を呼び出して、<xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされているワークフロー インスタンスをリモート制御できるようにします。 この機能を使用すると、一時停止、再開、終了などの管理操作をプログラムで実行することができます。  
  
> [!WARNING]
>  トランザクション内でワークフロー コントロール エンドポイントを使用していて、コントロールされているワークフローに <xref:System.Activities.Statements.Persist> アクティビティが含まれている場合、ワークフロー インスタンスはトランザクションがタイムアウトするまでハングします。  
  
## <a name="workflow-instance-management"></a>ワークフロー インスタンスの管理  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] は、<xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> と呼ばれる新しいコントラクトを定義します。 このコントラクトは、<xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされるワークフロー インスタンスをリモート制御する一連の管理操作を定義します。 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> は、<xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> コントラクトの実装を提供する標準のエンドポイントです。 <xref:System.ServiceModel.Activities.WorkflowControlClient> は、管理操作を <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> に送信するために使用するクラスです。  
  
 ワークフロー インスタンスには、次の状態があります。  
  
 アクティブ  
 完了した状態に達する前の、一時停止の状態でないときのワークフロー インスタンスの状態です。 この状態にあるときのワークフロー インスタンスは、アプリケーション メッセージを実行し、処理します。  
  
 Suspended  
 この状態にある間は、まだ実行が開始されていないアクティビティや、部分的に実行されているアクティビティがある場合でも、ワークフロー インスタンスは実行されません。  
  
 完了  
 ワークフロー インスタンスの最終的な状態です。 この状態に達した後は、ワークフロー インスタンスは実行できません。  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> インターフェイスでは、同期バージョンおよび非同期バージョンで、一連の管理操作が定義されます。 トランザクション処理されたバージョンでは、トランザクションに対応するバインディングを使用する必要があります。 次の表は、サポートされる管理操作の一覧を示します。  
  
|管理操作|説明|  
|-----------------------|-----------------|  
|[中止]|ワークフロー インスタンスの実行を強制的に停止します。|  
|キャンセル|ワークフロー インスタンスをアクティブ状態または一時停止状態から完了状態に移行します。|  
|実行|ワークフロー インスタンスに実行する機会を提供します。|  
|Suspend|ワークフロー インスタンスをアクティブ状態から一時停止状態に移行します。|  
|終了|ワークフロー インスタンスをアクティブ状態または一時停止状態から完了状態に移行します。|  
|Unsuspend|ワークフロー インスタンスを一時停止状態からアクティブ状態に移行します。|  
|TransactedCancel|クライアントからフローされた、またはローカルに作成されたトランザクションの下で Cancel 操作を実行します。 システムでワークフロー インスタンスの永続状態が維持される場合は、ワークフロー インスタンスが、この操作の実行中に持続している必要があります。|  
|TransactedRun|クライアントからフローされた、またはローカルに作成されたトランザクションの下で Run 操作を実行します。 システムでワークフロー インスタンスの永続状態が維持される場合は、ワークフロー インスタンスが、この操作の実行中に持続している必要があります。|  
|TransactedSuspend|クライアントからフローされた、またはローカルに作成されたトランザクションの下で Suspend 操作を実行します。 システムでワークフロー インスタンスの永続状態が維持される場合は、ワークフロー インスタンスが、この操作の実行中に持続している必要があります。|  
|TransactedTerminate|クライアントからフローされた、またはローカルに作成されたトランザクションの下で Terminate 操作を実行します。 システムでワークフロー インスタンスの永続状態が維持される場合は、ワークフロー インスタンスが、この操作の実行中に持続している必要があります。|  
|TransactedUnsuspend|クライアントからフローされた、またはローカルに作成されたトランザクションの下で Unsuspend 操作を実行します。 システムでワークフロー インスタンスの永続状態が維持される場合は、ワークフロー インスタンスが、この操作の実行中に持続している必要があります。|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> コントラクトは、新しいワークフロー インスタンスを作成する手段を提供せず、既存のワークフロー インスタンスを管理する手段のみを提供します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]リモートで、新しいワークフロー インスタンスを作成するを参照してください[ワークフロー サービス ホストの拡張機能](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)します。  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> は、固定コントラクト <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> を持つ標準のエンドポイントです。 <xref:System.ServiceModel.Activities.WorkflowServiceHost> インスタンスにこのエンドポイントが追加されると、このエンドポイントを使用して、ホスト インスタンスによってホストされる任意のワークフロー インスタンスにコマンド操作を送信できます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]標準エンドポイントを参照してください[標準エンドポイント](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)です。  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> は、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> の <xref:System.ServiceModel.Activities.WorkflowServiceHost> に制御メッセージを送信できるようにするクラスです。 このクラスには、トランザクション処理された操作を除き、<xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> コントラクトでサポートされる各操作用のメソッドが格納されています。 <xref:System.ServiceModel.Activities.WorkflowControlClient> では、アンビエント トランザクションを使用して、トランザクション処理された操作を使用する必要があるかどうかが判断されます。
