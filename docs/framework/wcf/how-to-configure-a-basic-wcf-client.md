---
title: "方法 : 基本的な Windows Communication Foundation クライアントを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WCF クライアント [WCF], 構成"
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: 47
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 47
---
# 方法 : 基本的な Windows Communication Foundation クライアントを構成する
これは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうち、5 番目のタスクです。  6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
 ここでは、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] の "サービス参照の追加" 機能、または[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して生成されたクライアント構成ファイルについて説明します。  クライアントを構成するには、クライアントがサービスにアクセスするために使用するエンドポイントを指定します。  エンドポイントには、アドレス、バインディング、およびコントラクトがあり、クライアントを構成する過程でそれぞれを指定する必要があります。  
  
### Windows Communication Foundation クライアントを構成するには  
  
1.  GettingStartedClient プロジェクトから生成された構成ファイル \(App.config\) を開きます。  生成された構成ファイルを次の例に示します。  [\<system.serviceModel\>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)[\<endpoint\> セクション内に](http://msdn.microsoft.com/ja-jp/13aa23b7-2f08-4add-8dbf-a99f8127c017) 要素があるのがわかります。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration><?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     この例では、アドレス http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService に配置されたサービスにアクセスするために、クライアントが使用するエンドポイントを構成しています。  
  
     endpoint 要素は、`ServiceReference1.ICalculator` サービス コントラクトが、WCF クライアントと WCF サービス間の通信に使用されるように指定します。  WCF チャネルはシステム標準の <xref:System.ServiceModel.WsHttpBinding> で構成されます。  このコントラクトは、Visual Studio の "サービス参照の追加" を使用して生成されました。  基本的には、GettingStartedLib プロジェクトで定義されているコントラクトのコピーです。  <xref:System.ServiceModel.WsHttpBinding> バインディングは、トランスポートとして HTTP を指定し、相互運用可能なセキュリティ、およびその他の構成詳細を指定します。  
  
2.  この構成で生成されたクライアントを使用する方法[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[方法 : クライアントを使用する](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)」を参照してください。  
  
## 参照  
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [方法 : クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [概要](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)