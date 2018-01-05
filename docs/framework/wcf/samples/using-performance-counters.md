---
title: "パフォーマンス カウンターの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef5a499e6d940e45e0c9aab093b0a1c00bb6cc32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-performance-counters"></a><span data-ttu-id="81396-102">パフォーマンス カウンターの使用</span><span class="sxs-lookup"><span data-stu-id="81396-102">Using Performance Counters</span></span>
<span data-ttu-id="81396-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] パフォーマンス カウンタにアクセスする方法と、ユーザー定義のパフォーマンス カウンタを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="81396-103">This sample demonstrates how to access [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="81396-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="81396-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81396-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81396-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="81396-106">このサンプルでは、クライアントが `ICalculator` サービスの 4 つのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="81396-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="81396-107">この処理は、ユーザーが中断するまで継続して行われます。</span><span class="sxs-lookup"><span data-stu-id="81396-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="81396-108">サービスは変更されません。</span><span class="sxs-lookup"><span data-stu-id="81396-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="81396-109">パフォーマンス カウンタは、サービスの Web.config ファイルの診断セクションで有効にします。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81396-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="81396-110">このタスクを実行することもを使用して、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="81396-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="81396-111">パフォーマンス カウンタが有効な場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パフォーマンス カウンタのスイート全体がサービスについて有効です。</span><span class="sxs-lookup"><span data-stu-id="81396-111">When performance counters are enabled, the entire suite of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters is enabled for the service.</span></span> <span data-ttu-id="81396-112">.NET Framework は、`ServiceModelService`、`ServiceModelEndpoint`、および `ServiceModelOperation` の 3 つのレベルで、パフォーマンス データを自動的に保持します。</span><span class="sxs-lookup"><span data-stu-id="81396-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="81396-113">これらの各レベルには、"呼び出し"、"1 秒あたりの呼び出し回数"、"承認されていないセキュリティ呼び出し" などのパフォーマンス カウンタがあります。</span><span class="sxs-lookup"><span data-stu-id="81396-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="81396-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="81396-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="81396-115">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="81396-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="81396-116">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="81396-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="81396-117">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="81396-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="81396-118">パフォーマンス データを表示するには</span><span class="sxs-lookup"><span data-stu-id="81396-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="81396-119">ツールを起動、パフォーマンス モニター をクリックして**開始**、**を実行しています.**、入力`perfmon` をクリック**ok、**またはコントロール パネルから選択**管理ツール** をダブルクリック**パフォーマンス**です。</span><span class="sxs-lookup"><span data-stu-id="81396-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81396-120">サンプル コードが実行されるまでは、カウンタを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="81396-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="81396-121">一覧表示されているパフォーマンス カウンタを削除するには、削除するパフォーマンス カウンタを選択して Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="81396-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="81396-122">追加[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]グラフ ウィンドウを右クリックしてカウンター**カウンターの追加**です。</span><span class="sxs-lookup"><span data-stu-id="81396-122">Add [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="81396-123">**カウンターの追加**ダイアログ ボックスで、 **ServiceModelOperation 3.0.0.0、ServiceModelEndpoint 3.0.0.0、または ServiceModelService 3.0.0.0**パフォーマンス オブジェクト でドロップダウン リスト ボックス。</span><span class="sxs-lookup"><span data-stu-id="81396-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="81396-124">表示するカウンタを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="81396-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="81396-125">コンピューター上で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが実行されていない場合は、サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パフォーマンス カウンターは存在しません。</span><span class="sxs-lookup"><span data-stu-id="81396-125">There are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters for a service if there are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="81396-126">構成エディターを使用してカウンターを有効にするには</span><span class="sxs-lookup"><span data-stu-id="81396-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="81396-127">SvcConfigEditor.exe のインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="81396-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="81396-128">ファイル メニューをクリックして**開く** をクリックし、 **Config ファイル.**.</span><span class="sxs-lookup"><span data-stu-id="81396-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="81396-129">サンプル アプリケーションの service フォルダーに移動し、Web.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="81396-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="81396-130">をクリックして**診断**構成ツリーにします。</span><span class="sxs-lookup"><span data-stu-id="81396-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="81396-131">トグル**パフォーマンス カウンター**で、**診断**'All' を表示するウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="81396-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="81396-132">構成ファイルを保存し、エディターを終了します。</span><span class="sxs-lookup"><span data-stu-id="81396-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81396-133">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="81396-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="81396-134">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="81396-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81396-135">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="81396-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81396-136">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="81396-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="81396-137">参照</span><span class="sxs-lookup"><span data-stu-id="81396-137">See Also</span></span>  
 [<span data-ttu-id="81396-138">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="81396-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
