---
title: ".NET ネイティブによる起動時間の改善の測定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03324850fbcb0264816b71cf8a8c6ad6a9688058
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="measuring-startup-improvement-with-net-native"></a><span data-ttu-id="924ee-102">.NET ネイティブによる起動時間の改善の測定</span><span class="sxs-lookup"><span data-stu-id="924ee-102">Measuring Startup Improvement with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="924ee-103">によって、アプリの起動時間が大幅に改善されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-103"> significantly improves the launch time of apps.</span></span> <span data-ttu-id="924ee-104">この改善は、ポータブルの低電力デバイスや複雑なアプリで特に顕著です。</span><span class="sxs-lookup"><span data-stu-id="924ee-104">This improvement is particularly noticeable on portable, low-powered devices and with complex apps.</span></span> <span data-ttu-id="924ee-105">このトピックでは、この起動時間の改善を測定するために必要となる基本的なインストルメンテーションの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="924ee-105">This topic helps you get started with the basic instrumentation needed to measure this startup improvement.</span></span>  
  
 <span data-ttu-id="924ee-106">パフォーマンスの調査を容易にするために、.NET Framework と Windows では、イベントが発生したときにアプリからツールに通知できるようにする Windows イベント トレーシング (ETW) という名前のイベント フレームワークを使用しています。</span><span class="sxs-lookup"><span data-stu-id="924ee-106">To facilitate performance investigations, the .NET Framework and Windows use an event framework called Event Tracing for Windows (ETW) that allows your app to notify tooling when events happen.</span></span> <span data-ttu-id="924ee-107">PerfView というツールを使用して、ETW イベントを簡単に表示および分析できます。</span><span class="sxs-lookup"><span data-stu-id="924ee-107">You can then use a tool called PerfView to easily view and analyze of ETW events.</span></span> <span data-ttu-id="924ee-108">このトピックでは、次の方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="924ee-108">This topic explains how to:</span></span>  
  
-   <span data-ttu-id="924ee-109"><xref:System.Diagnostics.Tracing.EventSource> クラスを使用したイベントの生成。</span><span class="sxs-lookup"><span data-stu-id="924ee-109">Use the <xref:System.Diagnostics.Tracing.EventSource> class to emit events.</span></span>  
  
-   <span data-ttu-id="924ee-110">PerfView を使用したこれらのイベントの収集。</span><span class="sxs-lookup"><span data-stu-id="924ee-110">Use PerfView to gather those events.</span></span>  
  
-   <span data-ttu-id="924ee-111">PerfView を使用したこれらのイベントの表示。</span><span class="sxs-lookup"><span data-stu-id="924ee-111">Use PerfView to display those events.</span></span>  
  
## <a name="using-eventsource-to-emit-events"></a><span data-ttu-id="924ee-112">EventSource を使用したイベントの生成</span><span class="sxs-lookup"><span data-stu-id="924ee-112">Using EventSource to emit events</span></span>  
 <span data-ttu-id="924ee-113"><xref:System.Diagnostics.Tracing.EventSource> は、カスタム イベント プロバイダーの作成元となる基底クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="924ee-113"><xref:System.Diagnostics.Tracing.EventSource> provides a base class from which to create a custom event provider.</span></span> <span data-ttu-id="924ee-114">一般的に、<xref:System.Diagnostics.Tracing.EventSource> のサブクラスを作成して、独自のイベント メソッドで `Write*` メソッドをラップします。</span><span class="sxs-lookup"><span data-stu-id="924ee-114">Generally, you create a subclass of <xref:System.Diagnostics.Tracing.EventSource> and wrap the `Write*` methods with your own event methods.</span></span> <span data-ttu-id="924ee-115">通常、シングルトン パターンが各 <xref:System.Diagnostics.Tracing.EventSource> に使用されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-115">A singleton pattern is generally used for each <xref:System.Diagnostics.Tracing.EventSource>.</span></span>  
  
 <span data-ttu-id="924ee-116">たとえば、次の例のクラスを使用して、2 つのパフォーマンス特性を測定できます。</span><span class="sxs-lookup"><span data-stu-id="924ee-116">For example, the class in the following example can be used to measure two performance characteristics:</span></span>  
  
