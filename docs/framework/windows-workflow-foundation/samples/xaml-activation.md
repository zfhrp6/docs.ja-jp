---
title: "XAML アクティベーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# XAML アクティベーション
このサンプルでは、宣言型ワークフローを IIS でホストする方法を示します。このサンプルは、1 つの操作を持つ、`EchoService` という名前の基本的なワークフローです。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で XAMLActivation.sln ソリューションを開きます。  
  
2.  **F5** キーを押して、ソリューションをビルドします。  
  
3.  WcfTestClient.exe を実行します。コマンド プロンプトで、次のコマンドを入力します。  
  
    1.  cd %SystemDrive%\\Program Files\\Microsoft Visual Studio 10.0\\Common7\\IDE  
  
    2.  WcfTestClient.exe を実行します。  
  
4.  WcfTestClient.exe でサービスのアドレスを設定します。これを行うには、Ctrl と Shift キーを押しながら A キーを押して、サービス アドレスを http:\/\/localhost:56133\/Service.xamlx に設定します。  
  
5.  エコー操作を実行してサービスをテストします。  
  
6.  管理特権を使用で、コマンド プロンプトの DeployToIIS.Bat を使用して、IIS でサービスを配置します。  
  
7.  クライアントでサービスのアドレスを http:\/\/localhost\/XAMLActivation\/Service.xamlx に更新し、WcfTestClient.exe を使用してサービスを再度テストします。