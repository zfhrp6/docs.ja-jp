---
title: "探索バインド要素のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af513015-85bf-417b-8729-1bdff77ff6d6
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 821f629a7f39869975af19c793fe26188a40d7d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-binding-element-sample"></a><span data-ttu-id="55ad7-102">探索バインド要素のサンプル</span><span class="sxs-lookup"><span data-stu-id="55ad7-102">Discovery Binding Element Sample</span></span>
<span data-ttu-id="55ad7-103">このサンプルでは、探索クライアント バインド要素を使用してサービスを探索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-103">This sample demonstrates how to use the discovery client binding element to discover a service.</span></span> <span data-ttu-id="55ad7-104">この機能を使用すると、開発者は、探索クライアント チャネルを既存のクライアント チャネル スタックに追加することにより、プログラミング モデルをきわめて直感的にすることができます。</span><span class="sxs-lookup"><span data-stu-id="55ad7-104">This feature enables developers to add a discovery client channel to their existing client channel stack, making the programming model very intuitive.</span></span> <span data-ttu-id="55ad7-105">関連付けられたチャネルが開いている場合、サービスのアドレスは探索を使用して解決されます。</span><span class="sxs-lookup"><span data-stu-id="55ad7-105">When the associated channel is opened, the address of the service is resolved using discovery.</span></span> <span data-ttu-id="55ad7-106">このサンプルは、次のプロジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="55ad7-106">This sample consists of the following projects:</span></span>  
  
