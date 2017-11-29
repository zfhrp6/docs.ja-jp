---
title: "循環トレース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b86867793424d6d0b42a18d6a2fbd6175bc1a47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="circular-tracing"></a><span data-ttu-id="18d12-102">循環トレース</span><span class="sxs-lookup"><span data-stu-id="18d12-102">Circular Tracing</span></span>
<span data-ttu-id="18d12-103">このサンプルでは、循環バッファ トレース リスナの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="18d12-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="18d12-104">製品版サービスの一般的なシナリオは、長期間使用できるサービスを持つことと、トレース ログを低レベルで有効にすることです。</span><span class="sxs-lookup"><span data-stu-id="18d12-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="18d12-105">こうしたサービスは、大量のディスク領域を消費します。</span><span class="sxs-lookup"><span data-stu-id="18d12-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="18d12-106">サービスのトラブルシューティングを行う場合、問題の解決に関連するのはトレース ログの最新データです。</span><span class="sxs-lookup"><span data-stu-id="18d12-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="18d12-107">このサンプルで示す循環バッファ トレース リスナの実装では、設定可能なデータ量を上限とする最新のトレースのみがディスク上に保持されます。</span><span class="sxs-lookup"><span data-stu-id="18d12-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="18d12-108">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)カスタム トレース リスナーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="18d12-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18d12-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18d12-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="18d12-110">このサンプルでは、について熟知している前提としています、[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)サンプルし、の提供されたドキュメントを読んだ、[トレースとメッセージ ログ](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="18d12-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="18d12-111">循環バッファ トレース リスナ</span><span class="sxs-lookup"><span data-stu-id="18d12-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="18d12-112">循環バッファ トレース リスナの実装の概念とは、2 つのファイルを使って、必要なトレース ログ データの全体量の半分を上限としたデータをそれぞれに保存することです。</span><span class="sxs-lookup"><span data-stu-id="18d12-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="18d12-113">リスナは 1 つのファイルを作成して、データ サイズの半分という限界に到達するまでデータを書き込みます。この限界に到達した時点で、2 番目のファイルに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="18d12-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="18d12-114">2 番目のファイルの限界に到達したら、リスナは最初のファイルを新しいトレースで上書きします。</span><span class="sxs-lookup"><span data-stu-id="18d12-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="18d12-115">このリスナーがから派生した、 `XmlWriteTraceListener` 、ログを表示することができ、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="18d12-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="18d12-116">ログの表示を試みる際に、サービス トレース ビューア ツールで 2 つのログ ファイルを両方同時に開くと、これらのファイルを簡単に再結合することができます。</span><span class="sxs-lookup"><span data-stu-id="18d12-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="18d12-117">サービス トレース ビューア ツールは、トレースが正しい順序で表示されるように自動的にトレースの並べ替えを管理します。</span><span class="sxs-lookup"><span data-stu-id="18d12-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="18d12-118">構成</span><span class="sxs-lookup"><span data-stu-id="18d12-118">Configuration</span></span>  
 <span data-ttu-id="18d12-119">サービスは、リスナとソースの要素に対して次のコードを追加することによって、循環バッファ トレース リスナを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="18d12-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="18d12-120">ファイルの最大サイズは、循環トレース リスナの構成の `maxFileSizeKB` 属性を設定することによって指定します。</span><span class="sxs-lookup"><span data-stu-id="18d12-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="18d12-121">このコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="18d12-121">This is demonstrated in the following code.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18d12-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="18d12-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="18d12-123">実行することを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="18d12-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="18d12-124">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="18d12-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="18d12-125">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="18d12-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="18d12-126">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="18d12-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="18d12-127">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18d12-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="18d12-128">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="18d12-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18d12-129">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="18d12-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="18d12-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="18d12-130">See Also</span></span>  
 [<span data-ttu-id="18d12-131">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="18d12-131">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
