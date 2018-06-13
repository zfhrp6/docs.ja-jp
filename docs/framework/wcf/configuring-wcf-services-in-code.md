---
title: コード内での WCF サービスの構成
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 714236bcdb562840323698622cdf3d0c6c89b6ca
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804148"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="5fd91-102">コード内での WCF サービスの構成</span><span class="sxs-lookup"><span data-stu-id="5fd91-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="5fd91-103">Windows Communication Foundation (WCF) では、構成ファイルまたはコードを使用してサービスの構成をすることができます。</span><span class="sxs-lookup"><span data-stu-id="5fd91-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="5fd91-104">構成ファイルは、サービスを配置した後に構成する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5fd91-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="5fd91-105">構成ファイルを使用する場合、IT 専門家は構成ファイルを更新するだけで、再コンパイルの必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5fd91-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="5fd91-106">ただし、構成ファイルの管理は複雑で難しくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5fd91-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="5fd91-107">構成ファイルのデバッグはサポートされていません。また、構成要素は名前で参照されるため、構成ファイルの作成時にエラーが発生しやすく、構成ファイルの作成が困難になります。</span><span class="sxs-lookup"><span data-stu-id="5fd91-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="5fd91-108">WCF では、コードでサービスを構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5fd91-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="5fd91-109">以前のバージョンのコードで WCF (4.0 およびそれ以前) 構成サービスが自己ホスト型では、簡単、<xref:System.ServiceModel.ServiceHost>クラスを使用するエンドポイントと、ServiceHost.Open を呼び出す前に動作を構成します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="5fd91-110">ただし、Web ホストのシナリオでは、<xref:System.ServiceModel.ServiceHost> クラスに直接アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="5fd91-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="5fd91-111">Web ホスト サービスを構成するには、`System.ServiceModel.ServiceHostFactory` を作成して必要な構成を実行する <xref:System.ServiceModel.Activation.ServiceHostFactory> を作成する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="5fd91-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="5fd91-112">.NET 4.5 以降で、WCF では、両方を構成する簡単な方法は自己ホスト型し、web ホスト サービスでコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="5fd91-113">Configure メソッド</span><span class="sxs-lookup"><span data-stu-id="5fd91-113">The Configure method</span></span>  
 <span data-ttu-id="5fd91-114">サービス実装クラスで、次のシグネチャを持つ `Configure` という名前のパブリックな静的メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="5fd91-115">Configure メソッドは、開発者がエンドポイントおよび動作を追加できるようにする <xref:System.ServiceModel.ServiceConfiguration> インスタンスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="5fd91-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="5fd91-116">このメソッドは、サービス ホストが開かれる前に、WCF によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5fd91-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="5fd91-117">app.config ファイルまたは web.config ファイルで指定されたすべてのサービスの構成設定は、定義されている場合、無視されます。</span><span class="sxs-lookup"><span data-stu-id="5fd91-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="5fd91-118">次のコード スニペットは、`Configure` メソッドを定義し、サービス エンドポイント、エンドポイントの動作、およびサービスの動作を追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5fd91-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return string.Format("You entered: {0}", value);  
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="5fd91-119">サービスで https などのプロトコルを有効にするには、プロトコルを使用するエンドポイントを明示的に追加するか、ServiceConfiguration.EnableProtocol(Binding) を呼び出すことによって自動的にエンドポイントを追加します。このメソッドは、プロトコルおよび定義された各サービス コントラクトと互換性がある各ベース アドレスのエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="5fd91-120">次のコードは、ServiceConfiguration.EnableProtocol メソッドを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5fd91-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="5fd91-121">設定、<`protocolMappings`> セクションをアプリケーション エンドポイントが追加されていない場合にのみ使用が、<xref:System.ServiceModel.ServiceConfiguration>プログラムでします。呼び出すことによって、既定のアプリケーション構成ファイルからサービスの構成を読み込むことができます必要に応じて<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>し、設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="5fd91-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> クラスを使って、集中化された構成から構成を読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="5fd91-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="5fd91-123">これを実装する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-123">The following code illustrates how to implement this:</span></span>  
  
```  
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="5fd91-124">なお<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>を無視 <`host`> 内の設定、<`service`> のタグ <`system.serviceModel`>。</span><span class="sxs-lookup"><span data-stu-id="5fd91-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="5fd91-125">概念的には、<`host`> は、ホストの構成、いないサービス構成、およびそのについて構成するメソッドが実行される前に読み込まれたを取得します。</span><span class="sxs-lookup"><span data-stu-id="5fd91-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fd91-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fd91-126">See Also</span></span>  
 [<span data-ttu-id="5fd91-127">構成ファイルを使用してサービスを構成する方法</span><span class="sxs-lookup"><span data-stu-id="5fd91-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="5fd91-128">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="5fd91-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="5fd91-129">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="5fd91-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="5fd91-130">構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="5fd91-130">Configuration-Based Activation</span></span>](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [<span data-ttu-id="5fd91-131">構成</span><span class="sxs-lookup"><span data-stu-id="5fd91-131">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="5fd91-132">IIS と WAS における構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="5fd91-132">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="5fd91-133">構成とメタデータのサポート</span><span class="sxs-lookup"><span data-stu-id="5fd91-133">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="5fd91-134">構成</span><span class="sxs-lookup"><span data-stu-id="5fd91-134">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [<span data-ttu-id="5fd91-135">方法: 構成でサービス バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="5fd91-135">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="5fd91-136">方法 : 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="5fd91-136">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="5fd91-137">方法 : 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="5fd91-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="5fd91-138">方法: 構成でクライアント バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="5fd91-138">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
