---
title: '方法 : 基本的な Windows Communication Foundation クライアントを構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: c03bf37c737a19b0a90f12e7ad5db78b75323f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499276"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>方法 : 基本的な Windows Communication Foundation クライアントを構成する
これは、5 番目の基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 6 つのタスクです。 タスクの 6 つのすべての概要については、次を参照してください。、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)トピックです。  
  
 このトピックのサービス参照の追加機能を使用して生成されたクライアント構成ファイル[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]または[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。 クライアントを構成するには、クライアントがサービスにアクセスするために使用するエンドポイントを指定します。 エンドポイントには、アドレス、バインディング、およびコントラクトがあり、クライアントを構成する過程でそれぞれを指定する必要があります。  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>Windows Communication Foundation クライアントを構成するには  
  
1.  GettingStartedClient プロジェクトから生成された構成ファイル (App.config) を開きます。 生成された構成ファイルを次の例に示します。 [\<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションの下にある [\<endpoint >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素を見つけてください。  
  
    ```xml  
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
    </configuration>   
    ```  
  
     この例は、次のアドレス位置にあるサービスにアクセスするクライアントが使用するエンドポイントを構成します。 http://localhost:8000/ServiceModelSamples/Service/CalculatorService  
  
     endpoint 要素は、`ServiceReference1.ICalculator` サービス コントラクトが、WCF クライアントと WCF サービス間の通信に使用されるように指定します。 WCF チャネルは、システム指定の構成 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>。 このコントラクトは、Visual Studio の "サービス参照の追加" を使用して生成されました。 基本的には、GettingStartedLib プロジェクトで定義されているコントラクトのコピーです。 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> バインディングでは、トランスポート、相互運用可能なセキュリティ、およびその他の構成の詳細として HTTP を指定します。  
  
2.  この構成では、生成されたクライアントを使用する方法の詳細については、次を参照してください。[する方法: クライアントを使用して](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)です。  
  
## <a name="see-also"></a>関連項目  
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [はじめに](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