-   <span data-ttu-id="924ee-117">`App` クラス コンストラクターが呼び出されるまでの時間。</span><span class="sxs-lookup"><span data-stu-id="924ee-117">The time until the `App` class constructor was called.</span></span>  
  
-   <span data-ttu-id="924ee-118">`MainPage` コンストラクターが呼び出されるまでの時間。</span><span class="sxs-lookup"><span data-stu-id="924ee-118">The time until the `MainPage` constructor was called.</span></span>  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 <span data-ttu-id="924ee-119">ここではいくつか注意する点があります。</span><span class="sxs-lookup"><span data-stu-id="924ee-119">There are a few things to notice here.</span></span> <span data-ttu-id="924ee-120">1 つ目は、シングルトンが `AppEventSource.Log` で作成されることです。</span><span class="sxs-lookup"><span data-stu-id="924ee-120">First, a singleton is created in `AppEventSource.Log`.</span></span> <span data-ttu-id="924ee-121">そのインスタンスが、すべてのログに使用されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-121">That instance will be used for all logging.</span></span> <span data-ttu-id="924ee-122">2 つ目は、各イベント メソッドに <xref:System.Diagnostics.Tracing.EventAttribute> があることです。</span><span class="sxs-lookup"><span data-stu-id="924ee-122">Second, each event method has an <xref:System.Diagnostics.Tracing.EventAttribute>.</span></span> <span data-ttu-id="924ee-123">これは、ツールが <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッドのインデックスを、`AppEventSource` で呼び出されたメソッドに関連付けるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="924ee-123">This helps tooling associate the index of the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method with the method that was called on `AppEventSource`.</span></span>  
  
 <span data-ttu-id="924ee-124">これらのイベントは単に説明を目的としていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="924ee-124">Note that these events are purely illustrative.</span></span> <span data-ttu-id="924ee-125">ほとんどのアプリ コードは、これらのイベントの後に実行されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-125">Most app code will run after these events.</span></span> <span data-ttu-id="924ee-126">ユーザー操作に対して、コード内のどのイベントが対応し、測定し、ベンチマークを改善するかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="924ee-126">You should understand which events in code correspond to user interactions, measure those, and improve those benchmarks.</span></span> <span data-ttu-id="924ee-127">また、イベント自体は時間内に 1 つのインスタンスのみをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="924ee-127">Also, the events themselves log only a single instance in time.</span></span> <span data-ttu-id="924ee-128">一般的に、操作ごとに開始イベントと停止イベントを対にしておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="924ee-128">It’s often useful to have paired start and stop events for every operation.</span></span> <span data-ttu-id="924ee-129">アプリの起動を調べる場合、開始イベントは通常、オペレーティング システムが生成する "Process/Start" イベントです。</span><span class="sxs-lookup"><span data-stu-id="924ee-129">When examining app startup, the start event is generally the "Process/Start" event that the operating system emits.</span></span>  
  
 <span data-ttu-id="924ee-130">たとえば、RSS リーダーを作成するとします。</span><span class="sxs-lookup"><span data-stu-id="924ee-130">For example, suppose you are creating an RSS reader.</span></span> <span data-ttu-id="924ee-131">次のような場合にイベントをログに記録すると役立ちます。</span><span class="sxs-lookup"><span data-stu-id="924ee-131">A few interesting locations to log an event are:</span></span>  
  
-   <span data-ttu-id="924ee-132">メイン ページが初めて表示された場合。</span><span class="sxs-lookup"><span data-stu-id="924ee-132">When the main page is first rendered.</span></span>  
  
-   <span data-ttu-id="924ee-133">ローカル ストレージから古い RSS ストーリーが逆シリアル化された場合。</span><span class="sxs-lookup"><span data-stu-id="924ee-133">When old RSS stories are deserialized from local storage.</span></span>  
  
-   <span data-ttu-id="924ee-134">アプリが新しいストーリーの同期を開始した場合。</span><span class="sxs-lookup"><span data-stu-id="924ee-134">When your app begins syncing new stories.</span></span>  
  
