---
title: 高度なフィルター
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: de8577be2d56ec3c942fd8736e350234daf6a35a
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805617"
---
# <a name="advanced-filters"></a><span data-ttu-id="7b4a2-102">高度なフィルター</span><span class="sxs-lookup"><span data-stu-id="7b4a2-102">Advanced Filters</span></span>
<span data-ttu-id="7b4a2-103">このサンプルでは、Windows Communication Foundation (WCF) ルーティング サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-103">This sample demonstrates a Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="7b4a2-104">ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに含めるしやすく WCF コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="7b4a2-105">このサンプルは、ルーティング サービスを使用して通信するために標準の WCF 電卓のサンプルを適合させます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-105">This sample adapts the standard WCF Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="7b4a2-106">そして、メッセージ フィルターとメッセージ フィルター テーブルを使用してコンテンツ ベースのルーティング ロジックを定義する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b4a2-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7b4a2-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b4a2-109">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b4a2-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="7b4a2-111">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="7b4a2-111">Sample Details</span></span>  
 <span data-ttu-id="7b4a2-112">次の表は、ルーティング サービスのメッセージ フィルター テーブルに追加されるメッセージ フィルターを示しています。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="7b4a2-113">フィルター</span><span class="sxs-lookup"><span data-stu-id="7b4a2-113">Filter</span></span>|<span data-ttu-id="7b4a2-114">ルール</span><span class="sxs-lookup"><span data-stu-id="7b4a2-114">Rule</span></span>|<span data-ttu-id="7b4a2-115">優先度</span><span class="sxs-lookup"><span data-stu-id="7b4a2-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="7b4a2-116">If (has header)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-116">If (has header)</span></span>|<span data-ttu-id="7b4a2-117">丸め</span><span class="sxs-lookup"><span data-stu-id="7b4a2-117">Rounding</span></span>|<span data-ttu-id="7b4a2-118">2</span><span class="sxs-lookup"><span data-stu-id="7b4a2-118">2</span></span>|  
