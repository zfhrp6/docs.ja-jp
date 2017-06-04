---
title: "ワークフロー管理エンドポイントのサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# ワークフロー管理エンドポイントのサンプル
このサンプルでは、ワークフロー コントロール エンドポイントを使用して、ローカルとリモートの両方でワークフローを作成および実行する方法を示します。このサンプルでは、コントロール エンドポイントをホストし、そのコントロール エンドポイントを呼び出すクライアントを記述して、ワークフローのインスタンスを作成および実行する方法を示します。このワークフローはサービスではありません。  
  
 サンプルのサービス側で、ワーク フローが WorkflowServiceHost を使用してホストされ、クライアントが管理操作 \(保留、開始など\) を実行できるように WorkflowControlEndpoint が追加されます。ワークフローの作成のため、ユーザー定義 CreationEndpoint も追加されます。次にサービスは中断状態のワーク フローを開始するこれらのエンドポイントを使用して、ワーク フローを再開します。クライアントはクライアント コードから同じ操作を実行します。これらのインターフェイスについては、[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)」および「[方法 : IIS でサービス以外のワークフローをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)」を参照してください。  
  
#### サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者権限で実行します。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ManagementEndpoint.sln ソリューションを開きます。  
  
3.  ソリューションをビルドするには、CTRL キーと SHIFT キーを押したまま B キーを押すか、**\[ビルド\]** メニューの **\[ソリューションのビルド\]** を選択します。  
  
4.  ManagementEndpoint.exe アプリケーションを起動します。  
  
5.  Client.exe アプリケーションを起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`  
  
## 参照