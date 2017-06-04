---
title: "非同期検索のサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 非同期検索のサンプル
このサンプルでは、クライアント アプリケーションで非同期の検索操作を使用する方法を示します。  
  
## サンプルの詳細  
 次のデザイン パターンの利点は、検索要求の結果として配置されたエンドポイントがクライアントに対して非同期に通知されることです。このしくみを確認するには、Client.cs ファイルを開いてください。<xref:System.ServiceModel.Discovery.DiscoveryClient> オブジェクトには、そのイベント ハンドラーにアタッチされるデリゲートが 2 つあることに注意してください。1 つは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベントの発生時に呼び出され、もう 1 つは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントが発生するたびに呼び出されます。このサンプルでは、アプリケーションでこのパターンを使用する方法について説明します。  
  
> [!NOTE]
>  このサンプルでは HTTP エンドポイントを使用します。サンプルを実行するには、適切な URL ACL を追加する必要があります。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HTTP および HTTPS の構成](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).管理特権で次のコマンドを実行すると、適切な ACL が追加されます。そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、AsyncFind.sln を開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、\\WCF\\Basic\\Discovery\\AsyncFind\\CS\\service\\bin\\Debug ディレクトリまたは \\WCF\\Basic\\Discovery\\AsyncFind\\VB\\service\\bin\\Debug ディレクトリに移動して、Service.exe を実行します。  
  
4.  サービスが開始したら、\\WCF\\Basic\\Discovery\\AsyncFind\\CS\\client\\bin\\Debug ディレクトリまたは WCF\\Basic\\Discovery\\AsyncFind\\VB\\client\\bin\\Debug ディレクトリに移動して、Client.exe を実行します。  
  
5.  クライアントでサービスを検索して呼び出せることを確認します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## 参照