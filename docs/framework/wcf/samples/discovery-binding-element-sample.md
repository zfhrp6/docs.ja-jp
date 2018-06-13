---
title: 探索バインド要素のサンプル
ms.date: 03/30/2017
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
ms.openlocfilehash: 853f5cebfd745b3413d605dcfbf0e395e103b4f1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805669"
---
# <a name="discovery-binding-element-sample"></a>探索バインド要素のサンプル
このサンプルでは、探索クライアント バインド要素を使用してサービスを探索する方法を示します。 この機能を使用すると、開発者は、探索クライアント チャネルを既存のクライアント チャネル スタックに追加することにより、プログラミング モデルをきわめて直感的にすることができます。 関連付けられたチャネルが開いている場合、サービスのアドレスは探索を使用して解決されます。 このサンプルは、次のプロジェクトで構成されています。  
  
-   **CalculatorService**: 探索可能な WCF サービスです。  
  
-   **CalculatorClient**: を検索し、CalculatorService を呼び出して、探索クライアント チャネルを使用する WCF クライアント アプリケーション。  
  
-   **DynamicCalculatorClient**: を検索し、CalculatorService を呼び出す動的エンドポイントを使用する WCF クライアント アプリケーション。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a>CalculatorService  
 このプロジェクトには、`ICalculatorService` コントラクトを実装する簡単な電卓サービスが含まれています。  
  
 次の App.config ファイルは、サービスの動作と探索エンドポイントに `<serviceDiscovery>` 動作を追加するために使用されています。  
  
```xml  
<system.serviceModel>  
    <services>  
      <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">  
        <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <!--Enable discovery through configuration.-->  
      <serviceBehaviors>  
        <behavior name="CalculatorBehavior">  
          <serviceDiscovery>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 これにより、サービスとそのエンドポイントが探索可能になります。 CalculatorService は、NetTcpBinding バインディングを使用してエンドポイントを 1 つ追加する、自己ホスト型サービスです。 また、次のコードに示すように、`EndpointDiscoveryBehavior` のエンドポイントへの追加と、スコープの指定も行います。  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a>CalculatorClient  
 このプロジェクトには、メッセージを CalculatorService に送信するクライアント実装が含まれています。 このプログラムは、`CreateCustomBindingWithDiscoveryElement()` メソッドを使用して、探索クライアント チャネルを使用するカスタム バインディングを作成します。  
  
```  
static CustomBinding CreateCustomBindingWithDiscoveryElement()  
 {  
      DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
            // Provide the search criteria and the endpoint over which the probe is sent  
            discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
            discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
            CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
            // Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
            // An exception is thrown if this binding element is not at the top  
            customBinding.Elements.Insert(0, discoveryBindingElement);  
  
            return customBinding; }  
```  
  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> をインスタンス化した後、サービスの検索時に使用する条件を指定します。 この場合の探索検索条件は `ICalculatorService` 型です。 さらに、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> を指定します。これにより、サービスの検索場所を示す <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> が返されます。 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> は、新しい <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> インスタンスを返します。 詳細については、次を参照してください。[探索クライアント チャネルでのカスタム バインドの使用](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md)です。  
  
```  
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
    // to the DiscoveryClientBindingElement. The Discovery ClientChannel   
    // uses this endpoint to send Probe message.  
    public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
    {  
        public override DiscoveryEndpoint GetDiscoveryEndpoint()  
        {  
            return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
        }  
    }  
```  
  
 この場合、クライアントは、探索プロトコルによって定義された UDP マルチキャスト メカニズムを使用して、ローカル サブネット上のサービスを検索します。 残りのメソッドは、カスタム バインディングを作成し、探索バインディング要素をスタックの一番上に挿入します。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> は、バインディング スタックの一番上に配置する必要があります。 <xref:System.ServiceModel.Channels.BindingElement> の一番上に配置された <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> によって作成されたチャネル ファクトリまたはチャネルでは、`EndpointAddress` プロパティまたは `Via` プロパティを使用しないようにする必要があります。これは、実際のアドレスが探索クライアント チャネルでしか見つからないからです。  
  
 次に、`CalculatorClient` をインスタンス化するために、このカスタム バインディングとエンドポイント アドレスを渡します。  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 探索クライアント チャネルを使用している場合、以前に指定された定数のエンドポイント アドレスが渡されます。 実行時には、探索クライアント チャネルは、検索条件で指定されたサービスを検索し、見つかったサービスに接続します。 サービスとクライアントの接続を確立するには、基になるバインディング スタックも同じにする必要があります。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、ソリューションを開きます。  
  
2.  ソリューションをビルドします。  
  
3.  サービス アプリケーションと各クライアント アプリケーションを実行します。  
  
4.  クライアントがサービスのアドレスを知ることなくサービスを検索できたことを確認します。  
  
## <a name="see-also"></a>関連項目
