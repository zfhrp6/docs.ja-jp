---
title: "待機モード"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, intrusiveness
- garbage collection, latency modes
ms.assetid: 96278bb7-6eab-4612-8594-ceebfc887d81
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 439fdd8fe78a0c0f0fda4ac7e759a4a780bb9b58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="latency-modes"></a><span data-ttu-id="a4ec2-102">待機モード</span><span class="sxs-lookup"><span data-stu-id="a4ec2-102">Latency Modes</span></span>
<span data-ttu-id="a4ec2-103">オブジェクトを再利用するには、ガベージ コレクターはアプリケーションで実行中のすべてのスレッドを停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-103">To reclaim objects, the garbage collector must stop all the executing threads in an application.</span></span> <span data-ttu-id="a4ec2-104">状況によっては、アプリケーションがデータの取得やコンテンツの表示を行うときなど、重要なときにフル ガベージ コレクションが発生し、パフォーマンスが低下することがあります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-104">In some situations, such as when an application retrieves data or displays content, a full garbage collection can occur at a critical time and impede performance.</span></span> <span data-ttu-id="a4ec2-105">ガベージ コレクターが作業に悪影響を与える度合いを調整するには、<xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> プロパティを <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 値のいずれかに設定することができます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-105">You can adjust the intrusiveness of the garbage collector by setting the <xref:System.Runtime.GCSettings.LatencyMode%2A?displayProperty=nameWithType> property to one of the <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="a4ec2-106">Latency (待機時間) は、ガベージ コレクターが実行中のアプリケーションに割って入る時間を指します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-106">Latency refers to the time that the garbage collector intrudes in your application.</span></span> <span data-ttu-id="a4ec2-107">待機時間が短い場合、ガベージ コレクターがオブジェクトを再利用する処理は控えめになり、アプリケーションに悪影響を与える度合いが下がります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-107">During low latency periods, the garbage collector is more conservative and less intrusive in reclaiming objects.</span></span> <span data-ttu-id="a4ec2-108"><xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> 列挙体には、待機時間の短い設定として次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-108">The <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType> enumeration provides two low latency settings:</span></span>  
  
-   <span data-ttu-id="a4ec2-109"><xref:System.Runtime.GCLatencyMode.LowLatency> では、ジェネレーション 2 のガベージ コレクションが停止し、ジェネレーション 0 および 1 のみガベージ コレクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-109"><xref:System.Runtime.GCLatencyMode.LowLatency> suppresses generation 2 collections and performs only generation 0 and 1 collections.</span></span> <span data-ttu-id="a4ec2-110">これは、短時間の場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-110">It can be used only for short periods of time.</span></span> <span data-ttu-id="a4ec2-111">この設定を長時間にわたって使用すると、システムのメモリが不足してガベージ コレクターがガベージ コレクションをトリガーした場合に、アプリケーションが少しの間停止したり、高速性を必要とする操作が中断されたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-111">Over longer periods, if the system is under memory pressure, the garbage collector will trigger a collection, which can briefly pause the application and disrupt a time-critical operation.</span></span> <span data-ttu-id="a4ec2-112">この設定は、ワークステーションのガベージ コレクションでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-112">This setting is available only for workstation garbage collection.</span></span>  
  
-   <span data-ttu-id="a4ec2-113"><xref:System.Runtime.GCLatencyMode.SustainedLowLatency> では、フォアグラウンドのジェネレーション 2 のガベージ コレクションが停止し、ジェネレーション 0 および 1 とバックグラウンドのジェネレーション 2 のガベージ コレクションのみが実行されます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-113"><xref:System.Runtime.GCLatencyMode.SustainedLowLatency> suppresses foreground generation 2 collections and performs only generation 0, 1, and background generation 2 collections.</span></span> <span data-ttu-id="a4ec2-114">これは長時間にわたって使用でき、ワークステーションとサーバーの両方のガベージ コレクションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-114">It can be used for longer periods of time, and is available for both workstation and server garbage collection.</span></span> <span data-ttu-id="a4ec2-115">この設定は、[同時実行ガベージ コレクション](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)が無効の場合には使用できません。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-115">This setting cannot be used if [concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) is disabled.</span></span>  
  
 <span data-ttu-id="a4ec2-116">待機時間の短い設定になっている場合でも、次の状況ではジェネレーション 2 のガベージ コレクションの停止が解除されます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-116">During low latency periods, generation 2 collections are suppressed unless the following occurs:</span></span>  
  
-   <span data-ttu-id="a4ec2-117">システムがオペレーティング システムからメモリ不足の通知を受け取った場合。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-117">The system receives a low memory notification from the operating system.</span></span>  
  
-   <span data-ttu-id="a4ec2-118">アプリケーション コードから <xref:System.GC.Collect%2A?displayProperty=nameWithType> メソッドを呼び出し、`generation` パラメーターに 2 を指定してガベージ コレクションを実行した場合。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-118">Your application code induces a collection by calling the <xref:System.GC.Collect%2A?displayProperty=nameWithType> method and specifying 2 for the `generation` parameter.</span></span>  
  
 <span data-ttu-id="a4ec2-119">次の表に、<xref:System.Runtime.GCLatencyMode> の各値を使用するアプリケーション シナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-119">The following table lists the application scenarios for using the <xref:System.Runtime.GCLatencyMode> values.</span></span>  
  
