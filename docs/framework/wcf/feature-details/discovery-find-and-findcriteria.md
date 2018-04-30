---
title: 探索検索と FindCriteria
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17ca5e12390e33525f0223917e4c72556a2a2ec7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="discovery-find-and-findcriteria"></a><span data-ttu-id="3b45f-102">探索検索と FindCriteria</span><span class="sxs-lookup"><span data-stu-id="3b45f-102">Discovery Find and FindCriteria</span></span>
<span data-ttu-id="3b45f-103">探索検索操作は、1 つ以上のサービスを探索するためにクライアントによって開始される操作であり、探索における主要なアクションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="3b45f-103">A discovery find operation is initiated by a client to discover one or more services and is one of the main actions in discovery.</span></span> <span data-ttu-id="3b45f-104">検索を実行すると、WS-Discovery Probe メッセージがネットワークを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-104">Performing a find sends a WS-Discovery Probe message over the network.</span></span> <span data-ttu-id="3b45f-105">指定された条件に一致するサービスは、WS-Discovery ProbeMatch メッセージを使用して応答します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-105">Services that match the criteria specified reply with WS-Discovery ProbeMatch messages.</span></span> <span data-ttu-id="3b45f-106">探索メッセージの詳細については、次を参照してください。、 [Ws-discovery 仕様](http://go.microsoft.com/fwlink/?LinkID=122347)です。</span><span class="sxs-lookup"><span data-stu-id="3b45f-106">For more information about discovery messages, see the [WS-Discovery specification](http://go.microsoft.com/fwlink/?LinkID=122347).</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="3b45f-107">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="3b45f-107">DiscoveryClient</span></span>  
 <span data-ttu-id="3b45f-108"><xref:System.ServiceModel.Discovery.DiscoveryClient> クラスは、検索操作を実行するメカニズムを提供し、探索クライアントの操作を簡単に実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3b45f-108">The <xref:System.ServiceModel.Discovery.DiscoveryClient> class provides the mechanism to perform find operations and makes performing discovery client operations easy.</span></span> <span data-ttu-id="3b45f-109">このクラスには、(ブロックする) 同期検索を実行する <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドと、ブロックしない非同期検索を実行する <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-109">It contains a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method, which performs a (blocking) synchronous find, and a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method, which initiates a non-blocking asynchronous find.</span></span> <span data-ttu-id="3b45f-110">どちらのメソッドも <xref:System.ServiceModel.Discovery.FindCriteria> パラメーターを使用し、<xref:System.ServiceModel.Discovery.FindResponse> オブジェクトを介してユーザーに結果を提供します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-110">Both methods take a <xref:System.ServiceModel.Discovery.FindCriteria> parameter, and provide results to the user through a <xref:System.ServiceModel.Discovery.FindResponse> object.</span></span>  
  
## <a name="findcriteria"></a><span data-ttu-id="3b45f-111">FindCriteria</span><span class="sxs-lookup"><span data-stu-id="3b45f-111">FindCriteria</span></span>  
 <span data-ttu-id="3b45f-112"><xref:System.ServiceModel.Discovery.FindCriteria> にはいくつかのプロパティがあり、検索対象のサービスを指定する検索条件と、検索を続行する期間を指定する検索終了条件に分類できます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-112"><xref:System.ServiceModel.Discovery.FindCriteria> has several properties, which can be grouped into search criteria, which specify what services you are looking for, and find termination criteria (how long the search should last).</span></span> <span data-ttu-id="3b45f-113"><xref:System.ServiceModel.Discovery.FindCriteria> には、複数の検索条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-113">A <xref:System.ServiceModel.Discovery.FindCriteria> can contain multiple search criteria.</span></span> <span data-ttu-id="3b45f-114">既定では、サービスがすべての条件に一致する必要があり、そうでない場合は、サービスがそれ自体を一致サービスと見なしません。</span><span class="sxs-lookup"><span data-stu-id="3b45f-114">By default, the service has to match all of the components otherwise it does not consider itself a matching service.</span></span> <span data-ttu-id="3b45f-115">条件の一部にのみ一致するサービスを検索する場合は、サービスにカスタムの検索ロジックを実装するか、複数のクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-115">If you want to find services that only match some of the criteria, you can implement custom find logic on the service or you can use multiple queries.</span></span>  
  
 <span data-ttu-id="3b45f-116">検索条件は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3b45f-116">Search criteria include:</span></span>  
  
-   <span data-ttu-id="3b45f-117"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - 省略できます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-117"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - Optional.</span></span> <span data-ttu-id="3b45f-118">検索対象のサービスのコントラクト名、およびサービスの検索に通常使用される条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-118">The contract name of the service being searched for and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="3b45f-119">複数のコントラクト名が指定されると、すべてのコントラクトに一致するサービス エンドポイントのみが応答します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-119">If more than one contract name is specified, only service endpoints matching ALL contracts reply.</span></span> <span data-ttu-id="3b45f-120">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、各エンドポイントでサポートされるコントラクトは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="3b45f-120">Note that in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] an endpoint can only support one contract.</span></span>  
  
-   <span data-ttu-id="3b45f-121"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - 省略できます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-121"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - Optional.</span></span> <span data-ttu-id="3b45f-122">Scopes は、個々のサービス エンドポイントの分類に使用される絶対 URI です。</span><span class="sxs-lookup"><span data-stu-id="3b45f-122">Scopes are absolute URIs that are used to categorize individual service endpoints.</span></span> <span data-ttu-id="3b45f-123">複数のエンドポイントが同じコントラクトを公開し、これらのエンドポイントのサブセットを検索する手段が必要な場合は、これを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-123">You may want to use this in scenarios where multiple endpoints expose the same contract and you want a way to search for a subset of the endpoints.</span></span> <span data-ttu-id="3b45f-124">複数のスコープが指定されると、すべてのスコープに一致するサービス エンドポイントのみが応答します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-124">If more than one scope is specified, only service endpoints matching ALL scopes reply.</span></span>  
  
-   <span data-ttu-id="3b45f-125"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Probe メッセージのスコープとエンドポイントのスコープとの一致の判定に使用する、一致アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-125"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Specifies the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span> <span data-ttu-id="3b45f-126">サポートされているスコープ一致規則は、次の 5 つです。</span><span class="sxs-lookup"><span data-stu-id="3b45f-126">There are five supported scope-matching rules:</span></span>  
  
    -   <span data-ttu-id="3b45f-127"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>: 大文字と小文字が区別される基本の文字列比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-127"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> does a basic case-sensitive string comparison.</span></span>  
  
    -   <span data-ttu-id="3b45f-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> 区切られたセグメント単位で一致する「/」です。</span><span class="sxs-lookup"><span data-stu-id="3b45f-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> matches by segments separated by "/".</span></span> <span data-ttu-id="3b45f-129">検索するhttp://contoso/building1と同じスコープを持つサービスhttp://contoso/building/floor1です。</span><span class="sxs-lookup"><span data-stu-id="3b45f-129">A search for http://contoso/building1 matches a service with scope http://contoso/building/floor1.</span></span> <span data-ttu-id="3b45f-130">一致しない注http://contoso/building100最後の 2 つのセグメントが一致しないためです。</span><span class="sxs-lookup"><span data-stu-id="3b45f-130">Note that it does not match http://contoso/building100 because the last two segments do not match.</span></span>  
  
    -   <span data-ttu-id="3b45f-131"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>: LDAP URL を使用してセグメント単位でスコープの一致を判定します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-131"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> matches scopes by segments using an LDAP URL.</span></span>  
  
    -   <span data-ttu-id="3b45f-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>: UUID 文字列を使用して、スコープが完全に一致するかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> matches scopes exactly using a UUID string.</span></span>  
  
    -   <span data-ttu-id="3b45f-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>: スコープを指定していないサービスのみを対象に一致を判定します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> matches only those services that do not specify a scope.</span></span>  
  
     <span data-ttu-id="3b45f-134">スコープ一致規則が指定されていない場合は、<xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-134">If a scope-matching rule is not specified, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> is used.</span></span>  
  
 <span data-ttu-id="3b45f-135">終了条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3b45f-135">Termination criteria include:</span></span>  
  
1.  <span data-ttu-id="3b45f-136"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - ネットワーク上でサービスからの応答を待機する最長時間。</span><span class="sxs-lookup"><span data-stu-id="3b45f-136"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - The maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="3b45f-137">既定の時間は 20 秒です。</span><span class="sxs-lookup"><span data-stu-id="3b45f-137">The default duration is 20 seconds.</span></span>  
  
2.  <span data-ttu-id="3b45f-138"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - 待機する応答の最大件数。</span><span class="sxs-lookup"><span data-stu-id="3b45f-138"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - The maximum number of replies to wait for.</span></span> <span data-ttu-id="3b45f-139"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> が経過する前に <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 応答が受信された場合は、検出操作が終了します。</span><span class="sxs-lookup"><span data-stu-id="3b45f-139">If <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> replies are received before <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed, the find operation ends.</span></span>  
  
## <a name="findresponse"></a><span data-ttu-id="3b45f-140">FindResponse</span><span class="sxs-lookup"><span data-stu-id="3b45f-140">FindResponse</span></span>  
 <span data-ttu-id="3b45f-141"><xref:System.ServiceModel.Discovery.FindResponse> には、ネットワーク上で一致するサービスから送信された応答を保持する <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> コレクション プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="3b45f-141"><xref:System.ServiceModel.Discovery.FindResponse> has an <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> collection property that contains any replies sent by matching services on the network.</span></span> <span data-ttu-id="3b45f-142">応答したサービスがない場合、このコレクションは空です。</span><span class="sxs-lookup"><span data-stu-id="3b45f-142">If no services replied, the collection is empty.</span></span> <span data-ttu-id="3b45f-143">1 つ以上のサービスが応答した場合、各応答は <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> オブジェクトに格納されます。これには、アドレスやコントラクトなど、サービスについての追加情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3b45f-143">If one or more services replied, each reply is stored in an <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> object, which contains the address, contract, and some additional information about the service.</span></span>  
  
 <span data-ttu-id="3b45f-144">次の例は、コードで検索操作を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3b45f-144">The following example shows how to perform a find operation in code.</span></span>  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b45f-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b45f-145">See Also</span></span>  
 [<span data-ttu-id="3b45f-146">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="3b45f-146">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="3b45f-147">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="3b45f-147">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="3b45f-148">スコープを使用した探索</span><span class="sxs-lookup"><span data-stu-id="3b45f-148">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="3b45f-149">非同期検索</span><span class="sxs-lookup"><span data-stu-id="3b45f-149">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="3b45f-150">基本</span><span class="sxs-lookup"><span data-stu-id="3b45f-150">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
