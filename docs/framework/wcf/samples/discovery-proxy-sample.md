---
title: "探索プロキシのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b6e24c72002c7eef0e03af18f43992cc93b1d5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-proxy-sample"></a><span data-ttu-id="1db6b-102">探索プロキシのサンプル</span><span class="sxs-lookup"><span data-stu-id="1db6b-102">Discovery Proxy Sample</span></span>
<span data-ttu-id="1db6b-103">このサンプルでは、既存のサービスに関する情報を格納するために探索プロキシの実装を作成する方法、およびクライアントからそのプロキシに情報のクエリを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-103">This sample shows how to create an implementation of a Discovery proxy to store information about existing services and how clients can query that proxy for information.</span></span> <span data-ttu-id="1db6b-104">このサンプルは、3 つのプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1db6b-104">This sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="1db6b-105">**サービス**: 単純な[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]探索プロキシに自らを登録する電卓サービス。</span><span class="sxs-lookup"><span data-stu-id="1db6b-105">**Service**: A simple [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] calculator service that registers itself with the discovery proxy.</span></span>  
  
-   <span data-ttu-id="1db6b-106">**探索プロキシ**: 探索プロキシ サービスの実装です。</span><span class="sxs-lookup"><span data-stu-id="1db6b-106">**Discovery Proxy**: The implementation of a discovery proxy service.</span></span>  
  
-   <span data-ttu-id="1db6b-107">**クライアント**: する WCF クライアント アプリケーション サービスの検索、探索プロキシが必要です。</span><span class="sxs-lookup"><span data-stu-id="1db6b-107">**Client**: A WCF client application that calls the discovery proxy to search for services.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1db6b-108">使用例</span><span class="sxs-lookup"><span data-stu-id="1db6b-108">Demonstrates</span></span>  
 <span data-ttu-id="1db6b-109">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="1db6b-109">Discovery proxy implementation</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1db6b-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1db6b-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1db6b-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1db6b-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1db6b-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1db6b-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1db6b-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1db6b-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a><span data-ttu-id="1db6b-114">DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="1db6b-114">DiscoveryProxy</span></span>  
 <span data-ttu-id="1db6b-115">このサンプルでは、Program.cs ファイルの `Main` メソッドで、<xref:System.ServiceModel.Discovery.DiscoveryProxy> 型のサービスをホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-115">In the `Main` method of the Program.cs file, the sample shows how a service of type <xref:System.ServiceModel.Discovery.DiscoveryProxy> is hosted.</span></span> <span data-ttu-id="1db6b-116">このメソッドによって、<xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 型と <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 型の 2 つのエンドポイントが公開されます。</span><span class="sxs-lookup"><span data-stu-id="1db6b-116">It exposes two endpoints, one of type <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> and another of type <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>.</span></span> <span data-ttu-id="1db6b-117">どちらのエンドポイントも、TCP をトランスポートとして使用します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-117">Both of the endpoints use TCP as a transport.</span></span> <span data-ttu-id="1db6b-118"><xref:System.ServiceModel.Discovery.DiscoveryEndpoint> は、`probeEndpointAddress` パラメーターで指定された URI をリッスンします。クライアントは、ここにプローブ メッセージを送信して、プロキシに対するデータのクエリを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1db6b-118">The <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> is listening at the URI specified by the `probeEndpointAddress` parameter, this is where clients can send probe messages to query the proxy for its data.</span></span> <span data-ttu-id="1db6b-119"><xref:System.ServiceModel.Discovery.AnnouncementEndpoint> は、`announcementEndpointAddress` パラメーターで指定された URI をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="1db6b-119">The <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> is listening at the URI specified by the `announcementEndpointAddress` parameter.</span></span> <span data-ttu-id="1db6b-120">これは、プロキシがアナウンスをリッスンする場所です。</span><span class="sxs-lookup"><span data-stu-id="1db6b-120">This is where the proxy listens to for announcements.</span></span> <span data-ttu-id="1db6b-121">プロキシは、オンライン アナウンスを受け取るとサービスをキャッシュに追加し、オフライン アナウンスを受け取るとサービスをキャッシュから削除します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-121">When an online announcement is received, the proxy adds the service to its cache and when an offline announcement is received it removes the service from its cache.</span></span>  
  
 <span data-ttu-id="1db6b-122"><xref:System.ServiceModel.Discovery.DiscoveryProxy> の実装は DiscoveryProxy.cs に含まれています。</span><span class="sxs-lookup"><span data-stu-id="1db6b-122">The DiscoveryProxy.cs contains the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="1db6b-123">プロキシは <xref:System.Object> クラスから継承する必要があり、<xref:System.Runtime.Remoting.Messaging.AsyncResult> の実装を必要とします。</span><span class="sxs-lookup"><span data-stu-id="1db6b-123">The Proxy must inherit from the <xref:System.Object> class and requires an implementation of <xref:System.Runtime.Remoting.Messaging.AsyncResult>.</span></span> <span data-ttu-id="1db6b-124">インスタンス化すると、プロキシは新しい <xref:System.Collections.Generic.Dictionary%602> を作成し、それを使用して認識している要素を格納します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-124">At instantiation, the Proxy creates a new <xref:System.Collections.Generic.Dictionary%602>, which it uses to store elements it knows about.</span></span>  
  
 <span data-ttu-id="1db6b-125">ファイルは、Proxy Cache Methods および Discovery Proxy Implementation という 2 つの領域に分かれています。</span><span class="sxs-lookup"><span data-stu-id="1db6b-125">The file is divided into two regions, Proxy Cache Methods and Discovery Proxy Implementation.</span></span> <span data-ttu-id="1db6b-126">Proxy Cache Methods 領域には、<xref:System.Collections.Generic.Dictionary%602> の更新、<xref:System.Collections.Generic.Dictionary%602> に対するクエリの実行、およびユーザーへのデータの出力に使用するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1db6b-126">The Proxy Cache Methods region contains methods used to update the <xref:System.Collections.Generic.Dictionary%602>, perform queries against the <xref:System.Collections.Generic.Dictionary%602>, and print the data for users.</span></span> <span data-ttu-id="1db6b-127">Discovery Proxy Implementation 領域には、アナウンスおよびプローブ機能に必要なオーバーライドされたメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1db6b-127">The Discovery Proxy Implementation region contains the overridden methods required for the Announcement and Probe functionality.</span></span> <span data-ttu-id="1db6b-128">これらによって、オンライン アナウンス、オフライン アナウンス、またはプローブ メッセージを受け取った後にプロキシで実行されるアクションが定義されます。</span><span class="sxs-lookup"><span data-stu-id="1db6b-128">They define the actions taken by a proxy after receiving an Online Announcement, an Offline Announcement, or a Probe message.</span></span>  
  
