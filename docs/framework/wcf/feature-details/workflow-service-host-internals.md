---
title: "ワークフロー サービス ホストの内部 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ワークフロー サービス ホストの内部
<xref:System.ServiceModel.WorkflowServiceHost> では、ワークフロー サービスのホストが提供されます。これにより、受信メッセージをリッスンして、該当するワークフロー サービス インスタンスにルーティングし、アイドル状態のワークフローのアンロードおよび永続化を制御できます。このトピックでは、WorkflowServiceHost がどのように受信メッセージを処理するかについて説明します。  
  
## WorkflowServiceHost の概要  
 <xref:System.ServiceModel.WorkflowServiceHost> クラスは、ワークフロー サービスをホストするために使用されます。このクラスは、受信メッセージをリッスンして、該当するサービス インスタンスにルーティングし、必要に応じて、新しいインスタンスを作成するか、永続ストレージから既存のインスタンスを読み込みます。次の図は、<xref:System.ServiceModel.WorkflowServiceHost> の動作の概要を示しています。  
  
 ![WorkflowServiceHost の概要](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 この図では、<xref:System.ServiceModel.WorkflowServiceHost> は .xamlx ファイルからワークフロー サービス定義を読み込み、構成ファイルから構成情報を読み込みます。また、追跡プロファイルから追跡構成を読み込みます。<xref:System.ServiceModel.WorkflowServiceHost> によって、ワークフロー インスタンスへの制御操作の送信を可能にするワークフロー コントロール エンドポイントが公開されます。詳細については、「[ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)」および「[ワークフロー管理エンドポイントのサンプル](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)」を参照してください。  
  
 <xref:System.ServiceModel.WorkflowServiceHost> によって、受信アプリケーション メッセージをリッスンするアプリケーション エンドポイントも公開されます。受信メッセージが到着すると、該当するワークフロー サービス インスタンスに送られます \(現在読み込み中の場合\)。必要に応じて、新しいワークフロー インスタンスが作成されます。既存のインスタンスが永続化されている場合は、永続ストアから読み込まれます。  
  
## WorkflowServiceHost の詳細  
 次の図は、<xref:System.ServiceModel.WorkflowServiceHost> がメッセージを処理する方法をさらに詳細に示しています。  
  
 ![ワークフロー サービス ホストのメッセージ フロー](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 この図には、3 つの異なるエンドポイント \(アプリケーション エンドポイント、ワークフロー コントロール エンドポイント、およびワークフローをホストするエンドポイント\) が示されています。アプリケーション エンドポイントは、特定のワークフロー インスタンスにバインドされたメッセージを受信します。ワークフロー コントロール エンドポイントは、制御操作をリッスンします。ワークフローをホストするエンドポイントは、<xref:System.ServiceModel.WorkflowServiceHost> がサービス以外のワークフローを読み込んで実行するためのメッセージをリッスンします。この図が示すように、すべてのメッセージは、WCF ランタイム中に処理されます。ワークフロー サービス インスタンスの調整は、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> プロパティを使用して実現されます。このプロパティは、同時ワークフロー サービス インスタンスの数を制限します。この調整を超過すると、新しいワークフロー サービス インスタンスの追加要求または永続化されたワークフロー インスタンスのアクティブ化の要求がキューに置かれます。キューに置かれた要求は、新規インスタンスと実行中の永続化されたインスタンスのどちらに対するものであるかにかかわらず、FIFO 順で処理されます。未処理の例外の処理方法およびアイドル状態のワークフロー サービスのアンロードおよび永続化方法を指定するホスト ポリシー情報が読み込まれます。これらのトピック[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー サービスの未処理の例外動作を構成する方法](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)」および「[WorkflowServiceHost を使用してアイドル動作を構成する方法](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md)」を参照してください。ワークフロー インスタンスは、ホスト ポリシーに従って永続化され、必要に応じて再度読み込まれます。ワークフロー永続化の詳細については、「[WorkflowServiceHost を使用して永続性を構成する方法](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md)」、「[長時間のワークフロー サービスの作成](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)」、および「[ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)」を参照してください。  
  
 次の図は、WorkflowServiceHost.Open が呼び出されたときの動作を示しています。  
  
 ![WorkflowServiceHost.Open が呼び出された場合の処理](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 ワークフローが XAML から読み込まれ、アクティビティ ツリーが作成されます。<xref:System.ServiceModel.WorkflowServiceHost> は、アクティビティ ツリーに従い、サービスの記述を作成します。構成がホストに適用されます。最後に、ホストは受信メッセージのリッスンを開始します。  
  
 次の図は、CanCreateInstance が `true` に設定された場合の Receive アクティビティにバインドされたメッセージを受信したときの <xref:System.ServiceModel.WorkflowServiceHost> の動作を示しています。  
  
 ![ワークフロー サービス ホストがメッセージを受信した場合の処理](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 メッセージが到着し、WCF チャネル スタックによって処理されます。スロットルがチェックされ、関連付けクエリが実行されます。既存のインスタンスにバインドされているメッセージは配信されます。新しいインスタンスを作成する必要がある場合は、Receive アクティビティの CanCreateInstance プロパティが確認されます。true に設定されている場合、新しいインスタンスが作成され、メッセージが配信されます。  
  
 次の図は、CanCreateInstance が false に設定された場合の Receive アクティビティにバインドされたメッセージを受信したときの <xref:System.ServiceModel.WorkflowServiceHost> の動作を示しています。  
  
 ![WorkflowServiceHost がメッセージを受信した場合の処理](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 メッセージが到着し、WCF チャネル スタックによって処理されます。スロットルがチェックされ、関連付けクエリが実行されます。メッセージが既存のインスタンスにバインドされている場合は \(CanCreateInstance が false に設定されているため\) インスタンスが永続ストアから読み込まれ、ブックマークが再開され、ワークフローが実行されます。  
  
> [!WARNING]
>  SQL Server が NamedPipe プロトコルでのみリッスンするように設定されている場合、ワークフロー サービス ホストは開きません。  
  
## 参照  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [ワークフロー サービスのホスティング](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)   
 [ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)   
 [ワークフロー管理エンドポイントのサンプル](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)   
 [ワークフロー サービスの未処理の例外動作を構成する方法](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)   
 [長時間のワークフロー サービスの作成](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)   
 [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation//workflow-persistence.md)