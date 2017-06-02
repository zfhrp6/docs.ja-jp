---
title: "構成チャネル ファクトリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 構成チャネル ファクトリ
このサンプルでは、<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> の使用方法を示します。<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> により、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント構成の集中管理が可能になります。これは、アプリケーション ドメインによる読み込みの後に構成が選択または変更される場合にも役立ちます。  
  
## 使用例  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## 説明  
 このサンプルでは、既定のアプリケーション構成ファイルを使用することなく、<xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> を使用して、クライアント アプリケーションに特定の構成ファイルを追加する方法を示します。  
  
 このサンプルは、2 つのプロジェクトで構成されます。最初のプロジェクトは、クライアントから送信されるメッセージに応答するために実行される単純なサービスです。2 番目のプロジェクトは、Test.config 構成ファイルの <xref:System.Configuration.ExeConfigurationFileMap> を使用して、2 つの <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> オブジェクトを作成し、サービスとの通信にそれらのオブジェクトを使用するクライアント アプリケーションです。どちらのクライアントも Test.config で指定された構成を使用してサービスと通信します。  
  
 次のコードでは、カスタム構成ファイルをクライアント アプリケーションに追加します。  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
  
```  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者権限で開きます。  
  
2.  ConfigurationChannelFactory ソリューション \(2 つのプロジェクト\) を右クリックし、**\[プロパティ\]** をクリックします。  
  
3.  **\[共通プロパティ\]** で、**\[スタートアップ プロジェクト\]** をクリックし、**\[マルチ スタートアップ プロジェクト\]** をクリックします。  
  
4.  **Service** プロジェクトを一覧の先頭に移動し、**\[アクション\]** を \[開始\] に設定します。次に、**Client** プロジェクトを **Service** プロジェクトの後ろに移動し、同様に **\[アクション\]** を \[開始\] に設定して、**Client** プロジェクトが **Service** プロジェクトの後に実行されるようにします。  
  
5.  **\[OK\]** をクリックし、F5 キーを押して \(または Ctrl キーを押しながら F5 キーを押して\) サンプルを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`