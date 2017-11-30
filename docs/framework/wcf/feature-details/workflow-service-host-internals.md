---
title: "ワークフロー サービス ホストの内部"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d41ff3e83b6517194c34dec5f7f768299f612bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="workflow-service-host-internals"></a>ワークフロー サービス ホストの内部
<xref:System.ServiceModel.WorkflowServiceHost> では、ワークフロー サービスのホストが提供されます。 これにより、受信メッセージをリッスンして、該当するワークフロー サービス インスタンスにルーティングし、アイドル状態のワークフローのアンロードおよび永続化を制御できます。 このトピックでは、WorkflowServiceHost がどのように受信メッセージを処理するかについて説明します。  
  
## <a name="workflowservicehost-overview"></a>WorkflowServiceHost の概要  
 <xref:System.ServiceModel.WorkflowServiceHost> クラスは、ワークフロー サービスをホストするために使用されます。 このクラスは、受信メッセージをリッスンして、該当するサービス インスタンスにルーティングし、必要に応じて、新しいインスタンスを作成するか、永続ストレージから既存のインスタンスを読み込みます。  次の図は、<xref:System.ServiceModel.WorkflowServiceHost> の動作の概要を示しています。  
  
 ![WorkflowServiceHost の概要](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 この図では、<xref:System.ServiceModel.WorkflowServiceHost> は .xamlx ファイルからワークフロー サービス定義を読み込み、構成ファイルから構成情報を読み込みます。 また、追跡プロファイルから追跡構成を読み込みます。 <xref:System.ServiceModel.WorkflowServiceHost> によって、ワークフロー インスタンスへの制御操作の送信を可能にするワークフロー コントロール エンドポイントが公開されます。  詳細については、次を参照してください。[ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)と[ワークフロー管理エンドポイントのサンプル](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)です。  
  
 <xref:System.ServiceModel.WorkflowServiceHost> によって、受信アプリケーション メッセージをリッスンするアプリケーション エンドポイントも公開されます。 受信メッセージが到着すると、該当するワークフロー サービス インスタンスに送られます (現在読み込み中の場合)。 必要に応じて、新しいワークフロー インスタンスが作成されます。 既存のインスタンスが永続化されている場合は、永続ストアから読み込まれます。  
  
## <a name="workflowservicehost-details"></a>WorkflowServiceHost の詳細  
 次の図は、<xref:System.ServiceModel.WorkflowServiceHost> がメッセージを処理する方法をさらに詳細に示しています。  
  
 ![ワークフロー サービス ホストのメッセージ フロー](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 この図には、3 つの異なるエンドポイント (アプリケーション エンドポイント、ワークフロー コントロール エンドポイント、およびワークフローをホストするエンドポイント) が示されています。 アプリケーション エンドポイントは、特定のワークフロー インスタンスにバインドされたメッセージを受信します。 ワークフロー コントロール エンドポイントは、制御操作をリッスンします。 ワークフローをホストするエンドポイントは、<xref:System.ServiceModel.WorkflowServiceHost> がサービス以外のワークフローを読み込んで実行するためのメッセージをリッスンします。 この図が示すように、すべてのメッセージは、WCF ランタイム中に処理されます。  ワークフロー サービス インスタンスの調整は、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> プロパティを使用して実現されます。 このプロパティは、同時ワークフロー サービス インスタンスの数を制限します。 この調整を超過すると、新しいワークフロー サービス インスタンスの追加要求または永続化されたワークフロー インスタンスのアクティブ化の要求がキューに置かれます。 キューに置かれた要求は、新規インスタンスと実行中の永続化されたインスタンスのどちらに対するものであるかにかかわらず、FIFO 順で処理されます。 未処理の例外の処理方法およびアイドル状態のワークフロー サービスのアンロードおよび永続化方法を指定するホスト ポリシー情報が読み込まれます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]これらのトピックを参照してください[する方法: WorkflowServiceHost での例外動作の構成ワークフロー未処理](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)と[する方法: WorkflowServiceHost でのアイドル動作の構成](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md)です。 ワークフロー インスタンスは、ホスト ポリシーに従って永続化され、必要に応じて再度読み込まれます。 ワークフローの永続化の詳細については、次を参照してください:[する方法: WorkflowServiceHost で永続化を構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md)、[実行時間の長いワークフロー サービスを作成する](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)、および[ワークフローの永続化](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 次の図は、WorkflowServiceHost.Open が呼び出されたときの動作を示しています。  
  
 ![WorkflowServiceHost.Open が呼び出されたとき](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 ワークフローが XAML から読み込まれ、アクティビティ ツリーが作成されます。 <xref:System.ServiceModel.WorkflowServiceHost> は、アクティビティ ツリーに従い、サービスの記述を作成します。 構成がホストに適用されます。 最後に、ホストは受信メッセージのリッスンを開始します。  
  
 次の図は、CanCreateInstance が <xref:System.ServiceModel.WorkflowServiceHost> に設定された場合の Receive アクティビティにバインドされたメッセージを受信したときの `true` の動作を示しています。  
  
 ![ワークフロー サービス ホストがメッセージを受信](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 メッセージが到着し、WCF チャネル スタックによって処理されます。 スロットルがチェックされ、関連付けクエリが実行されます。 既存のインスタンスにバインドされているメッセージは配信されます。 新しいインスタンスを作成する必要がある場合は、Receive アクティビティの CanCreateInstance プロパティが確認されます。 true に設定されている場合、新しいインスタンスが作成され、メッセージが配信されます。  
  
 次の図は、CanCreateInstance が false に設定された場合の Receive アクティビティにバインドされたメッセージを受信したときの <xref:System.ServiceModel.WorkflowServiceHost> の動作を示しています。  
  
 ![WorkflowServiceHost がメッセージを受信した](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 メッセージが到着し、WCF チャネル スタックによって処理されます。 スロットルがチェックされ、関連付けクエリが実行されます。 メッセージが既存のインスタンスにバインドされている場合は (CanCreateInstance が false に設定されているため) インスタンスが永続ストアから読み込まれ、ブックマークが再開され、ワークフローが実行されます。  
  
> [!WARNING]
>  SQL Server が NamedPipe プロトコルでのみリッスンするように設定されている場合、ワークフロー サービス ホストは開きません。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー サービス](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [ワークフロー サービスのホスティング](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 [ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 [ワークフロー管理エンドポイントのサンプル](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)  
 [方法: ワークフローを構成する未処理の例外の動作を WorkflowServiceHost を使用](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
 [実行時間の長いワークフロー サービスを作成します。](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [ワークフローの永続性](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
