---
title: "ルーティング サービスを使用した Hello World"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1d068894c9ad28d786c7b433c56b6d0fd79acc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="aa90c-102">ルーティング サービスを使用した Hello World</span><span class="sxs-lookup"><span data-stu-id="aa90c-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="aa90c-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ルーティング サービスを示します。</span><span class="sxs-lookup"><span data-stu-id="aa90c-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Routing Service.</span></span> <span data-ttu-id="aa90c-104">ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに簡単に追加できるようにする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="aa90c-104">The Routing Service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="aa90c-105">このサンプルでは、標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 電卓のサンプルを改良し、ルーティング サービスを使用して通信するようにします。</span><span class="sxs-lookup"><span data-stu-id="aa90c-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="aa90c-106">このサンプルの電卓クライアントは、ルーターによって公開されるエンドポイントにメッセージを送信するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="aa90c-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="aa90c-107">ルーティング サービスは、送信されてきたすべてのメッセージを受け入れ、電卓サービスに対応するエンドポイントに転送するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="aa90c-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="aa90c-108">したがって、クライアントから送信されたメッセージはルーターで受信され、実際の電卓サービスに再ルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="aa90c-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="aa90c-109">電卓サービスからのメッセージはルーターに送り返され、ルーターから電卓クライアントに渡されます。</span><span class="sxs-lookup"><span data-stu-id="aa90c-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="aa90c-110">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="aa90c-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="aa90c-111">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、HelloRoutingService.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="aa90c-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open HelloRoutingService.sln.</span></span>  
  
2.  <span data-ttu-id="aa90c-112">F5 キーを押すか、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="aa90c-112">Press F5 or CTRL+SHIFT+B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aa90c-113">F5 キーを押した場合は、電卓クライアントが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="aa90c-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="aa90c-114">Ctrl キーと Shift キーを押しながら B キーを押した (ビルドする) 場合は、次のアプリケーションを手動で開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa90c-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>  
    >   
    >  1.  <span data-ttu-id="aa90c-115">電卓クライアント (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="aa90c-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>  
    > 2.  <span data-ttu-id="aa90c-116">電卓サービス (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="aa90c-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>  
    > 3.  <span data-ttu-id="aa90c-117">ルーティング サービス (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="aa90c-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>  
  
3.  <span data-ttu-id="aa90c-118">Enter キーを押してクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="aa90c-118">Press ENTER to start the client.</span></span>  
  
     <span data-ttu-id="aa90c-119">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa90c-119">You should see the following output:</span></span>  
  
     <span data-ttu-id="aa90c-120">Add(100,15.99) = 115.99</span><span class="sxs-lookup"><span data-stu-id="aa90c-120">Add(100,15.99) = 115.99</span></span>  
  
     <span data-ttu-id="aa90c-121">Subtract(145,76.54) = 68.46</span><span class="sxs-lookup"><span data-stu-id="aa90c-121">Subtract(145,76.54) = 68.46</span></span>  
  
     <span data-ttu-id="aa90c-122">Multiply(9,81.25) = 731.25</span><span class="sxs-lookup"><span data-stu-id="aa90c-122">Multiply(9,81.25) = 731.25</span></span>  
  
     <span data-ttu-id="aa90c-123">Divide(22,7) = 3.14285714285714</span><span class="sxs-lookup"><span data-stu-id="aa90c-123">Divide(22,7) = 3.14285714285714</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="aa90c-124">コードまたは App.Config で構成可能</span><span class="sxs-lookup"><span data-stu-id="aa90c-124">Configurable via Code or App.Config</span></span>  
 <span data-ttu-id="aa90c-125">サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="aa90c-125">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="aa90c-126">App.config ファイルの名前を別の名前に変更して認識されないようにし、ConfigureRouterViaCode() に対するメソッド呼び出しのコメントを解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa90c-126">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="aa90c-127">どちらの方法でも、ルーターの動作は同じになります。</span><span class="sxs-lookup"><span data-stu-id="aa90c-127">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="aa90c-128">シナリオ</span><span class="sxs-lookup"><span data-stu-id="aa90c-128">Scenario</span></span>  
 <span data-ttu-id="aa90c-129">このサンプルでは、基本的なメッセージ ポンプとして機能するルーターを示します。</span><span class="sxs-lookup"><span data-stu-id="aa90c-129">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="aa90c-130">ルーティング サービスは、構成済みの一連の送信先エンドポイントに直接メッセージを渡すように構成された透過的なプロキシ ノードとして機能します。</span><span class="sxs-lookup"><span data-stu-id="aa90c-130">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="aa90c-131">実際のシナリオ</span><span class="sxs-lookup"><span data-stu-id="aa90c-131">Real World Scenario</span></span>  
 <span data-ttu-id="aa90c-132">Contoso では、サービスの名前指定、アドレス指定、構成、およびセキュリティに関する柔軟性を高めるために、</span><span class="sxs-lookup"><span data-stu-id="aa90c-132">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="aa90c-133">基本的なメッセージ ポンプをサービスの前に配置して、それをエンドポイントとして公開しています。</span><span class="sxs-lookup"><span data-stu-id="aa90c-133">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="aa90c-134">これにより、実際のサービスの前にセキュリティが追加され、スケールアウトされたソリューションやサービスのバージョン管理を後で簡単に実装できるようになります。</span><span class="sxs-lookup"><span data-stu-id="aa90c-134">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aa90c-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="aa90c-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="aa90c-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="aa90c-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aa90c-137">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="aa90c-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa90c-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="aa90c-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="aa90c-139">参照</span><span class="sxs-lookup"><span data-stu-id="aa90c-139">See Also</span></span>  
 [<span data-ttu-id="aa90c-140">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="aa90c-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
