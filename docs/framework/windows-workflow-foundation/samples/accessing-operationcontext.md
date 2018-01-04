---
title: "OperationContext へのアクセス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ca0290f658dfc5e34ec7e1e1be228213c521ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-operationcontext"></a>OperationContext へのアクセス
このサンプルで示す方法、メッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive>と<xref:System.ServiceModel.Activities.Send>) にアクセスする、カスタムのスコープ アクティビティと共に使用できます<xref:System.ServiceModel.OperationContext.Current%2A>アタッチしたり、送信または受信メッセージ内のカスタム メッセージ ヘッダーを取得します。  
  
## <a name="demonstrates"></a>使用例  
 メッセージング アクティビティ、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。  
  
## <a name="discussion"></a>説明  
 このサンプルでは、メッセージング アクティビティで拡張ポイント (<xref:System.ServiceModel.Activities.ISendMessageCallback> および <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) を使用して <xref:System.ServiceModel.OperationContext.Current%2A> にアクセスする方法を示します。 これらのコールバックは、実行時にメッセージング アクティビティによって取得される <xref:System.Activities.IExecutionProperty> の実装としてワークフロー ランタイム内に登録されます。 その <xref:System.Activities.IExecutionProperty> 実装と同じスコープ内のメッセージング アクティビティはすべて影響を受けます。 具体的には、このサンプルでは、カスタムのスコープ アクティビティを使用してコールバック動作を適用します。 <xref:System.ServiceModel.Activities.ISendMessageCallback> は、ワークフローの <xref:System.Activities.WorkflowApplication.Id%2A> を送信 <xref:System.ServiceModel.Channels.MessageHeader> として含めるためにクライアント ワークフローで使用されます。 このヘッダーはサービスで <xref:System.ServiceModel.Activities.IReceiveMessageCallback> を使用して取得され、ヘッダーの値がコンソールに出力されます。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。 このサンプルを適切な URL Acl を実行するを追加する必要があります (を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細については)、管理者として Visual Studio を実行しているか、適切な Acl を追加する管理者特権のプロンプトで次のコマンドを実行することによってです。 ドメインとユーザー名は置き換えてください。  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  URL ACL を追加したら、次の手順を実行します。  
  
    1.  ソリューションをビルドします。  
  
    2.  複数のスタートアップ プロジェクトを設定するには、ソリューションを右クリックしを選択すると**スタートアップ プロジェクトの**します。  
  
    3.  追加**サービス**と**クライアント**(その順序で) 複数のスタートアップ プロジェクトとして。  
  
    4.  アプリケーションを実行します。 クライアント コンソールに実行中のワークフローが 2 回示され、[サービス] ウィンドウにこれらのワークフローのインスタンス ID が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