|<span data-ttu-id="a4ec2-120">待機時間モード</span><span class="sxs-lookup"><span data-stu-id="a4ec2-120">Latency mode</span></span>|<span data-ttu-id="a4ec2-121">アプリケーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="a4ec2-121">Application scenarios</span></span>|  
|------------------|---------------------------|  
|<xref:System.Runtime.GCLatencyMode.Batch>|<span data-ttu-id="a4ec2-122">UI 操作のないアプリケーションの場合、またはサーバー側の操作の場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-122">For applications that have no UI or server-side operations.</span></span><br /><br /> <span data-ttu-id="a4ec2-123">これは、[同時実行ガベージ コレクション](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)が無効の場合の既定モードです。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-123">This is the default mode when [concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) is disabled.</span></span>|  
|<xref:System.Runtime.GCLatencyMode.Interactive>|<span data-ttu-id="a4ec2-124">UI を持つほとんどのアプリケーションの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-124">For most applications that have a UI.</span></span><br /><br /> <span data-ttu-id="a4ec2-125">これは、[同時実行ガベージ コレクション](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)が有効の場合の既定モードです。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-125">This is the default mode when [concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) is enabled.</span></span>|  
|<xref:System.Runtime.GCLatencyMode.LowLatency>|<span data-ttu-id="a4ec2-126">ガベージ コレクターからの割り込みにより重大な影響を受け、高速性を必要とする、短期間の操作を実行するアプリケーションの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-126">For applications that have short-term, time-sensitive operations during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="a4ec2-127">たとえば、アニメーションのレンダリングやデータの取得機能を実行するアプリケーションなどがあります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-127">For example, applications that do animation rendering or data acquisition functions.</span></span>|  
|<xref:System.Runtime.GCLatencyMode.SustainedLowLatency>|<span data-ttu-id="a4ec2-128">ガベージ コレクターからの割り込みにより重大な影響を受け、高速性を必要とする、さほど処理時間を必要としないものの長時間になる可能性のある操作を実行するアプリケーションの場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-128">For applications that have time-sensitive operations for a contained but potentially longer duration of time during which interruptions from the garbage collector could be disruptive.</span></span> <span data-ttu-id="a4ec2-129">たとえば、取引時間中に市場データの変化に応じて迅速な応答時間を必要とするアプリケーションなどがあります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-129">For example, applications that need quick response times as market data changes during trading hours.</span></span><br /><br /> <span data-ttu-id="a4ec2-130">このモードでは、マネージ ヒープのサイズが他のモードより大きくなります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-130">This mode results in a larger managed heap size than other modes.</span></span> <span data-ttu-id="a4ec2-131">マネージ ヒープは最適化されないため、断片化の割合が高くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-131">Because it does not compact the managed heap, higher fragmentation is possible.</span></span> <span data-ttu-id="a4ec2-132">十分なメモリが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-132">Ensure that sufficient memory is available.</span></span>|  
  
## <a name="guidelines-for-using-low-latency"></a><span data-ttu-id="a4ec2-133">待機時間の短いモードの使用に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="a4ec2-133">Guidelines for Using Low Latency</span></span>  
 <span data-ttu-id="a4ec2-134"><xref:System.Runtime.GCLatencyMode.LowLatency> モードを使用する場合は、次のガイドラインを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-134">When you use <xref:System.Runtime.GCLatencyMode.LowLatency> mode, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="a4ec2-135">待機時間を短くする期間は、できるだけ短くします。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-135">Keep the period of time in low latency as short as possible.</span></span>  
  
-   <span data-ttu-id="a4ec2-136">待機時間を短くする期間中は、大量のメモリを割り当てないようにします。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-136">Avoid allocating high amounts of memory during low latency periods.</span></span> <span data-ttu-id="a4ec2-137">ガベージ コレクションによって再利用されるオブジェクトの数が少なくなるため、メモリ不足の通知が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-137">Low memory notifications can occur because garbage collection reclaims fewer objects.</span></span>  
  
-   <span data-ttu-id="a4ec2-138">待機時間の短いモードの間は、割り当ての数、特に大きなオブジェクト ヒープや固定されたオブジェクトへの割り当ての数を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-138">While in the low latency mode, minimize the number of allocations you make, in particular allocations onto the Large Object Heap and pinned objects.</span></span>  
  
-   <span data-ttu-id="a4ec2-139">割り当てられる可能性のあるスレッドに注意します。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-139">Be aware of threads that could be allocating.</span></span> <span data-ttu-id="a4ec2-140"><xref:System.Runtime.GCSettings.LatencyMode%2A> プロパティの設定はプロセス全体に適用されるため、割り当てられた他のスレッドで <xref:System.OutOfMemoryException> が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-140">Because the <xref:System.Runtime.GCSettings.LatencyMode%2A> property setting is process-wide, you could generate an <xref:System.OutOfMemoryException> on any thread that may be allocating.</span></span>  
  
-   <span data-ttu-id="a4ec2-141">制約された実行領域で、待機時間の短いコードを折り返す (詳細については、次を参照してください。[制約された実行領域](../../../docs/framework/performance/constrained-execution-regions.md))。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-141">Wrap the low latency code in constrained execution regions (for more information, see [Constrained Execution Regions](../../../docs/framework/performance/constrained-execution-regions.md)).</span></span>  
  
-   <span data-ttu-id="a4ec2-142">待機時間を短くする期間中でも、<xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> メソッドを呼び出せばジェネレーション 2 のガベージ コレクションを強制できます。</span><span class="sxs-lookup"><span data-stu-id="a4ec2-142">You can force generation 2 collections during a low latency period by calling the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%29?displayProperty=nameWithType> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ec2-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4ec2-143">See Also</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
 [<span data-ttu-id="a4ec2-144">発生したコレクション</span><span class="sxs-lookup"><span data-stu-id="a4ec2-144">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)  
 [<span data-ttu-id="a4ec2-145">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="a4ec2-145">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
