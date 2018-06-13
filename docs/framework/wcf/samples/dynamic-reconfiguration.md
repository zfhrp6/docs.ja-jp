---
title: 動的再構成
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: 81a2b494c48476e683053e12e58264e756201124
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810381"
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="a44c1-102">動的再構成</span><span class="sxs-lookup"><span data-stu-id="a44c1-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="a44c1-103">このサンプルでは、Windows Communication Foundation (WCF) ルーティング サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="a44c1-104">ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに含めるしやすく WCF コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a44c1-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="a44c1-105">このサンプルは、ルーティング サービスを使用して通信するために標準の WCF 電卓のサンプルを適合させます。</span><span class="sxs-lookup"><span data-stu-id="a44c1-105">This sample adapts the standard WCF Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="a44c1-106">このサンプルでは、実行時にルーティング サービスを動的に再構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a44c1-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a44c1-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a44c1-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a44c1-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a44c1-109">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="a44c1-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a44c1-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a44c1-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="a44c1-111">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="a44c1-111">Sample Details</span></span>  
 <span data-ttu-id="a44c1-112">このサンプルでは、実行時にルーティング サービスを動的に再構成するために、5 秒ごとにタイマーを作動させ、新しい <xref:System.ServiceModel.Routing.RoutingConfiguration> オブジェクトを作成して適用します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="a44c1-113">この構成は、通常の電卓のエンドポイントまたは丸め処理を行う電卓のエンドポイントのいずれかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a44c1-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="a44c1-114">電卓クライアント アプリケーションは、ルーティング サービスがその時点でどちらのサービスにルーティングするように構成されているかに応じて、いずれか一方のサービスからメッセージを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a44c1-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="a44c1-115">ルーティング サービスのカスタム動作を介した動的再構成機能が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a44c1-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="a44c1-116">このカスタム動作は、5 秒ごとに作動する単純なスレッド タイマーを含むサービス拡張をアタッチします。このスレッド タイマーにより、`UpdateRules` メソッドへのコールバックが発生し、</span><span class="sxs-lookup"><span data-stu-id="a44c1-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="a44c1-117">新しいルーティング構成が作成および適用されます。</span><span class="sxs-lookup"><span data-stu-id="a44c1-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="a44c1-118">実際の配置では、このコールバックは、別の種類のイベント (SQL-Event 通知や WS-Discovery アナウンスなど) の結果として行われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a44c1-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a44c1-119">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a44c1-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="a44c1-120">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して DynamicReconfiguration.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="a44c1-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="a44c1-121">開くには**ソリューション エクスプ ローラー****ソリューション エクスプ ローラー**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="a44c1-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="a44c1-122">キーを押して**f5 キーを押して**または**CTRL + SHIFT + B** Visual Studio でします。</span><span class="sxs-lookup"><span data-stu-id="a44c1-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="a44c1-123">キーを押したときに必要なプロジェクトを自動的に起動するかかどうか**f5 キーを押して**、ソリューションを右クリックし **プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="a44c1-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="a44c1-124">選択、**スタートアップ プロジェクト**ノードの下**共通プロパティ**左側のウィンドウでします。</span><span class="sxs-lookup"><span data-stu-id="a44c1-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="a44c1-125">選択、**マルチ スタートアップ プロジェクト**ラジオ ボタンと、すべてのプロジェクトに対して、設定、**開始**アクション。</span><span class="sxs-lookup"><span data-stu-id="a44c1-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="a44c1-126">使用してプロジェクトをビルドする場合**CTRL + SHIFT + B**、次のアプリケーションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a44c1-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="a44c1-127">電卓クライアント (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="a44c1-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="a44c1-128">電卓サービス (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a44c1-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="a44c1-129">丸め処理を行う電卓サービス (./RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a44c1-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="a44c1-130">ルーティング サービス (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="a44c1-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="a44c1-131">電卓クライアントのコンソール ウィンドウで、Enter キーを押してクライアントを開始し、電卓サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="a44c1-132">ルーティング サービスは、丸め処理を行う電卓と通常の電卓に交互にメッセージをルーティングします。これはルーティング構成が 5 秒ごとに動的に変化するためです。</span><span class="sxs-lookup"><span data-stu-id="a44c1-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="a44c1-133">ルーティング サービスがどちらのエンドポイントにメッセージを送信するように構成されているかに応じて、異なる出力がクライアント コンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a44c1-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="a44c1-134">Enter キーを 5 秒以上にわたって繰り返し押して、サービスから返される結果が変化することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="a44c1-135">次に、ルーター サービスが丸め処理を行う電卓サービスにメッセージをルーティングするように構成されている場合に返される出力を示します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="a44c1-136">次に、ルーティング サービスが通常の電卓サービスにメッセージをルーティングするように構成されている場合に返される出力を示します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="a44c1-137">また、電卓サービスと丸め処理を行う電卓サービスは、呼び出された操作のログをそれぞれのコンソール ウィンドウに出力します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="a44c1-138">クライアント コンソール ウィンドウには、「終了」を入力し、enter キーを押して終了します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="a44c1-139">サービスを終了するには、サービス コンソール ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="a44c1-140">シナリオ</span><span class="sxs-lookup"><span data-stu-id="a44c1-140">Scenario</span></span>  
 <span data-ttu-id="a44c1-141">このサンプルでは、1 つのエンドポイントを介して複数の種類または実装のサービスを公開することを可能にするコンテンツ ベースのルーターとして機能するルーターを示します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="a44c1-142">実際のシナリオ</span><span class="sxs-lookup"><span data-stu-id="a44c1-142">Real World Scenario</span></span>  
 <span data-ttu-id="a44c1-143">Contoso では、すべてのサービスを仮想化して 1 つのエンドポイントのみを公開し、そのエンドポイントを通じて複数の異なる種類のサービスへのアクセスを提供したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="a44c1-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="a44c1-144">この場合は、ルーティング サービスのコンテンツ ベースのルーティング機能を使用して受信要求の送信先を決定します。</span><span class="sxs-lookup"><span data-stu-id="a44c1-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44c1-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="a44c1-145">See Also</span></span>  
 [<span data-ttu-id="a44c1-146">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="a44c1-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
