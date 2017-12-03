---
title: "WCF サービスの簡略化された構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6f0d73ba01ec51fe2fcd00f33bbd3183e382c74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="simplified-configuration-for-wcf-services"></a>WCF サービスの簡略化された構成
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、一般的なサービスおよびクライアントを実装して構成する方法を示します。 このサンプルは、他のすべての基本的な技術サンプルの基礎になります。  
  
 このサービスは、サービスとの通信に使用する単一エンドポイントを公開しており、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] の簡略化された構成を使用しています。 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 以前は、次の構成コード例に示すように、エンドポイントは通常、構成ファイル (Web.config) で定義されています。  
  
```xml  
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
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、`<service>` 要素は省略可能です。 サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。 このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。 次のコード例は、簡略化された構成ファイルを示しています。 前の構成では、サービスと同じコンピューター上にあるクライアントは、http://localhost/servicemodelsamples/service.svc でサービスにアクセスできます。 リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。 既定では、サービスはメタデータを公開しません。 そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。  
  
```xml  
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
  
### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
3.  次の手順に従ってサンプルを実行します。  
  
    1.  右クリックして、**サービス**プロジェクトし、選択**スタートアップ プロジェクトとして設定**、キーを押します**ctrl キーを押しながら f5 キー**です。  
  
    2.  コンソール出力でサービスが動作していることが確認されるまで待機します。  
  
    3.  右クリックして、**クライアント**プロジェクトし、選択**スタートアップ プロジェクトとして設定**、キーを押します**ctrl キーを押しながら f5 キー**です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric 管理のサンプル](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)
