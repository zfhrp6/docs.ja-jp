---
title: 簡略化された構成
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 9f35a5f4fa4ae6be63bd75a24f58b56dd236ee9c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="simplified-configuration"></a><span data-ttu-id="a390b-102">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="a390b-102">Simplified Configuration</span></span>
<span data-ttu-id="a390b-103">Windows Communication Foundation (WCF) サービスを構成すると、複雑なタスクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a390b-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="a390b-104">さまざまなオプションがあり、どの設定が必要であるかをいつでも簡単に判断できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="a390b-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="a390b-105">構成ファイルは、WCF サービスの柔軟性を向上させ、それらもは発見しにくい問題の多くのソースです。</span><span class="sxs-lookup"><span data-stu-id="a390b-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="a390b-106"> では、このような問題に対応し、サービス構成の規模と複雑さを軽減する手段を提供しています。</span><span class="sxs-lookup"><span data-stu-id="a390b-106"> addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="a390b-107">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="a390b-107">Simplified Configuration</span></span>  
 <span data-ttu-id="a390b-108">WCF サービス構成ファイルで、<`system.serviceModel`> セクションが含まれています、<`service`> ホストされているサービスごとの要素。</span><span class="sxs-lookup"><span data-stu-id="a390b-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="a390b-109"><`service`> 要素には、各サービスに対して公開されるエンドポイントと、必要に応じて一連のサービス動作を指定する <`endpoint`> 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a390b-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="a390b-110"><`endpoint`> 要素は、エンドポイントが公開するアドレス、バインド、およびコントラクトと、必要に応じてバインド構成およびエンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="a390b-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="a390b-111"><`system.serviceModel`> セクションには、サービスまたはエンドポイントの動作を指定できる <`behaviors`> 要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a390b-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="a390b-112">構成ファイルの <`system.serviceModel`> セクションの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a390b-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="a390b-113"> 要件を削除することで簡単に WCF サービスを構成できるように、<`service`> 要素。</span><span class="sxs-lookup"><span data-stu-id="a390b-113"> makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="a390b-114"><`service`> セクションを追加したり、<`service`> セクションにエンドポイントを追加したりせず、サービスがプログラムを使用してエンドポイントを定義しない場合は、一連の既定のエンドポイントが自動的にサービスに追加されます。この場合、各サービスのベース アドレスに対して 1 つ、サービスによって実装される各コントラクトに対して 1 つのエンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="a390b-115">これらの各エンドポイントでは、エンドポイント アドレスがベース アドレスに対応し、バインドがベース アドレス スキームで決定されます。また、コントラクトは、サービスによって実装されるコントラクトになります。</span><span class="sxs-lookup"><span data-stu-id="a390b-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="a390b-116">エンドポイントまたはサービスの動作を指定する必要も、バインド設定を変更する必要もない場合、サービス構成ファイルを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a390b-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="a390b-117">サービスが 2 つのコントラクトを実装し、ホストが HTTP トランスポートと TCP トランスポートの両方を有効にしている場合、サービス ホストは、それぞれのトランスポートを使用する各コントラクトに対して 1 つずつ、合計 4 つの既定のエンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="a390b-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="a390b-118">既定のエンドポイントを作成するには、使用するバインドをサービス ホストに伝える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a390b-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="a390b-119">これらの設定は、<`protocolMappings`> セクション内の <`system.serviceModel`> セクションに指定します。</span><span class="sxs-lookup"><span data-stu-id="a390b-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="a390b-120"><`protocolMappings`> セクションには、バインドの型にマップされたトランスポート プロトコル スキームの一覧が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="a390b-121">サービス ホストは、渡されたベース アドレスを使用して、使用するバインドを決定します。</span><span class="sxs-lookup"><span data-stu-id="a390b-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="a390b-122">次の例では、<`protocolMappings`> 要素を使用しています。</span><span class="sxs-lookup"><span data-stu-id="a390b-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a390b-123">バインディングまたは動作のような既定の構成要素を変更すると、構成階層の下のレベルで定義されたサービスはこれらの既定のバインディングおよび動作を使用している可能性があるため、影響を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="a390b-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="a390b-124">したがって、既定のバインディングおよび動作を変更する場合は、これらの変更が階層の他のサービスに影響を与える可能性があることに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a390b-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a390b-125">インターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされるサービスは、仮想ディレクトリをベース アドレスとして使用します。</span><span class="sxs-lookup"><span data-stu-id="a390b-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="a390b-126">前の例では、"http" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.BasicHttpBinding> を使用します。</span><span class="sxs-lookup"><span data-stu-id="a390b-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="a390b-127">"net.tcp" スキームで始まるベース アドレスのエンドポイントは、<xref:System.ServiceModel.NetTcpBinding> を使用します。</span><span class="sxs-lookup"><span data-stu-id="a390b-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="a390b-128">ローカルの App.config または Web.config ファイルの設定はオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a390b-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="a390b-129"><`protocolMappings`> セクション内の各要素は、スキームとバインドを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a390b-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="a390b-130">必要に応じて、構成ファイルの <`bindingConfiguration`> セクション内で、バインド構成を指定する `bindings` 属性を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a390b-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="a390b-131">`bindingConfiguration` が指定されていない場合は、適切なバインド型の匿名バインド構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="a390b-132">既定のエンドポイントでは、<`behavior`> セクション内の匿名の <`serviceBehaviors`> セクションを使用して、サービスの動作が構成されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="a390b-133">サービスの動作の構成には、<`behavior`> 内の、名前が付けられていない <`serviceBehaviors`> 要素が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="a390b-134">たとえば、次の構成ファイルでは、ホスト内のすべてのサービスで、サービス メタデータの公開が有効になります。</span><span class="sxs-lookup"><span data-stu-id="a390b-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="a390b-135">エンドポイントの動作は、<`behavior`> セクション内の匿名の <`serviceBehaviors`> セクションを使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="a390b-136">以下は、このトピックの最初にある例と同じ内容ですが、簡略化された構成モデルを使用している構成ファイルの例です。</span><span class="sxs-lookup"><span data-stu-id="a390b-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="a390b-137">この機能は、WCF サービス構成にのみ適用され、クライアント構成には適用されません。</span><span class="sxs-lookup"><span data-stu-id="a390b-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="a390b-138">ほとんどの場合、WCF クライアント構成は、svcutil.exe などのツールを使用したり、Visual Studio からサービス参照を追加したりすることで生成されます。</span><span class="sxs-lookup"><span data-stu-id="a390b-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="a390b-139">WCF クライアントを手動で構成している場合は、追加する必要があります、\<クライアント > 要素を構成し、呼び出すエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="a390b-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a390b-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a390b-140">See Also</span></span>  
 [<span data-ttu-id="a390b-141">構成ファイルを使用してサービスを構成する方法</span><span class="sxs-lookup"><span data-stu-id="a390b-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="a390b-142">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="a390b-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="a390b-143">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="a390b-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a390b-144">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="a390b-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="a390b-145">Windows Communication Foundation アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="a390b-145">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="a390b-146">コード内での WCF サービスの構成</span><span class="sxs-lookup"><span data-stu-id="a390b-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
