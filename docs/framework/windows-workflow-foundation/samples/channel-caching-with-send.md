---
title: "Send によるチャネル キャッシュ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Send によるチャネル キャッシュ
<xref:System.ServiceModel.Activities.SendMessageChannelCache> を使用すると、ユーザーは <xref:System.ServiceModel.Activities.Send> および <xref:System.ServiceModel.Activities.SendParametersContent> アクティビティでさまざまなレベルのチャネル キャッシュを利用できます。既定では、インスタンス レベルのキャッシュが有効になっています。このサンプルでは、次の機能を示します。  
  
1.  アプリケーション ドメイン間での <xref:System.ServiceModel.Activities.SendMessageChannelCache> の共有。  
  
2.  チャネル キャッシュの無効化。  
  
3.  <xref:System.ServiceModel.Activities.WorkflowServiceHost> 内のワークフロー インスタンス間での <xref:System.ServiceModel.Activities.SendMessageChannelCache> の共有。  
  
## 使用例  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 拡張、<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.ReceiveContent>、および <xref:System.ServiceModel.Activities.SendReply> アクティビティ。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。  
  
2.  \\EchoWorkflowService\\bin\\debug に生成された EchoWorkflowService アプリケーションを実行します。  
  
3.  \\EchoWorkflowClient\\bin\\debug に生成された EchoWorkflowClient アプリケーションを実行します。\\EchoWorkflowClient\\bin\\debug  
  
4.  クライアントは、サービスで Echo 操作を呼び出し、結果を出力します。結果が出力されたら、Enter キーを押してクライアントを終了し、サービスを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`