-   <span data-ttu-id="55ad7-107">**CalculatorService**: 探索可能な[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービス。</span><span class="sxs-lookup"><span data-stu-id="55ad7-107">**CalculatorService**: A discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
-   <span data-ttu-id="55ad7-108">**CalculatorClient**: A[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]の検索し、呼び出し、CalculatorService を探索クライアント チャネルを使用するクライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="55ad7-108">**CalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery client channel to search for and call the CalculatorService.</span></span>  
  
-   <span data-ttu-id="55ad7-109">**DynamicCalculatorClient**: A[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を検索し、CalculatorService を呼び出して、動的エンドポイントを使用するクライアント アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="55ad7-109">**DynamicCalculatorClient**: A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses a dynamic endpoint to search for and call the CalculatorService.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55ad7-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="55ad7-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55ad7-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="55ad7-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55ad7-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="55ad7-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55ad7-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="55ad7-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryBindingElement`  
  
## <a name="calculatorservice"></a><span data-ttu-id="55ad7-114">CalculatorService</span><span class="sxs-lookup"><span data-stu-id="55ad7-114">CalculatorService</span></span>  
 <span data-ttu-id="55ad7-115">このプロジェクトには、`ICalculatorService` コントラクトを実装する簡単な電卓サービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55ad7-115">This project contains a simple calculator service that implements the `ICalculatorService` contract.</span></span>  
  
 <span data-ttu-id="55ad7-116">次の App.config ファイルは、サービスの動作と探索エンドポイントに `<serviceDiscovery>` 動作を追加するために使用されています。</span><span class="sxs-lookup"><span data-stu-id="55ad7-116">The following App.config file is used to add a `<serviceDiscovery>` behavior in the service behaviors as well as the discovery endpoint.</span></span>  
  
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
  
 <span data-ttu-id="55ad7-117">これにより、サービスとそのエンドポイントが探索可能になります。</span><span class="sxs-lookup"><span data-stu-id="55ad7-117">This makes the service and its endpoints discoverable.</span></span> <span data-ttu-id="55ad7-118">CalculatorService は、NetTcpBinding バインディングを使用してエンドポイントを 1 つ追加する、自己ホスト型サービスです。</span><span class="sxs-lookup"><span data-stu-id="55ad7-118">The CalculatorService is a self-hosted service that adds one endpoint using the NetTcpBinding binding.</span></span> <span data-ttu-id="55ad7-119">また、次のコードに示すように、`EndpointDiscoveryBehavior` のエンドポイントへの追加と、スコープの指定も行います。</span><span class="sxs-lookup"><span data-stu-id="55ad7-119">It also adds an `EndpointDiscoveryBehavior` to the endpoint and specifies a scope as shown in the following code.</span></span>  
  
```  
// Add a NET.TCP endpoint and add a scope to that endpoint.  
ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), netTcpAddress);  
EndpointDiscoveryBehavior netTctEndpointBehavior = new EndpointDiscoveryBehavior();  
netTctEndpointBehavior.Scopes.Add(new Uri("ldap:///ou=engineering,o=exampleorg,c=us"));  
netTcpEndpoint.Behaviors.Add(netTctEndpointBehavior);  
serviceHost.Open();  
```  
  
## <a name="calculatorclient"></a><span data-ttu-id="55ad7-120">CalculatorClient</span><span class="sxs-lookup"><span data-stu-id="55ad7-120">CalculatorClient</span></span>  
 <span data-ttu-id="55ad7-121">このプロジェクトには、メッセージを CalculatorService に送信するクライアント実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="55ad7-121">This project contains a client implementation that sends messages to the CalculatorService.</span></span> <span data-ttu-id="55ad7-122">このプログラムは、`CreateCustomBindingWithDiscoveryElement()` メソッドを使用して、探索クライアント チャネルを使用するカスタム バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-122">This program uses the `CreateCustomBindingWithDiscoveryElement()` method to create a custom binding that uses the Discovery Client Channel.</span></span>  
  
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
  
 <span data-ttu-id="55ad7-123"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> をインスタンス化した後、サービスの検索時に使用する条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-123">After the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is instantiated, the developer specifies the criteria to use when searching for a service.</span></span> <span data-ttu-id="55ad7-124">この場合の探索検索条件は `ICalculatorService` 型です。</span><span class="sxs-lookup"><span data-stu-id="55ad7-124">In this case, the discovery find criterion is the `ICalculatorService` type.</span></span> <span data-ttu-id="55ad7-125">さらに、<xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> を指定します。これにより、サービスの検索場所を示す <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> が返されます。</span><span class="sxs-lookup"><span data-stu-id="55ad7-125">Additionally, the developer specifies a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> which returns a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> that specifies where to look for the services.</span></span> <span data-ttu-id="55ad7-126"><xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> は、新しい <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-126">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> returns a new <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="55ad7-127">[探索クライアント チャネルで、カスタム バインディングを使用して](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md)です。</span><span class="sxs-lookup"><span data-stu-id="55ad7-127"> [Using a Custom Binding with the Discovery Client Channel](../../../../docs/framework/wcf/feature-details/using-a-custom-binding-with-the-discovery-client-channel.md).</span></span>  
  
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
  
 <span data-ttu-id="55ad7-128">この場合、クライアントは、探索プロトコルによって定義された UDP マルチキャスト メカニズムを使用して、ローカル サブネット上のサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-128">In this case, the client uses the UDP multicast mechanism defined by the Discovery protocol to search for services on the local subnet.</span></span> <span data-ttu-id="55ad7-129">残りのメソッドは、カスタム バインディングを作成し、探索バインディング要素をスタックの一番上に挿入します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-129">The remainder of the method creates a custom binding and inserts the Discovery binding element at the top of the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ad7-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> は、バインディング スタックの一番上に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ad7-130">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must be placed on the top of the binding stack.</span></span> <span data-ttu-id="55ad7-131"><xref:System.ServiceModel.Channels.BindingElement> の一番上に配置された <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> によって作成されたチャネル ファクトリまたはチャネルでは、`EndpointAddress` プロパティまたは `Via` プロパティを使用しないようにする必要があります。これは、実際のアドレスが探索クライアント チャネルでしか見つからないからです。</span><span class="sxs-lookup"><span data-stu-id="55ad7-131">Any <xref:System.ServiceModel.Channels.BindingElement> on top of <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the channel factory or channel it creates does not use the `EndpointAddress` or `Via` properties, because the actual address is found only at the Discovery client channel.</span></span>  
  
 <span data-ttu-id="55ad7-132">次に、`CalculatorClient` をインスタンス化するために、このカスタム バインディングとエンドポイント アドレスを渡します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-132">Next, the `CalculatorClient` can be instantiated by passing in this custom binding as well as an endpoint address.</span></span>  
  
```  
CalculatorServiceClient client = new CalculatorServiceClient(CreateCustomBindingWithDiscoveryElement(), DiscoveryClientBindingElement.DiscoveryEndpointAddress);  
```  
  
 <span data-ttu-id="55ad7-133">探索クライアント チャネルを使用している場合、以前に指定された定数のエンドポイント アドレスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="55ad7-133">When using the Discovery Client Channel, the constant endpoint address specified previously is passed in.</span></span> <span data-ttu-id="55ad7-134">実行時には、探索クライアント チャネルは、検索条件で指定されたサービスを検索し、見つかったサービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-134">Now at runtime, the Discovery Client Channel finds the service specified by the find criteria and connects to it.</span></span> <span data-ttu-id="55ad7-135">サービスとクライアントの接続を確立するには、基になるバインディング スタックも同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55ad7-135">For the service and the client to establish a connection, they must also have the same underlying binding stack.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="55ad7-136">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="55ad7-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="55ad7-137">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="55ad7-137">Open the solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="55ad7-138">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="55ad7-138">Build the solution.</span></span>  
  
3.  <span data-ttu-id="55ad7-139">サービス アプリケーションと各クライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-139">Run the service application and each of the client applications.</span></span>  
  
4.  <span data-ttu-id="55ad7-140">クライアントがサービスのアドレスを知ることなくサービスを検索できたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="55ad7-140">Observe that the client was able to find the service without knowing its address.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ad7-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="55ad7-141">See Also</span></span>