|<span data-ttu-id="7b4a2-119">If (showed up on Ep2)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="7b4a2-120">Regular</span><span class="sxs-lookup"><span data-stu-id="7b4a2-120">Regular</span></span>|<span data-ttu-id="7b4a2-121">1</span><span class="sxs-lookup"><span data-stu-id="7b4a2-121">1</span></span>|  
|<span data-ttu-id="7b4a2-122">If (showed up with Address2)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-122">If (showed up with Address2)</span></span>|<span data-ttu-id="7b4a2-123">丸め</span><span class="sxs-lookup"><span data-stu-id="7b4a2-123">Rounding</span></span>|<span data-ttu-id="7b4a2-124">1</span><span class="sxs-lookup"><span data-stu-id="7b4a2-124">1</span></span>|  
|<span data-ttu-id="7b4a2-125">If (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-125">If (RoundRobin1)</span></span>|<span data-ttu-id="7b4a2-126">Regular</span><span class="sxs-lookup"><span data-stu-id="7b4a2-126">Regular</span></span>|<span data-ttu-id="7b4a2-127">0</span><span class="sxs-lookup"><span data-stu-id="7b4a2-127">0</span></span>|  
|<span data-ttu-id="7b4a2-128">If (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-128">If (RoundRobin2)</span></span>|<span data-ttu-id="7b4a2-129">丸め</span><span class="sxs-lookup"><span data-stu-id="7b4a2-129">Rounding</span></span>|<span data-ttu-id="7b4a2-130">0</span><span class="sxs-lookup"><span data-stu-id="7b4a2-130">0</span></span>|  
  
 <span data-ttu-id="7b4a2-131">メッセージ フィルターとメッセージ フィルター テーブルは、コードまたはアプリケーション構成ファイルで作成および構成できます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="7b4a2-132">このサンプルのメッセージ フィルターとメッセージ フィルター テーブルは、コードで定義されたものが RoutingService\routing.cs ファイルに、アプリケーション構成ファイルで定義されたものが RoutingService\App.config ファイルにあります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="7b4a2-133">以降では、このサンプルのメッセージ フィルターとメッセージ フィルター テーブルをコードで作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="7b4a2-134">まず最初に、<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> でカスタム ヘッダーを探します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="7b4a2-135"><xref:System.ServiceModel.WSHttpBinding> の結果のエンベロープ バージョンでは SOAP 1.2 が使用されるため、SOAP 1.2 名前空間を使用するように XPath ステートメントを定義します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="7b4a2-136"><xref:System.ServiceModel.Dispatcher.XPathMessageFilter> の既定の名前空間マネージャーでは SOAP 1.2 名前空間のプレフィックス /s12 が既に定義されているため、このプレフィックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="7b4a2-137">一方、クライアントが実際のヘッダー値を定義するために使用するカスタムの名前空間は含まれていないため、そのプレフィックスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="7b4a2-138">このヘッダーを持つすべてのメッセージがこのフィルターに一致します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="7b4a2-139">2 番目のフィルターは、<xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> で受信されたメッセージに一致する `calculatorEndpoint` です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="7b4a2-140">エンドポイント名は、サービス エンドポイント オブジェクトの作成時に定義されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="7b4a2-141">3 番目のフィルターは、<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="7b4a2-142">このフィルターは、指定したアドレス プレフィックス (アドレスの前半部分) に一致するアドレスを持つエンドポイントで受信されたメッセージに一致します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="7b4a2-143">としてこの例では、アドレス プレフィックスが定義されている"http://localhost/routingservice/router/rounding/"です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="7b4a2-144">つまり、受信メッセージにアドレスが"http://localhost/routingservice/router/rounding/\*"は、このフィルターで一致します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/\*" are matched by this filter.</span></span> <span data-ttu-id="7b4a2-145">この場合は、丸め処理を行う電卓のエンドポイントに表示されるメッセージのアドレスを持つ"http://localhost/routingservice/router/rounding/calculator"です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="7b4a2-146">最後の 2 種類のメッセージ フィルターは、カスタムの <xref:System.ServiceModel.Dispatcher.MessageFilter> です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="7b4a2-147">この例では、"RoundRobin" メッセージ フィルターが使用されています。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="7b4a2-148">このメッセージ フィルターは、付属の RoutingService\RoundRobinMessageFilter.cs ファイルに作成されています。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="7b4a2-149">これらのフィルターを同じグループに設定すると、両方のフィルターが同時に `true` を返さないように、メッセージに一致したという報告と一致しないという報告を交互に行うようになります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="7b4a2-150">次に、これらすべてのメッセージ フィルターを <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> に追加します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="7b4a2-151">その際に、メッセージ フィルター テーブルでフィルターが実行される順番を左右する優先度を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="7b4a2-152">優先度の高いフィルターが先に実行され、優先度の低いフィルターは後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="7b4a2-153">したがって、優先度が 2 のフィルターは優先度が 1 のフィルターより先に実行されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="7b4a2-154">優先度が指定されていない場合の既定の優先度は 0 です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="7b4a2-155">メッセージ フィルター テーブルは、特定の優先度のフィルターをすべて実行してから次の優先度に移ります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="7b4a2-156">特定の優先度で一致が検出された場合、それより低い優先度のフィルターでの検出は省略されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b4a2-157">ここではメッセージ フィルターの優先度の使い方を説明していますが、一般的には、優先度を設定しなくても正しく機能するようにフィルターを設計および構成するのがパフォーマンスの観点からも設計の観点からも理想的です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="7b4a2-158">最初に追加するフィルターは、優先度が 2 に設定された XPath フィルターです。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="7b4a2-159">これが、最初に実行されるメッセージ フィルターです。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-159">This is the first message filter that executes.</span></span> <span data-ttu-id="7b4a2-160">このフィルターによってカスタム ヘッダーが検出されると、他のフィルターの結果に関係なく、メッセージは丸め処理を行う電卓のエンドポイントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="7b4a2-161">優先度 1 では 2 つのフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="7b4a2-162">これらのフィルターは、メッセージが優先度 2 の XPath フィルターに一致しなかった場合にのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="7b4a2-163">この 2 つのフィルターは、受信したメッセージの宛先を特定する 2 とおりの方法を示しており、</span><span class="sxs-lookup"><span data-stu-id="7b4a2-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="7b4a2-164">それぞれが、2 つのエンドポイントの一方でメッセージが受信されたかどうかを確認します。したがって、両方が同時に `true` を返すことはないため、同じ優先度で実行できます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="7b4a2-165">最後に、優先度 0 (最も低い優先度) で RoundRobin メッセージ フィルターが実行されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="7b4a2-166">これらのフィルターは同じグループ名で構成されているため、一度に 1 つのフィルターのみが一致します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="7b4a2-167">カスタム ヘッダーを持つメッセージと特定の仮想エンドポイント宛てのメッセージはすべて既にルーティングされているため、RoundRobin メッセージ フィルターによって処理されるメッセージは、カスタム ヘッダーを持たない、既定のルーターのエンドポイント宛てのメッセージだけです。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="7b4a2-168">これらのメッセージは呼び出しのたびに切り替えられるため、操作の半分は通常の電卓のエンドポイントに送られ、もう半分は丸め処理を行う電卓のエンドポイントに送られます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7b4a2-169">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="7b4a2-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="7b4a2-170">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して AdvancedFilters.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="7b4a2-171">開くには**ソリューション エクスプ ローラー****ソリューション エクスプ ローラー**から、**ビュー**メニュー。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="7b4a2-172">Visual Studio で f5 キーまたは CTRL + SHIFT + B にキーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-172">Press F5 or CTRL+SHIFT+B in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="7b4a2-173">F5 キーを押したときに必要なプロジェクトを自動的に起動する場合は、ソリューションを右クリックし **プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="7b4a2-174">選択、**スタートアップ プロジェクト**ノードの下**共通プロパティ**左側のウィンドウでします。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="7b4a2-175">選択、**マルチ スタートアップ プロジェクト**ラジオ ボタンと、すべてのプロジェクトに対して、設定、**開始**アクション。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="7b4a2-176">Ctrl キーと Shift キーを押しながら B キーを押してプロジェクトをビルドする場合は、次のアプリケーションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="7b4a2-177">電卓クライアント (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="7b4a2-178">電卓サービス (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="7b4a2-179">丸め処理を行う電卓サービス (./RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="7b4a2-180">ルーティング サービス (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="7b4a2-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="7b4a2-181">電卓クライアントのコンソール ウィンドウで、Enter キーを押してクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="7b4a2-182">選択可能な送信先エンドポイントの一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="7b4a2-183">対応する文字を入力して送信先エンドポイントを選択し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="7b4a2-184">次に、カスタム ヘッダーを追加するかどうかを確認するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="7b4a2-185">追加する場合は Y (Yes) キーを、追加しない場合は N (No) キーを押して、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="7b4a2-186">選択に応じて異なる出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="7b4a2-187">メッセージにカスタム ヘッダーを追加した場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="7b4a2-188">カスタム ヘッダーを使用せずに丸め処理を行う電卓のエンドポイントを選択した場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="7b4a2-189">カスタム ヘッダーを使用せずに通常の電卓のエンドポイントを選択した場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="7b4a2-190">カスタム ヘッダーを使用せずに既定のルーターのエンドポイントを選択した場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="7b4a2-191">また、電卓サービスと丸め処理を行う電卓サービスは、呼び出された操作のログをそれぞれのコンソール ウィンドウに出力します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="7b4a2-192">クライアント コンソール ウィンドウで次のように入力します。`quit`を終了するには ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="7b4a2-193">サービスを終了するには、サービス コンソール ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="7b4a2-194">コードまたは App.config で構成可能</span><span class="sxs-lookup"><span data-stu-id="7b4a2-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="7b4a2-195">サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="7b4a2-196">RoutingService\App.config ファイルの名前を別の名前に変更して認識されないようにし、RoutingService\routing.cs の `ConfigureRouterViaCode()` に対するメソッド呼び出しのコメントを解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="7b4a2-197">どちらの方法でも、ルーターの動作は同じになります。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="7b4a2-198">シナリオ</span><span class="sxs-lookup"><span data-stu-id="7b4a2-198">Scenario</span></span>  
 <span data-ttu-id="7b4a2-199">このサンプルでは、1 つのエンドポイントを介して複数の種類または実装のサービスを公開することを可能にするコンテンツ ベースのルーターとして機能するルーターを示します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="7b4a2-200">実際のシナリオ</span><span class="sxs-lookup"><span data-stu-id="7b4a2-200">Real World Scenario</span></span>  
 <span data-ttu-id="7b4a2-201">Contoso では、すべてのサービスを仮想化して 1 つのエンドポイントのみを公開し、そのエンドポイントを通じて複数の異なる種類のサービスへのアクセスを提供したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="7b4a2-202">この場合は、ルーティング サービスのコンテンツ ベースのルーティング機能を使用して受信要求の送信先を決定します。</span><span class="sxs-lookup"><span data-stu-id="7b4a2-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b4a2-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b4a2-203">See Also</span></span>  
 [<span data-ttu-id="7b4a2-204">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="7b4a2-204">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
