---
title: "標準エンドポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 755669b1305060efeb6af592867844b571b67020
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2017
---
# <a name="standard-endpoints"></a><span data-ttu-id="6e1d9-102">標準エンドポイント</span><span class="sxs-lookup"><span data-stu-id="6e1d9-102">Standard Endpoints</span></span>
<span data-ttu-id="6e1d9-103">エンドポイントは、アドレス、バインディング、およびコントラクトを指定して定義します。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="6e1d9-104">エンドポイントに設定できるその他のパラメーターには、動作構成、ヘッダー、リッスン URI などがあります。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="6e1d9-105">特定の種類のエンドポイントでは、これらの値が変化しません。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="6e1d9-106">たとえば、メタデータ交換エンドポイントでは、常に <xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="6e1d9-107"><xref:System.ServiceModel.Description.WebHttpEndpoint> などのその他のエンドポイントでは、指定されたエンドポイント動作が必要です。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="6e1d9-108">一般的に使用されるエンドポイント プロパティの既定の値を設定することによって、エンドポイントの操作性を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="6e1d9-109">開発者は、標準エンドポイントを使用して、既定値を持つエンドポイント、またはエンドポイントの 1 つ以上のプロパティが変化しないエンドポイントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="6e1d9-110">これらのエンドポイントによって、静的な性質の情報を指定する必要がないエンドポイントの使用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="6e1d9-111">標準エンドポイントは、インフラストラクチャ エンドポイントおよびアプリケーション エンドポイントに使用できます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="6e1d9-112">インフラストラクチャ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="6e1d9-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="6e1d9-113">サービスの作成者が明示的に実装していないいくつかのプロパティを持つエンドポイントを、サービスが公開することがあります。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="6e1d9-114">たとえば、メタデータ交換エンドポイントは <xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを公開しますが、そのインターフェイスを実装するのは、サービスの作成者ではなく、WCF です。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="6e1d9-115">このようなインフラストラクチャ エンドポイントには、1 つ以上のプロパティの既定値があり、そのいくつかは変更できません。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="6e1d9-116">メタデータ交換エンドポイントの <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> プロパティは <xref:System.ServiceModel.Description.IMetadataExchange> である必要がありますが、バインディングなど、その他のプロパティは開発者が提供できます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="6e1d9-117">インフラストラクチャ エンドポイントは、<xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> プロパティを `true` に設定することによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="6e1d9-118">アプリケーション エンドポイント</span><span class="sxs-lookup"><span data-stu-id="6e1d9-118">Application Endpoints</span></span>  
 <span data-ttu-id="6e1d9-119">アプリケーション開発者は独自の標準エンドポイントを定義でき、このエンドポイントでアドレス、バインディング、またはコントラクトの既定値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="6e1d9-120">標準エンドポイントを定義するには、<xref:System.ServiceModel.Description.ServiceEndpoint> からクラスを派生させ、適切なエンドポイント プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="6e1d9-121">変更可能な既定値をプロパティに設定できます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="6e1d9-122">他のいくつかのプロパティには、変更できない静的な値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="6e1d9-123">次の例は、標準エンドポイントの実装方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  
    
    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  
    
    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }
    
    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="6e1d9-124">ユーザー定義のカスタム エンドポイントを構成ファイルで使用するには、<xref:System.ServiceModel.Configuration.StandardEndpointElement> から 1 つのクラスを派生させ、<xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> から 1 つのクラスを派生させて、新しい標準エンドポイントを app.config または machine.config の拡張セクションに登録します。<xref:System.ServiceModel.Configuration.StandardEndpointElement> は、次の例に示すように、標準エンドポイントの構成サポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="6e1d9-125"><xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>バッキング型コレクションの提供、下に表示される、<`standardEndpoints`> 標準エンドポイントの構成」セクション。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="6e1d9-126">次の例は、このクラスを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="6e1d9-127">次の例は、拡張セクションで標準エンドポイントを登録する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="6e1d9-128">標準エンドポイントの構成</span><span class="sxs-lookup"><span data-stu-id="6e1d9-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="6e1d9-129">標準エンドポイントは、コードまたは構成で追加できます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="6e1d9-130">標準エンドポイントをコードで追加するには、次の例に示すように、適切な標準エンドポイントの種類をインスタンス化し、それをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="6e1d9-131">構成では、標準エンドポイントを追加するには、追加、<`endpoint`> 要素を <`service`> 要素との必要な構成設定で、<`standardEndpoints`> 要素。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="6e1d9-132">次の例は、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を追加する方法を示しています。これは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に付属する標準エンドポイントの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>    
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="6e1d9-133">種類の属性を使用する標準エンドポイントの種類が指定されて、<`endpoint`> 要素。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="6e1d9-134">内でエンドポイントが構成されている、<`standardEndpoints`> 要素。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="6e1d9-135">前の例では、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> エンドポイントが追加され、構成されます。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="6e1d9-136"><`udpDiscoveryEndpoint`> 要素が含まれています、<`standardEndpoint`> が設定された、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A>のプロパティ、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>です。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="6e1d9-137">.NET Framework に付属する標準エンドポイント</span><span class="sxs-lookup"><span data-stu-id="6e1d9-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="6e1d9-138">次の表は、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に付属する標準エンドポイントを示しています。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="6e1d9-139">サービス メタデータの公開に使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="6e1d9-140">サービスがアナウンス メッセージを送信するために使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="6e1d9-141">サービスが探索メッセージを送信するために使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="6e1d9-142">UDP マルチキャスト バインディング上での探索操作用に事前構成済みの標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="6e1d9-143">サービスが UDP バインディングでアナウンス メッセージを送信するために使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="6e1d9-144">実行時にエンドポイント アドレスを動的に検索するために WS-Discovery を使用する標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="6e1d9-145">メタデータ交換用の標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="6e1d9-146"><xref:System.ServiceModel.WebHttpBinding> の動作を自動的に追加する <xref:System.ServiceModel.Description.WebHttpBehavior> バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="6e1d9-147"><xref:System.ServiceModel.WebHttpBinding> の動作を自動的に追加する <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="6e1d9-148"><xref:System.ServiceModel.WebHttpBinding> バインディングを持つ標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="6e1d9-149">ワークフロー インスタンスで管理操作を呼び出すことができる標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="6e1d9-150">ワークフローの作成とブックマークの再開をサポートする標準エンドポイント。</span><span class="sxs-lookup"><span data-stu-id="6e1d9-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
