---
title: "WCF サービスの簡略化された構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# WCF サービスの簡略化された構成
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、一般的なサービスおよびクライアントを実装して構成する方法を示します。このサンプルは、他のすべての基本的な技術サンプルの基礎になります。  
  
 このサービスは、サービスとの通信に使用する単一エンドポイントを公開しており、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] の簡略化された構成を使用しています。[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 以前は、次の構成コード例に示すように、エンドポイントは通常、構成ファイル \(Web.config\) で定義されています。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
  
```  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、`<service>` 要素は省略可能です。サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。次のコード例は、簡略化された構成ファイルを示しています。前の構成では、サービスと同じコンピューター上にあるクライアントは、http:\/\/localhost\/servicemodelsamples\/service.svc でサービスにアクセスできます。リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。既定では、サービスはメタデータを公開しません。そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
  
```  
  
### このサンプルを使用するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションをビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  次の手順に従ってサンプルを実行します。  
  
    1.  **Service** プロジェクトを右クリックして **\[スタートアップ プロジェクトに設定\]** をクリックし、**Ctrl** キーを押しながら F5 キーを押します。  
  
    2.  コンソール出力でサービスが動作していることが確認されるまで待機します。  
  
    3.  **Client** プロジェクトを右クリックして **\[スタートアップ プロジェクトに設定\]** をクリックし、**Ctrl** キーを押しながら F5 キーを押します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## 参照  
 [AppFabric の管理のサンプル](http://go.microsoft.com/fwlink/?LinkId=193960)   
 [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)