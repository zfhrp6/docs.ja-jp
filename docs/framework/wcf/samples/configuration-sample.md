---
title: "構成サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c73fd8501d5209a87564caa810997476357f3e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-sample"></a><span data-ttu-id="5fe32-102">構成サンプル</span><span class="sxs-lookup"><span data-stu-id="5fe32-102">Configuration Sample</span></span>
<span data-ttu-id="5fe32-103">このサンプルでは、構成ファイルを使用してサービスを探索可能にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fe32-104">このサンプルでは、探索を構成ファイルで実装しています。</span><span class="sxs-lookup"><span data-stu-id="5fe32-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="5fe32-105">コードでの検出を実装するサンプルについては、次を参照してください。[基本](../../../../docs/framework/wcf/samples/basic-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fe32-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fe32-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5fe32-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5fe32-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5fe32-108">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="5fe32-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5fe32-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="5fe32-110">サービス構成</span><span class="sxs-lookup"><span data-stu-id="5fe32-110">Service Configuration</span></span>  
 <span data-ttu-id="5fe32-111">このサンプルの構成ファイルでは、次の 2 つの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-111">The configuration file in this sample demonstrates two features:</span></span>  
  
-   <span data-ttu-id="5fe32-112">標準の <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を介してサービスを探索できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5fe32-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
-   <span data-ttu-id="5fe32-113">サービスのアプリケーション エンドポイントに対する探索関連の情報を調整し、標準エンドポイントに対する探索関連の設定を調整します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="5fe32-114">探索を有効にするには、サービスのアプリケーション構成ファイルで次の変更を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
-   <span data-ttu-id="5fe32-115">探索エンドポイントを `<service>` 要素に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="5fe32-116">これは標準の <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="5fe32-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="5fe32-117">このエンドポイントが、ランタイムによって探索サービスに関連付けられるシステム エンドポイントになります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="5fe32-118">探索サービスは、このエンドポイント上でメッセージをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="5fe32-118">The discovery service listens for messages on this endpoint.</span></span>  
  
-   <span data-ttu-id="5fe32-119">`<serviceDiscovery>` 動作を `<serviceBehaviors>` セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="5fe32-120">これにより、サービスが実行時に探索されるようになり、前述の探索エンドポイントを使用して探索の `Probe` メッセージおよび `Resolve` メッセージをリッスンするようになります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="5fe32-121">この 2 つの追加により、指定した探索エンドポイントでサービスが探索可能になります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="5fe32-122">次の構成スニペットでは、アプリケーション エンドポイントのサービスと定義された探索エンドポイントが示されています。</span><span class="sxs-lookup"><span data-stu-id="5fe32-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="5fe32-123">アナウンスを活用するために、アナウンス エンドポイントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="5fe32-124">これを実行するために、次のコードに示すように構成ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="5fe32-125">アナウンス エンドポイントを探索サービス動作に追加することにより、サービスの既定のアナウンス クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="5fe32-126">これによって、サービスは、サービスが開いたときおよび閉じたときにそれぞれオンラインおよびオフラインのアナウンスを送信することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="5fe32-127">この構成ファイルは、さらに動作を変更することによって、より高度な機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="5fe32-128">特定のエンドポイントを使用することで、探索関連の情報を制御できます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="5fe32-129">つまり、ユーザーは、エンドポイントを探索できるかどうかを制御できるだけでなく、そのエンドポイントを <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> およびカスタム XML メタデータでマークすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="5fe32-130">これを行うには、`behaviorConfiguration` プロパティをアプリケーション エンドポイントに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="5fe32-131">この場合、次のプロパティをアプリケーション エンドポイントに追加します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="5fe32-132">これで、この動作構成要素を通じて、探索関連の属性を制御できます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="5fe32-133">この場合、2 つのスコープがアプリケーション エンドポイントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5fe32-134">スコープを参照してください[探索の検索と FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fe32-134"> scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="5fe32-135">探索エンドポイントに固有の詳細を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="5fe32-136">この制御には <xref:System.ServiceModel.Configuration.StandardEndpointsSection> を使用します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="5fe32-137">このサンプルでは、次のコード例に示すように、使用するプロトコルのバージョンを変更し、`maxResponseDelay` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="5fe32-138">この例で使用されている構成ファイルの全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="5fe32-139">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="5fe32-139">Client Configuration</span></span>  
 <span data-ttu-id="5fe32-140">クライアントのアプリケーション構成ファイルでは、`standardEndpoint` 型の `dynamicEndpoint` を使用して次の構成スニペットに示すように探索を利用します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="5fe32-141">クライアントで `dynamicEndpoint` を使用する場合、探索は自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="5fe32-142">探索時にはさまざまな設定が使用されます。たとえば、使用する探索エンドポイントの型を指定する、`discoveryClientSettings` セクションで定義される設定などがあります。</span><span class="sxs-lookup"><span data-stu-id="5fe32-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="5fe32-143">サービスの検索に使用する検索基準。</span><span class="sxs-lookup"><span data-stu-id="5fe32-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="5fe32-144">このサンプルでは、この機能を拡張し、クライアントで使用される <xref:System.ServiceModel.Discovery.FindCriteria>、および探索に使用される標準の `updDiscoveryEndpoint` の一部のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="5fe32-145"><xref:System.ServiceModel.Discovery.FindCriteria> は、スコープと特定の `scopeMatchBy` アルゴリズム、およびカスタムの終了条件を使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="5fe32-146">さらに、このサンプルでは、クライアントで `Probe` メッセージを使用して XML 要素を送信する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="5fe32-147">最後に、次の構成ファイルに示すように、使用するプロトコルのバージョンや UDP 固有の設定など、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> の変更をいくつか行います。</span><span class="sxs-lookup"><span data-stu-id="5fe32-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="5fe32-148">サンプルで使用されているクライアント構成の全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5fe32-149">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="5fe32-149">To use this sample</span></span>  
  
1.  <span data-ttu-id="5fe32-150">このサンプルは、HTTP エンドポイントを使用して、このサンプルを適切な URL Acl を実行する必要があります追加を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="5fe32-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="5fe32-151">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="5fe32-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="5fe32-152">そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="5fe32-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="5fe32-153">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="5fe32-153">Build the solution.</span></span>  
  
3.  <span data-ttu-id="5fe32-154">ビルド ディレクトリからサービス実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-154">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="5fe32-155">クライアント実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="5fe32-155">Run the client executable.</span></span> <span data-ttu-id="5fe32-156">クライアントでサービスを検索できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5fe32-156">Note that the client is able to locate the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe32-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fe32-157">See Also</span></span>
