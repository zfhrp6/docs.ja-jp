---
title: "トレースの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c92aa17f25271173ca0bcbad1a8a180c9129abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-tracing"></a><span data-ttu-id="1f5eb-102">トレースの拡張</span><span class="sxs-lookup"><span data-stu-id="1f5eb-102">Extending Tracing</span></span>
<span data-ttu-id="1f5eb-103">このサンプルでは、ユーザー定義のアクティビティ トレースをクライアントとサービス コードに記述することにより、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] トレース機能を拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-103">This sample demonstrates how to extend the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="1f5eb-104">これにより、ユーザーはトレース アクティビティを作成し、トレースを作業の論理単位ごとにグループ化することができます。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="1f5eb-105">さらに、転送 (同じエンドポイント内) や伝達 (異なるエンドポイント間) を経由してアクティビティを相互に関連付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="1f5eb-106">このサンプルでは、トレースはクライアントとサービスの両方で有効です。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="1f5eb-107">クライアントとサービス構成ファイルでトレースを有効にする方法の詳細については、次を参照してください。[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="1f5eb-108">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f5eb-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f5eb-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1f5eb-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1f5eb-112">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f5eb-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="1f5eb-114">トレースとアクティビティの伝達</span><span class="sxs-lookup"><span data-stu-id="1f5eb-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="1f5eb-115">ユーザー定義のアクティビティ トレースにより、ユーザー自身のトレース アクティビティを作成できます。これによって、複数のトレースを作業の論理単位ごとにグループ化したり、転送や伝達を経由してアクティビティを相互に関連付けたり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] トレースのパフォーマンスの負荷 (ログ ファイルによるディスク領域の負荷など) を軽減できます。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="1f5eb-116">カスタム ソースの追加</span><span class="sxs-lookup"><span data-stu-id="1f5eb-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="1f5eb-117">ユーザー定義のトレースは、クライアントとサービス コードの両方に追加できます。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="1f5eb-118">これらのカスタム トレース記録しに表示するを許可するクライアントまたはサービス構成ファイルにトレース ソースの追加、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="1f5eb-119">次のコードは、`ServerCalculatorTraceSource` というユーザー定義のトレース ソースを構成ファイルに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a><span data-ttu-id="1f5eb-120">アクティビティの相互関連付け</span><span class="sxs-lookup"><span data-stu-id="1f5eb-120">Correlating Activities</span></span>  
 <span data-ttu-id="1f5eb-121">エンドポイント間でアクティビティを直接関連付けるには、`propagateActivity` トレース ソースの `true` 属性を `System.ServiceModel` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="1f5eb-122">また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティビティを経由せずにトレースを伝達するには、ServiceModel アクティビティ トレースをオフにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-122">Also, to propagate traces without going through [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="1f5eb-123">次のコード サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f5eb-124">ServiceModel アクティビティ トレースをオフにすることは、`switchValue` プロパティが表すトレース レベルをオフにすることとは異なります。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="1f5eb-125">パフォーマンスの負荷の軽減</span><span class="sxs-lookup"><span data-stu-id="1f5eb-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="1f5eb-126">`ActivityTracing` トレース ソースの `System.ServiceModel` をオフに設定すると、ユーザー定義のアクティビティ トレースのみを含み、ServiceModel アクティビティ トレースは含まないトレース ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="1f5eb-127">これによって、ログ ファイルのサイズがはるかに小さくなります。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="1f5eb-128">ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 処理トレースを関連付けることはできなくなります。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-128">However, the opportunity to correlate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f5eb-129">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1f5eb-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1f5eb-130">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1f5eb-131">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1f5eb-132">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f5eb-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5eb-133">参照</span><span class="sxs-lookup"><span data-stu-id="1f5eb-133">See Also</span></span>  
 [<span data-ttu-id="1f5eb-134">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="1f5eb-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
