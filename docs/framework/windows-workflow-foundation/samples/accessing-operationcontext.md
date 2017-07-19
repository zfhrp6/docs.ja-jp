---
title: "OperationContext へのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# OperationContext へのアクセス
このサンプルでは、メッセージング アクティビティ \(<xref:System.ServiceModel.Activities.Receive> および <xref:System.ServiceModel.Activities.Send>\) を、カスタムのスコープ アクティビティと共に使用して <xref:System.ServiceModel.OperationContext.Current%2A> にアクセスし、送信メッセージまたは受信メッセージ内のカスタム メッセージ ヘッダーを追加または取得する方法を示します。  
  
## 使用例  
 メッセージング アクティビティ、<xref:System.ServiceModel.Activities.ISendMessageCallback>、<xref:System.ServiceModel.Activities.IReceiveMessageCallback>。  
  
## 説明  
 このサンプルでは、メッセージング アクティビティで拡張ポイント \(<xref:System.ServiceModel.Activities.ISendMessageCallback> および <xref:System.ServiceModel.Activities.IReceiveMessageCallback>\) を使用して <xref:System.ServiceModel.OperationContext.Current%2A> にアクセスする方法を示します。これらのコールバックは、実行時にメッセージング アクティビティによって取得される <xref:System.Activities.IExecutionProperty> の実装としてワークフロー ランタイム内に登録されます。その <xref:System.Activities.IExecutionProperty> 実装と同じスコープ内のメッセージング アクティビティはすべて影響を受けます。具体的には、このサンプルでは、カスタムのスコープ アクティビティを使用してコールバック動作を適用します。<xref:System.ServiceModel.Activities.ISendMessageCallback> は、ワークフローの <xref:System.Activities.WorkflowApplication.Id%2A> を送信 <xref:System.ServiceModel.Channels.MessageHeader> として含めるためにクライアント ワークフローで使用されます。このヘッダーはサービスで <xref:System.ServiceModel.Activities.IReceiveMessageCallback> を使用して取得され、ヘッダーの値がコンソールに出力されます。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  このサンプルでは、HTTP エンドポイントを使用してワークフロー サービスを公開します。このサンプルを実行するには、適切な URL ACL を追加する必要があります \(詳細については、「[HTTP および HTTPS の構成](http://go.microsoft.com/fwlink/?LinkId=70353)」を参照\)。適切な ACL を追加するには、Visual Studio を管理者として実行するか、権限のレベルが高いプロンプトで次のコマンドを実行します。ドメインとユーザー名は置き換えてください。  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  URL ACL を追加したら、次の手順を実行します。  
  
    1.  ソリューションをビルドします。  
  
    2.  ソリューションを右クリックし、**\[スタートアップ プロジェクトの設定\]** をクリックして、複数のスタートアップ プロジェクトを設定します。  
  
    3.  複数のスタートアップ プロジェクトとして **Service** および **Client** を \(この順序で\) 追加します。  
  
    4.  アプリケーションを実行します。クライアント コンソールに実行中のワークフローが 2 回示され、\[サービス\] ウィンドウにこれらのワークフローのインスタンス ID が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`