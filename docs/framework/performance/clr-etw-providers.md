---
title: "CLR ETW プロバイダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b76b3a1d4969a5ed81e5fa90afb06050b780804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-providers"></a><span data-ttu-id="94737-102">CLR ETW プロバイダー</span><span class="sxs-lookup"><span data-stu-id="94737-102">CLR ETW Providers</span></span>
<span data-ttu-id="94737-103">共通言語ランタイム (CLR: Common Language Runtime) には、ランタイム プロバイダーとランダウン プロバイダーという 2 つのプロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="94737-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="94737-104">ランタイム プロバイダーは、有効になっているキーワードに応じてイベントを発生させます (キーワードとはイベントのカテゴリです)。</span><span class="sxs-lookup"><span data-stu-id="94737-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="94737-105">たとえば、ローダー イベントを収集するには `LoaderKeyword` キーワードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="94737-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="94737-106">Windows イベント トレーシング (ETW: Event Tracing for Windows) のログは、.etl 拡張子を持つファイルに記録されます。このファイルは、必要に応じてコンマ区切り値 (.csv) ファイルで後処理できます。</span><span class="sxs-lookup"><span data-stu-id="94737-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="94737-107">.etl ファイルを .csv ファイルに変換する方法の詳細については、「[.NET Framework のログ記録の制御](../../../docs/framework/performance/controlling-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94737-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="94737-108">ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="94737-108">The Runtime Provider</span></span>  
 <span data-ttu-id="94737-109">ランタイム プロバイダーは、メインの CLR ETW プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="94737-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="94737-110">CLR ランタイム プロバイダーの GUID は e13c0d23-ccbc-4e12-931b-d9cc2eee27e4 です。</span><span class="sxs-lookup"><span data-stu-id="94737-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="94737-111">一般に利用可能なツールを使用して CLR ETW イベントを記録および表示する方法の例については、「[.NET Framework のログ記録の制御](../../../docs/framework/performance/controlling-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94737-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="94737-112">`LoaderKeyword` などのキーワードを使用する以外にも、発生頻度が高いイベントを記録するためのキーワードを有効にしなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="94737-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="94737-113">`StartEnumerationKeyword` キーワードと `EndEnumerationKeyword` キーワードはこれらのイベントを有効にします。概要については、「[CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」(CLR ETW のキーワードおよびレベル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94737-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="94737-114">ランダウン プロバイダー</span><span class="sxs-lookup"><span data-stu-id="94737-114">The Rundown Provider</span></span>  
 <span data-ttu-id="94737-115">ランダウン プロバイダーは、一部の特殊な用途で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="94737-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="94737-116">ただし、大半のユーザーにとっては、ランタイム プロバイダーで十分です。</span><span class="sxs-lookup"><span data-stu-id="94737-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="94737-117">CLR ランダウン プロバイダーの GUID は A669021C-C450-4609-A035-5AF59AF4DF18 です。</span><span class="sxs-lookup"><span data-stu-id="94737-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="94737-118">通常は、プロセスが開始される前に ETW のログを有効にし、プロセスの終了後にログを無効にしますが、</span><span class="sxs-lookup"><span data-stu-id="94737-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="94737-119">プロセスの実行中に ETW ログを有効にする場合もあります。その場合は、そのプロセスについて追加の情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="94737-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="94737-120">たとえば、シンボルを解決するには、ログを有効にする前に既に読み込まれていたメソッドのメソッド イベントを記録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94737-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="94737-121">`DCStart` イベントと `DCEnd` イベントは、データの収集が開始されたときと停止されたときのプロセスの状態をキャプチャします </span><span class="sxs-lookup"><span data-stu-id="94737-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="94737-122">(状態とは、既に Just-In-Time コンパイルされているメソッド、既に読み込まれているアセンブリなど、高レベルの情報を指します)。これらの 2 つのイベントを使用すると、そのプロセスで既に行われたことに関する情報 (どのメソッドが Just-In-Time コンパイルされたかなど) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="94737-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="94737-123">ランダウン プロバイダーで発生するイベントは、名前に `DC`、`DCStart`、`DCEnd`、または `DCInit` を含むイベントだけです。</span><span class="sxs-lookup"><span data-stu-id="94737-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="94737-124">また、これらのイベントはランダウン プロバイダーでしか発生しません。</span><span class="sxs-lookup"><span data-stu-id="94737-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="94737-125">ランダウン プロバイダーでは、イベント キーワード フィルターのほかに、`StartRundownKeyword` と `EndRundownKeyword` というキーワードによるターゲット フィルターもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="94737-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="94737-126">開始ランダウン</span><span class="sxs-lookup"><span data-stu-id="94737-126">Start Rundown</span></span>  
 <span data-ttu-id="94737-127">開始ランダウンは、`StartRundownKeyword` キーワードを使用してランダウン プロバイダーのイベントの記録を有効にした場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="94737-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="94737-128">開始ランダウンがトリガーされると、`DCStart` イベントが発生して、システムの状態がキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="94737-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="94737-129">列挙の開始前には `DCStartInit` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="94737-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="94737-130">列挙の終了時には `DCStartComplete` イベントが発生して、データの収集が正常に終了したことがコントローラーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="94737-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="94737-131">終了ランダウン</span><span class="sxs-lookup"><span data-stu-id="94737-131">End Rundown</span></span>  
 <span data-ttu-id="94737-132">終了ランダウンは、`EndRundownKeyword` キーワードを使用してランダウン プロバイダーのイベントの記録を有効にした場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="94737-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="94737-133">終了ランダウンでは、実行中のプロセスのプロファイリングが停止され、</span><span class="sxs-lookup"><span data-stu-id="94737-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="94737-134">`DCEnd` イベントにより、プロファイリングが停止されたときのシステムの状態がキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="94737-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="94737-135">列挙の開始前には `DCEndInit` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="94737-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="94737-136">列挙の終了時には `DCEndComplete` イベントが発生して、データの収集が正常に終了したことがコンシューマーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="94737-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="94737-137">開始ランダウンと終了ランダウンは、主にマネージ シンボルの解決のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="94737-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="94737-138">開始ランダウンは、プロファイリング セッションが開始される前に既に Just-In-Time コンパイル (JIT コンパイル) されていたメソッドのアドレス範囲の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="94737-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="94737-139">終了ランダウンは、プロファイリングを停止するときに JIT コンパイルされていたすべてのメソッドのアドレス範囲の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="94737-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="94737-140">終了ランダウンは、プロファイリング セッションが停止されると自動的に発生するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="94737-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="94737-141">ツールでマネージ シンボルを解決する必要がある場合は、プロファイリングを停止する直前に、`EndRundownKeyword` キーワードを有効にして CLR ランダウン プロバイダー セッションを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="94737-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="94737-142">マネージ シンボルを解決するためのメソッドのアドレス範囲の情報は、開始ランダウンと終了ランダウンのどちらでも取得できますが、`EndRundownKeyword` キーワード (`DCEnd` イベント) ではなく `StartRundownKeyword` キーワード (`DCStart` イベント) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94737-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="94737-143">`StartRundownKeyword` を使用すると、プロファイリング セッションの間にランダウンが発生するため、プロファイリング対象のシナリオに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="94737-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="94737-144">ランタイム プロバイダーとランダウン プロバイダーによる ETW データの収集</span><span class="sxs-lookup"><span data-stu-id="94737-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="94737-145">次の例は、マネージ プロセスのシンボルを、プロセスの開始または終了がプロファイリング期間の範囲内かどうかに関係なく最小限の影響で解決できるようにするための CLR ランダウン プロバイダーの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="94737-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1.  <span data-ttu-id="94737-146">CLR ランタイム プロバイダーを使用して ETW のログの記録を有効にします。</span><span class="sxs-lookup"><span data-stu-id="94737-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="94737-147">ログは、clr1.etl ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="94737-147">The log will be saved to the clr1.etl file.</span></span>  
  
2.  <span data-ttu-id="94737-148">プロセスの実行中にプロファイリングを停止するには、ランダウン プロバイダーを開始して `DCEnd` イベントをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="94737-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="94737-149">これにより、`DCEnd` イベントの収集を有効にして、ランダウン セッションを開始できます。</span><span class="sxs-lookup"><span data-stu-id="94737-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="94737-150">すべてのイベントが収集されるまでには 30 ～ 60 秒かかります。</span><span class="sxs-lookup"><span data-stu-id="94737-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="94737-151">ログは、clr1.et2 ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="94737-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3.  <span data-ttu-id="94737-152">すべての ETW プロファイリングを停止します。</span><span class="sxs-lookup"><span data-stu-id="94737-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  <span data-ttu-id="94737-153">プロファイルをマージして 1 つのログ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="94737-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="94737-154">merged.etl ファイルには、ランタイム プロバイダー セッションとランダウン プロバイダー セッションのイベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="94737-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="94737-155">ツールを使用して、ユーザーがプロファイリングの停止を要求したときに直ちにプロファイリングを停止する代わりに手順 2. と 3. (ランダウン セッションを開始してからプロファイリングを終了する) が実行されるようにすることも、</span><span class="sxs-lookup"><span data-stu-id="94737-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="94737-156">手順 4. もツールで実行できます。</span><span class="sxs-lookup"><span data-stu-id="94737-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94737-157">参照</span><span class="sxs-lookup"><span data-stu-id="94737-157">See Also</span></span>  
 [<span data-ttu-id="94737-158">共通言語ランタイムの ETW イベント</span><span class="sxs-lookup"><span data-stu-id="94737-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
