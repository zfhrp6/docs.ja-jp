---
title: "DiscoveryClient と DynamicEndpoint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6cd38a2fd0a682ebae0a32cc1fec31a3ac40851
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="a80cb-102">DiscoveryClient と DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="a80cb-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="a80cb-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> および <xref:System.ServiceModel.Discovery.DynamicEndpoint> の 2 つは、サービスの検索にクライアント側で使用されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="a80cb-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="a80cb-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> は、特定の条件に一致するサービスの一覧を表示し、サービスに接続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a80cb-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="a80cb-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> は同じ操作を実行するだけでなく、見つかったサービスの 1 つに自動的に接続します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="a80cb-106"><xref:System.ServiceModel.Discovery.DynamicEndpoint> には任意のエンドポイントを指定でき、構成に検索条件も追加できます。このため、ソリューションに探索機能が必要だが、クライアント ロジックを変更したくないという場合は、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を使用すると、エンドポイントを変更するだけで済み、便利です。</span><span class="sxs-lookup"><span data-stu-id="a80cb-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="a80cb-107">これに対して、<xref:System.ServiceModel.Discovery.DiscoveryClient> は、検索操作を詳細に制御する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="a80cb-108">次に、それぞれのクラスの用途と利点について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="a80cb-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="a80cb-109">DiscoveryClient</span></span>  
 <span data-ttu-id="a80cb-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> は、同期および非同期の Find メソッド、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベント、および <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="a80cb-111">さらに、同期および非同期の Resolve メソッド、および <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> イベントも定義します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="a80cb-112"><xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドまたは <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> メソッドを使用して、サービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="a80cb-113">これらのメソッドは両方とも <xref:System.ServiceModel.Discovery.FindCriteria> インスタンスを受け取ります。このインスタンスにより、コントラクト型名、スコープ、要求した結果の最大数、およびスコープ一致規則の指定が可能になります。</span><span class="sxs-lookup"><span data-stu-id="a80cb-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="a80cb-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> メソッドを呼び出す際には、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> イベントおよび <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> イベントが使用できます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="a80cb-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> がサービスからの応答を受け取るたびに、<xref:System.ServiceModel.Discovery.DiscoveryClient> が発生します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="a80cb-116">これを使用して、検索操作の進捗状況を示すプログレス バーを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="a80cb-117">また、受け取った検索応答を処理するのにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="a80cb-118">検索操作が完了すると、<xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="a80cb-119">最大数の応答を受信した場合、または <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> が経過した場合に、これが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a80cb-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="a80cb-120">検索操作が完了すると、結果が <xref:System.ServiceModel.Discovery.FindResponse> インスタンスで返されます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="a80cb-121"><xref:System.ServiceModel.Discovery.FindResponse> には <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> のコレクションが含まれており、これには、一致するサービスのアドレス、コントラクト型名、拡張子、リッスン URI、およびスコープが格納されています。</span><span class="sxs-lookup"><span data-stu-id="a80cb-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="a80cb-122">この情報を使用して、一致するいずれかのサービスに接続し、呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="a80cb-123">次の例では、System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) メソッドを呼び出し、返されたメタデータを使用して、見つかったサービスの呼び出しをする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="a80cb-124">使用する利点<xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)>はするが増えると、後でエンドポイントの一覧をキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="a80cb-125">このキャッシュを使用して、さまざまなエラー状況を処理するカスタム ロジックを構築できます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 <span data-ttu-id="a80cb-126">次の例は、検索操作を非同期で実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a80cb-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a80cb-127">非同期呼び出しを検索を参照してください[非同期検索](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="a80cb-127"> making asynchronous find calls, see [Asynchronous Find](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span></span>  
  
 <span data-ttu-id="a80cb-128">エンドポイント アドレスに基づいてサービスを検索するには、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> メソッドおよび <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="a80cb-129">エンドポイント アドレスをネットワーク アドレスで指定できないアドレスの場合は、これが便利です。</span><span class="sxs-lookup"><span data-stu-id="a80cb-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="a80cb-130">Resolve メソッドは、<xref:System.ServiceModel.Discovery.ResolveCriteria> のインスタンスを受け取ります。このインスタンスは、解決するサービスのエンドポイント アドレス、解決操作の最大期間、および拡張のセットを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a80cb-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="a80cb-131">次の例は、<xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> メソッドを使用してサービスを解決する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a80cb-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="a80cb-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="a80cb-132">DynamicEndpoint</span></span>  
 <span data-ttu-id="a80cb-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint>標準エンドポイントです ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [標準エンドポイント](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) が検出を実行し、一致するサービスが自動的に選択します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="a80cb-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> を作成して、検索するコントラクトおよび使用するバインディングを渡し、<xref:System.ServiceModel.Discovery.DynamicEndpoint> インスタンスを WCF クライアントに渡します。</span><span class="sxs-lookup"><span data-stu-id="a80cb-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="a80cb-135">次の例は、<xref:System.ServiceModel.Discovery.DynamicEndpoint> を作成および使用して電卓サービスを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a80cb-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="a80cb-136">クライアントが開かれるたびに、探索が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a80cb-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="a80cb-137">構成で定義されている任意のエンドポイントにも変換できます、<xref:System.ServiceModel.Discovery.DynamicEndpoint>追加することによって、`kind ="dynamicEndpoint"`属性をエンドポイント構成要素。</span><span class="sxs-lookup"><span data-stu-id="a80cb-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a><span data-ttu-id="a80cb-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="a80cb-138">See Also</span></span>  
 [<span data-ttu-id="a80cb-139">スコープの検出</span><span class="sxs-lookup"><span data-stu-id="a80cb-139">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="a80cb-140">非同期検索</span><span class="sxs-lookup"><span data-stu-id="a80cb-140">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="a80cb-141">基本</span><span class="sxs-lookup"><span data-stu-id="a80cb-141">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