-   <span data-ttu-id="924ee-135">アプリが新しいストーリーの同期を終了した場合。</span><span class="sxs-lookup"><span data-stu-id="924ee-135">When your app has finished syncing new stories.</span></span>  
  
 <span data-ttu-id="924ee-136">アプリのインストルメント化は簡単です。派生クラスで適切なメソッドを呼び出すのみです。</span><span class="sxs-lookup"><span data-stu-id="924ee-136">Instrumenting an app is straightforward: Just call the appropriate method on the derived class.</span></span> <span data-ttu-id="924ee-137">前の例の `AppEventSource` を使用して、次のようにアプリをインストルメント化できます。</span><span class="sxs-lookup"><span data-stu-id="924ee-137">Using `AppEventSource` from the previous example, you can instrument an app as follows:</span></span>  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 <span data-ttu-id="924ee-138">アプリがインストルメント化されたら、イベントを収集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="924ee-138">When the app is instrumented, you’re ready to gather events.</span></span>  
  
## <a name="gathering-events-with-perfview"></a><span data-ttu-id="924ee-139">PerfView でのイベントの収集</span><span class="sxs-lookup"><span data-stu-id="924ee-139">Gathering events with PerfView</span></span>  
 <span data-ttu-id="924ee-140">PerfView は ETW イベントを使用して、アプリでさまざまなパフォーマンスを調査できるようにします。</span><span class="sxs-lookup"><span data-stu-id="924ee-140">PerfView uses ETW events to help you do all sorts of performance investigations on your app.</span></span> <span data-ttu-id="924ee-141">また、さまざまな種類のイベントのログ記録をオンまたはオフにするために使用できる構成 GUI も含まれています。</span><span class="sxs-lookup"><span data-stu-id="924ee-141">It also includes a configuration GUI that lets you turn logging for different types of events on or off.</span></span> <span data-ttu-id="924ee-142">PerfView は無料ツールであり、[Microsoft ダウンロード センター](http://www.microsoft.com/download/details.aspx?id=28567)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="924ee-142">PerfView is a free tool and can be downloaded from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=28567).</span></span> <span data-ttu-id="924ee-143">詳細については、[PerfView のチュートリアル ビデオ](http://channel9.msdn.com/Series/PerfView-Tutorial)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="924ee-143">For more information, watch the [PerfView tutorial videos](http://channel9.msdn.com/Series/PerfView-Tutorial).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="924ee-144">PerfView を使用して ARM システムでイベントを収集することはできません。</span><span class="sxs-lookup"><span data-stu-id="924ee-144">PerfView cannot be used to collect events on ARM systems.</span></span> <span data-ttu-id="924ee-145">ARM システムでイベントを収集する場合は、Windows Performance Recorder (WPR) を使用します。</span><span class="sxs-lookup"><span data-stu-id="924ee-145">To collect events on ARM systems, use Windows Performance Recorder (WPR).</span></span> <span data-ttu-id="924ee-146">詳細については、[Vance Morrison のブログ投稿](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="924ee-146">For more information, see [Vance Morrison's blog post](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).</span></span>  
  
 <span data-ttu-id="924ee-147">コマンド ラインから PerfView を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="924ee-147">You can also invoke PerfView from the command line.</span></span> <span data-ttu-id="924ee-148">プロバイダーからのイベントのみをログに記録する場合は、コマンドプロンプト ウィンドウを開き、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="924ee-148">To log only the events from your provider, open the Command Prompt window and enter the command:</span></span>  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 <span data-ttu-id="924ee-149">それぞれの文字について以下に説明します。</span><span class="sxs-lookup"><span data-stu-id="924ee-149">where:</span></span>  
  
 `-KernelEvents:Process`  
 <span data-ttu-id="924ee-150">プロセスが開始および停止したときに通知するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="924ee-150">Indicates that you want to know when the process starts and stops.</span></span> <span data-ttu-id="924ee-151">他のイベント時間から減算できるよう、アプリに Process/Start イベントが必要です。</span><span class="sxs-lookup"><span data-stu-id="924ee-151">You need the Process/Start event for your app so it can be subtracted from other event times.</span></span>  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 <span data-ttu-id="924ee-152">PerfView が既定でオンにするその他のプロバイダーをオフにし、MyCompany-MyApp プロバイダーをオンにします。</span><span class="sxs-lookup"><span data-stu-id="924ee-152">Turns off other providers that PerfView turns on by default, and turns on the MyCompany-MyApp provider.</span></span>  <span data-ttu-id="924ee-153">(アスタリスクは、<xref:System.Diagnostics.Tracing.EventSource> であることを示します。)</span><span class="sxs-lookup"><span data-stu-id="924ee-153">(The asterisk indicates that it is an <xref:System.Diagnostics.Tracing.EventSource>.)</span></span>  
  
 `collect outputFile`  
 <span data-ttu-id="924ee-154">収集を開始して、データを outputFile.etl.zip に保存するよう指定します。</span><span class="sxs-lookup"><span data-stu-id="924ee-154">Indicates that you want to start collection and save the data to outputFile.etl.zip.</span></span>  
  
 <span data-ttu-id="924ee-155">PerfView の開始後にアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="924ee-155">Run your app after starting PerfView.</span></span> <span data-ttu-id="924ee-156">アプリを実行するときには、次のことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="924ee-156">There are a few things to remember when running your app:</span></span>  
  
-   <span data-ttu-id="924ee-157">デバッグ ビルドではなく、リリース ビルドを使用します。</span><span class="sxs-lookup"><span data-stu-id="924ee-157">Use a release build, not a debug build.</span></span> <span data-ttu-id="924ee-158">デバッグ ビルドには、多くの場合、アプリの実行に予想よりも時間がかかる原因となる、余分なエラー チェックおよびエラー処理コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="924ee-158">Debug builds often contain extra error checking and error handling code that can cause your app to run slower than expected.</span></span>  
  
-   <span data-ttu-id="924ee-159">デバッガーをアタッチしてアプリを実行すると、アプリのパフォーマンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="924ee-159">Running your app with a debugger attached affects the performance of your app.</span></span>  
  
-   <span data-ttu-id="924ee-160">Windows では、アプリの起動時間を短縮するために複数のキャッシュ戦略を使用しています。</span><span class="sxs-lookup"><span data-stu-id="924ee-160">Windows uses multiple caching strategies to speed up app launch times.</span></span> <span data-ttu-id="924ee-161">アプリが現在メモリにキャッシュされており、ディスクから読み込む必要がない場合、起動時間は短縮されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-161">If your app is currently cached in memory and doesn't have to be loaded from disk, it will start faster.</span></span> <span data-ttu-id="924ee-162">一貫性を保つために、測定前にアプリを数回起動して停止してください。</span><span class="sxs-lookup"><span data-stu-id="924ee-162">To ensure consistency, start and close your app a few times before measuring it.</span></span>  
  
 <span data-ttu-id="924ee-163">生成されたイベントを PerfView can が収集できるようにアプリを実行した場合は、**[コレクションの停止]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="924ee-163">When you’ve run your app so that PerfView can collect emitted events, choose the **Stop Collection** button.</span></span> <span data-ttu-id="924ee-164">通常は、アプリを停止する前にコレクションを停止して、不要なイベントを取得しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="924ee-164">Generally, you should stop collection before closing your app so you don’t get extraneous events.</span></span> <span data-ttu-id="924ee-165">ただし、シャットダウンまたは中断のパフォーマンスを測定する場合は、コレクションを続行します。</span><span class="sxs-lookup"><span data-stu-id="924ee-165">However, if you’re measuring shutdown or suspension performance, you’ll want to continue collection.</span></span>  
  
## <a name="displaying-the-events"></a><span data-ttu-id="924ee-166">イベントの表示</span><span class="sxs-lookup"><span data-stu-id="924ee-166">Displaying the events</span></span>  
 <span data-ttu-id="924ee-167">既に収集されたイベントを表示するには、PerfView を使用して作成した .etl ファイルまたは .etl.zip ファイルを開き、**[イベント]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="924ee-167">To view the events that have already been collected, use PerfView to open the .etl or .etl.zip file you created and choose **Events**.</span></span> <span data-ttu-id="924ee-168">ETW によって、他のプロセスのイベントを含む、多数のイベントに関する情報が収集されています。</span><span class="sxs-lookup"><span data-stu-id="924ee-168">ETW will have collected information about a large number of events, including events from other processes.</span></span> <span data-ttu-id="924ee-169">調査の対象を絞り込むために、イベント ビューで次のテキスト ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="924ee-169">To focus your investigation, complete the following text boxes in the events view:</span></span>  
  
-   <span data-ttu-id="924ee-170">**[Process Filter]\(プロセス フィルター\)** ボックスで、アプリの名前を指定します (".exe" は含めません)。</span><span class="sxs-lookup"><span data-stu-id="924ee-170">In the **Process Filter** box, specify your app name (without ".exe").</span></span>  
  
-   <span data-ttu-id="924ee-171">**[Event Types Filter]\(イベント タイプ フィルター\)** ボックスに、「`Process/Start | MyCompany-MyApp`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="924ee-171">In the **Event Types Filter** box, specify `Process/Start | MyCompany-MyApp`.</span></span> <span data-ttu-id="924ee-172">これにより、MyCompany-MyApp のイベントと Windows Kernel/Process/Start イベントのフィルターが設定されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-172">This sets a filter for events from MyCompany-MyApp and the Windows Kernel/Process/Start event.</span></span>  
  
 <span data-ttu-id="924ee-173">左ペインに示されているイベントをすべて選択し (Ctrl + A)、**Enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="924ee-173">Select all the events listed in the left pane (Ctrl-A) and choose the **Enter** key.</span></span> <span data-ttu-id="924ee-174">これで、各イベントのタイムスタンプを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="924ee-174">Now, you should be able to see the timestamps from each event.</span></span> <span data-ttu-id="924ee-175">これらのタイムスタンプは、トレースの開始時間を基準としています。そのため、起動時からの経過時間を調べるには、プロセスの開始時間から各イベントの時間を減算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="924ee-175">These timestamps are relative to the start of the trace, so you have to subtract the time of each event from the start time of the process to identify the elapsed time since startup.</span></span> <span data-ttu-id="924ee-176">Ctrl キーを押しながらクリックして 2 つのタイムスタンプを選択すると、ページ下部にあるステータス バーにそれらのタイムスタンプの差が表示されます。</span><span class="sxs-lookup"><span data-stu-id="924ee-176">If you use Ctrl+Click to select two timestamps, you'll see the difference between them displayed in the status bar at the bottom of the page.</span></span> <span data-ttu-id="924ee-177">これにより、表示されている 2 つのイベント間の経過時間が簡単にわかるようになります (プロセスの開始を含む)。</span><span class="sxs-lookup"><span data-stu-id="924ee-177">This makes it easy to see the elapsed time between any two events in the display (including process start).</span></span> <span data-ttu-id="924ee-178">ビューのショートカット メニューを開いて、CSV ファイルにエクスポートしたり、Microsoft Excel を開いてデータを保存または処理したりするなど、便利なオプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="924ee-178">You can open the shortcut menu for the view and select from a number of useful options, like exporting to CSV files or opening Microsoft Excel to save or process the data.</span></span>  
  
 <span data-ttu-id="924ee-179">元のアプリと [!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンを使用してビルドしたバージョンの両方についてこの手順を繰り返し、パフォーマンスの違いを比較できます。</span><span class="sxs-lookup"><span data-stu-id="924ee-179">By repeating the procedure for both your original app and the version you built by using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain, you can compare the difference in performance.</span></span>   <span data-ttu-id="924ee-180">通常、[!INCLUDE[net_native](../../../includes/net-native-md.md)] アプリの方が [!INCLUDE[net_native](../../../includes/net-native-md.md)]以外のアプリよりも速く起動します。</span><span class="sxs-lookup"><span data-stu-id="924ee-180">[!INCLUDE[net_native](../../../includes/net-native-md.md)] apps generally start faster than non-[!INCLUDE[net_native](../../../includes/net-native-md.md)] apps.</span></span> <span data-ttu-id="924ee-181">より詳しく調べる場合は、最も時間がかかっているコードの部分を PerfView で特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="924ee-181">If you’re interested in digging deeper, PerfView can also identify the parts of your code that are taking the most time.</span></span> <span data-ttu-id="924ee-182">詳細については、[PerfView のチュートリアル](http://channel9.msdn.com/Series/PerfView-Tutorial)または [Vance Morrison のブログ エントリ](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="924ee-182">For more information, watch the [PerfView tutorials](http://channel9.msdn.com/Series/PerfView-Tutorial) or read [Vance Morrison’s blog entry](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="924ee-183">参照</span><span class="sxs-lookup"><span data-stu-id="924ee-183">See Also</span></span>  
 <xref:System.Diagnostics.Tracing.EventSource>
