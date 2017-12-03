---
title: "ワークフロー管理エンドポイントのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 193620902d5bcc2b71f91a26518ab4b6560e6753
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-management-endpoint-sample"></a>ワークフロー管理エンドポイントのサンプル
このサンプルでは、ワークフロー コントロール エンドポイントを使用して、ローカルとリモートの両方でワークフローを作成および実行する方法を示します。 このサンプルでは、コントロール エンドポイントをホストし、そのコントロール エンドポイントを呼び出すクライアントを記述して、ワークフローのインスタンスを作成および実行する方法を示します。 このワークフローはサービスではありません。  
  
 サンプルのサービス側では、ワークフローが WorkflowServiceHost を使用してホストされており、クライアントが管理操作 (保留、開始など) を実行できるように WorkflowControlEndpoint が追加されています。 ワークフローを作成できるように、ユーザー定義 CreationEndpoint も追加されています。 次に、サービスは、中断状態のワークフローを開始するこれらのエンドポイントを使用して、ワークフローを再開します。 クライアントはクライアント コードから同じ操作を実行します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]これらのインターフェイスを参照してください、[ワークフロー コントロール エンドポイント](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)と[する方法: IIS でサービス以外のワークフローのホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を管理者権限で実行します。  
  
2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で ManagementEndpoint.sln ソリューションを開きます。  
  
3.  ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。  
  
4.  ManagementEndpoint.exe アプリケーションを起動します。  
  
5.  Client.exe アプリケーションを起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`