## <a name="service"></a><span data-ttu-id="1db6b-129">サービス</span><span class="sxs-lookup"><span data-stu-id="1db6b-129">Service</span></span>  
 <span data-ttu-id="1db6b-130">Service プロジェクトの Program.cs ファイルでは、探索プロキシと同じ URI がアナウンス エンドポイントに使用されています。</span><span class="sxs-lookup"><span data-stu-id="1db6b-130">In the Program.cs file in the Service project, the same URI is used for its announcement endpoint as the discovery proxy.</span></span> <span data-ttu-id="1db6b-131">これは、サービスがこのエンドポイントを使用して送信したアナウンスを、プロキシが同じエンドポイントを使用して受け取るためです。</span><span class="sxs-lookup"><span data-stu-id="1db6b-131">This is because service uses the endpoint for sending the announcements, while the proxy uses it for receiving them.</span></span> <span data-ttu-id="1db6b-132">サービスは、<xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> を使用し、それにアナウンス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-132">The service uses the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> and adds an announcement endpoint to it.</span></span>  
  
## <a name="client"></a><span data-ttu-id="1db6b-133">クライアント</span><span class="sxs-lookup"><span data-stu-id="1db6b-133">Client</span></span>  
 <span data-ttu-id="1db6b-134">Client プロジェクトは、プロキシと同じ URI をプローブ エンドポイントに使用します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-134">The Client project uses the same URI for its probe endpoint as the Proxy.</span></span> <span data-ttu-id="1db6b-135">これは、このシナリオのプローブも、プロキシで使用できるエンドポイントに明確にユニキャストされるからです。</span><span class="sxs-lookup"><span data-stu-id="1db6b-135">This is because the probes in this scenario are also being unicast specifically to the endpoint available on the proxy.</span></span> <span data-ttu-id="1db6b-136">クライアントは、この既知のアドレスに接続してサービスのクエリを実行し、</span><span class="sxs-lookup"><span data-stu-id="1db6b-136">The Client connects to this well-known address and then queries it for the service.</span></span> <span data-ttu-id="1db6b-137">サービスを見つけるとそれに接続します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-137">Once it has found the service it connects to it.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1db6b-138">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="1db6b-138">To use this sample</span></span>  
  
1.  <span data-ttu-id="1db6b-139">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1db6b-139">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="1db6b-140">最初に、[ソリューションの基本ディレクトリ]\DiscoveryProxy\bin\debug に生成された探索プロキシ アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-140">First run the Discovery Proxy application, generated in [solution base directory]\DiscoveryProxy\bin\debug.</span></span> <span data-ttu-id="1db6b-141">探索プロキシを最初に実行しなければならないのは、サービスでアナウンスを送信するために TCP アナウンス エンドポイントを起動しておく必要があるからです。</span><span class="sxs-lookup"><span data-stu-id="1db6b-141">The Discovery Proxy must run first because TCP announcement endpoints must be up for the service to send its announcements.</span></span>  
  
3.  <span data-ttu-id="1db6b-142">2 番目に、[ソリューションの基本ディレクトリ]\Service\bin\debug に生成されたサービス アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-142">Second, run the service application generated in [solution base directory]\Service\bin\debug.</span></span> <span data-ttu-id="1db6b-143">起動時に、サービスから探索プロキシのアナウンス エンドポイントにアナウンスが送信され、サービスがプロキシのキャッシュに登録されます。</span><span class="sxs-lookup"><span data-stu-id="1db6b-143">At start-up, the service sends an announcement to the announcement endpoint of the discovery proxy and is registered in the proxy’s cache.</span></span>  
  
4.  <span data-ttu-id="1db6b-144">次に、[ソリューションの基本ディレクトリ]\Client\bin\debug に生成されたクライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-144">Next, run the client application, generated in [solution base directory]\Client\bin\debug.</span></span> <span data-ttu-id="1db6b-145">クライアントは、プロキシに対してクエリを実行してサービスのアドレスを取得し、サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-145">The client queries the proxy, gets the service address and then connects to the service.</span></span>  
  
5.  <span data-ttu-id="1db6b-146">最後に、クライアント、サービス、プロキシの順に終了します。</span><span class="sxs-lookup"><span data-stu-id="1db6b-146">Lastly, terminate the client, service and then the proxy.</span></span> <span data-ttu-id="1db6b-147">プロキシは、サービスのオフライン アナウンスを受け取るまでは実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1db6b-147">The proxy must be running for it to receive the service's offline announcement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db6b-148">参照</span><span class="sxs-lookup"><span data-stu-id="1db6b-148">See Also</span></span>
