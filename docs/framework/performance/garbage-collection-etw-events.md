---
title: "ガベージ コレクション ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 06fc335e4b8011afd92e698b20e4b84572b153c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="90f2d-102">ガベージ コレクション ETW イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="90f2d-103">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="90f2d-104">ガベージ コレクションが実行された回数、ガベージ コレクションの間に解放されたメモリの量など、診断やデバッグに役立つ情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="90f2d-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="90f2d-105">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="90f2d-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="90f2d-106">GCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="90f2d-107">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="90f2d-108">GCHeapStats_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="90f2d-109">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="90f2d-110">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="90f2d-111">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="90f2d-112">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="90f2d-113">GCSuspendEE_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="90f2d-114">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="90f2d-115">GCAllocationTick_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="90f2d-116">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="90f2d-117">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="90f2d-118">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="90f2d-119">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="90f2d-120">GCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="90f2d-121">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="90f2d-122">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="90f2d-123">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-123">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-124">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-127">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-128">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-128">Event</span></span>|<span data-ttu-id="90f2d-129">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-129">Event ID</span></span>|<span data-ttu-id="90f2d-130">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="90f2d-131">1</span><span class="sxs-lookup"><span data-stu-id="90f2d-131">1</span></span>|<span data-ttu-id="90f2d-132">ガベージ コレクションが開始されました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="90f2d-133">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-134">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-134">Field name</span></span>|<span data-ttu-id="90f2d-135">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-135">Data type</span></span>|<span data-ttu-id="90f2d-136">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-137">カウント</span><span class="sxs-lookup"><span data-stu-id="90f2d-137">Count</span></span>|<span data-ttu-id="90f2d-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-138">win:UInt32</span></span>|<span data-ttu-id="90f2d-139">*n* 回目のガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="90f2d-140">奥行</span><span class="sxs-lookup"><span data-stu-id="90f2d-140">Depth</span></span>|<span data-ttu-id="90f2d-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-141">win:UInt32</span></span>|<span data-ttu-id="90f2d-142">収集されるジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="90f2d-143">理由</span><span class="sxs-lookup"><span data-stu-id="90f2d-143">Reason</span></span>|<span data-ttu-id="90f2d-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-144">win:UInt32</span></span>|<span data-ttu-id="90f2d-145">ガベージ コレクションが発生した理由:</span><span class="sxs-lookup"><span data-stu-id="90f2d-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="90f2d-146">0x0 - 小さなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="90f2d-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="90f2d-147">0x1 - 強制実行。</span><span class="sxs-lookup"><span data-stu-id="90f2d-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="90f2d-148">0x2 - メモリ不足。</span><span class="sxs-lookup"><span data-stu-id="90f2d-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="90f2d-149">0x3 - 空。</span><span class="sxs-lookup"><span data-stu-id="90f2d-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="90f2d-150">0x4 - 大きなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="90f2d-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="90f2d-151">0x5 - 領域不足 (小さなオブジェクト ヒープが対象)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="90f2d-152">0x6 - 領域不足 (大きなオブジェクト ヒープが対象)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="90f2d-153">0x7 - 強制実行されるが、ブロッキングとして強制されない。</span><span class="sxs-lookup"><span data-stu-id="90f2d-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="90f2d-154">型</span><span class="sxs-lookup"><span data-stu-id="90f2d-154">Type</span></span>|<span data-ttu-id="90f2d-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-155">win:UInt32</span></span>|<span data-ttu-id="90f2d-156">0x0 - バックグラウンド ガベージ コレクションの外部で発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="90f2d-157">0x1 - バックグラウンド ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="90f2d-158">0x2 - バックグラウンド ガベージ コレクションの実行中に発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="90f2d-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-159">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-160">win:UInt16</span></span>|<span data-ttu-id="90f2d-161">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90f2d-162">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="90f2d-163">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="90f2d-164">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-165">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-165">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-166">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-168">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-169">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-170">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-170">Event</span></span>|<span data-ttu-id="90f2d-171">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-171">Event ID</span></span>|<span data-ttu-id="90f2d-172">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="90f2d-173">2</span><span class="sxs-lookup"><span data-stu-id="90f2d-173">2</span></span>|<span data-ttu-id="90f2d-174">ガベージ コレクションが終了しました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="90f2d-175">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-176">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-176">Field name</span></span>|<span data-ttu-id="90f2d-177">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-177">Data type</span></span>|<span data-ttu-id="90f2d-178">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-179">カウント</span><span class="sxs-lookup"><span data-stu-id="90f2d-179">Count</span></span>|<span data-ttu-id="90f2d-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-180">win:UInt32</span></span>|<span data-ttu-id="90f2d-181">*n* 回目のガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="90f2d-182">奥行</span><span class="sxs-lookup"><span data-stu-id="90f2d-182">Depth</span></span>|<span data-ttu-id="90f2d-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-183">win:UInt32</span></span>|<span data-ttu-id="90f2d-184">収集されたジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="90f2d-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-185">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-186">win:UInt16</span></span>|<span data-ttu-id="90f2d-187">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90f2d-188">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="90f2d-189">GCHeapStats_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="90f2d-190">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-191">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-191">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-192">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-194">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-195">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-196">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-196">Event</span></span>|<span data-ttu-id="90f2d-197">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-197">Event ID</span></span>|<span data-ttu-id="90f2d-198">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="90f2d-199">4</span><span class="sxs-lookup"><span data-stu-id="90f2d-199">4</span></span>|<span data-ttu-id="90f2d-200">各ガベージ コレクション終了時のヒープの統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="90f2d-201">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-202">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-202">Field name</span></span>|<span data-ttu-id="90f2d-203">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-203">Data type</span></span>|<span data-ttu-id="90f2d-204">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="90f2d-205">GenerationSize0</span></span>|<span data-ttu-id="90f2d-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-206">win:UInt64</span></span>|<span data-ttu-id="90f2d-207">ジェネレーション 0 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="90f2d-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="90f2d-208">TotalPromotedSize0</span></span>|<span data-ttu-id="90f2d-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-209">win:UInt64</span></span>|<span data-ttu-id="90f2d-210">ジェネレーション 0 からジェネレーション 1 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="90f2d-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="90f2d-211">GenerationSize1</span></span>|<span data-ttu-id="90f2d-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-212">win:UInt64</span></span>|<span data-ttu-id="90f2d-213">ジェネレーション 1 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="90f2d-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="90f2d-214">TotalPromotedSize1</span></span>|<span data-ttu-id="90f2d-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-215">win:UInt64</span></span>|<span data-ttu-id="90f2d-216">ジェネレーション 1 からジェネレーション 2 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="90f2d-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="90f2d-217">GenerationSize2</span></span>|<span data-ttu-id="90f2d-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-218">win:UInt64</span></span>|<span data-ttu-id="90f2d-219">ジェネレーション 2 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="90f2d-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="90f2d-220">TotalPromotedSize2</span></span>|<span data-ttu-id="90f2d-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-221">win:UInt64</span></span>|<span data-ttu-id="90f2d-222">最後のガベージ コレクションの後にジェネレーション 2 に残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="90f2d-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="90f2d-223">GenerationSize3</span></span>|<span data-ttu-id="90f2d-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-224">win:UInt64</span></span>|<span data-ttu-id="90f2d-225">大きなオブジェクト ヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="90f2d-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="90f2d-226">TotalPromotedSize3</span></span>|<span data-ttu-id="90f2d-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-227">win:UInt64</span></span>|<span data-ttu-id="90f2d-228">最後のガベージ コレクションの後に大きなオブジェクト ヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="90f2d-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="90f2d-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="90f2d-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-230">win:UInt64</span></span>|<span data-ttu-id="90f2d-231">終了準備が完了しているオブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="90f2d-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="90f2d-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="90f2d-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-233">win:UInt64</span></span>|<span data-ttu-id="90f2d-234">終了準備が完了しているオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="90f2d-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="90f2d-235">PinnedObjectCount</span></span>|<span data-ttu-id="90f2d-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-236">win:UInt32</span></span>|<span data-ttu-id="90f2d-237">ピン止めオブジェクト (移動できないオブジェクト) の数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="90f2d-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="90f2d-238">SinkBlockCount</span></span>|<span data-ttu-id="90f2d-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-239">win:UInt32</span></span>|<span data-ttu-id="90f2d-240">使用中の同期ブロックの数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="90f2d-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="90f2d-241">GCHandleCount</span></span>|<span data-ttu-id="90f2d-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-242">win:UInt32</span></span>|<span data-ttu-id="90f2d-243">使用中のガベージ コレクション ハンドルの数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="90f2d-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-244">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-245">win:UInt16</span></span>|<span data-ttu-id="90f2d-246">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90f2d-247">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="90f2d-248">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="90f2d-249">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-250">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-250">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-251">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-253">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-254">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-255">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-255">Event</span></span>|<span data-ttu-id="90f2d-256">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-256">Event ID</span></span>|<span data-ttu-id="90f2d-257">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="90f2d-258">5</span><span class="sxs-lookup"><span data-stu-id="90f2d-258">5</span></span>|<span data-ttu-id="90f2d-259">新しいガベージ コレクション セグメントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="90f2d-260">既に実行されているプロセスでトレースを有効にした場合は、このイベントが各既存セグメントについて発生します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="90f2d-261">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-262">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-262">Field name</span></span>|<span data-ttu-id="90f2d-263">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-263">Data type</span></span>|<span data-ttu-id="90f2d-264">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-265">アドレス</span><span class="sxs-lookup"><span data-stu-id="90f2d-265">Address</span></span>|<span data-ttu-id="90f2d-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-266">win:UInt64</span></span>|<span data-ttu-id="90f2d-267">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="90f2d-267">The address of the segment.</span></span>|  
|<span data-ttu-id="90f2d-268">サイズ</span><span class="sxs-lookup"><span data-stu-id="90f2d-268">Size</span></span>|<span data-ttu-id="90f2d-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-269">win:UInt64</span></span>|<span data-ttu-id="90f2d-270">セグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="90f2d-270">The size of the segment.</span></span>|  
|<span data-ttu-id="90f2d-271">型</span><span class="sxs-lookup"><span data-stu-id="90f2d-271">Type</span></span>|<span data-ttu-id="90f2d-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-272">win:UInt32</span></span>|<span data-ttu-id="90f2d-273">0x0 - 小さなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="90f2d-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="90f2d-274">0x1 - 大きなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="90f2d-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="90f2d-275">0x2 - 読み取り専用ヒープ。</span><span class="sxs-lookup"><span data-stu-id="90f2d-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="90f2d-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-276">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-277">win:UInt16</span></span>|<span data-ttu-id="90f2d-278">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="90f2d-279">ガベージ コレクターによって割り当てられるセグメントのサイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="90f2d-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="90f2d-280">アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="90f2d-281">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="90f2d-282">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="90f2d-283">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-284">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-284">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-285">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-287">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-288">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-289">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-289">Event</span></span>|<span data-ttu-id="90f2d-290">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-290">Event ID</span></span>|<span data-ttu-id="90f2d-291">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="90f2d-292">6</span><span class="sxs-lookup"><span data-stu-id="90f2d-292">6</span></span>|<span data-ttu-id="90f2d-293">ガベージ コレクション セグメントが解放されました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="90f2d-294">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-295">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-295">Field name</span></span>|<span data-ttu-id="90f2d-296">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-296">Data type</span></span>|<span data-ttu-id="90f2d-297">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-298">アドレス</span><span class="sxs-lookup"><span data-stu-id="90f2d-298">Address</span></span>|<span data-ttu-id="90f2d-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-299">win:UInt64</span></span>|<span data-ttu-id="90f2d-300">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="90f2d-300">The address of the segment.</span></span>|  
|<span data-ttu-id="90f2d-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-301">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-302">win:UInt16</span></span>|<span data-ttu-id="90f2d-303">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90f2d-304">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="90f2d-305">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="90f2d-306">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-307">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-307">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-308">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-310">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-311">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-312">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-312">Event</span></span>|<span data-ttu-id="90f2d-313">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-313">Event ID</span></span>|<span data-ttu-id="90f2d-314">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="90f2d-315">7</span><span class="sxs-lookup"><span data-stu-id="90f2d-315">7</span></span>|<span data-ttu-id="90f2d-316">共通言語ランタイムの中断からの再開が開始されました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="90f2d-317">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-317">No event data.</span></span>  
  
 [<span data-ttu-id="90f2d-318">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="90f2d-319">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="90f2d-320">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-321">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-321">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-322">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-324">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-325">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-326">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-326">Event</span></span>|<span data-ttu-id="90f2d-327">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-327">Event Id</span></span>|<span data-ttu-id="90f2d-328">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="90f2d-329">3</span><span class="sxs-lookup"><span data-stu-id="90f2d-329">3</span></span>|<span data-ttu-id="90f2d-330">共通言語ランタイムの中断からの再開が終了しました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="90f2d-331">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-331">No event data.</span></span>  
  
 [<span data-ttu-id="90f2d-332">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="90f2d-333">GCSuspendEE_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="90f2d-334">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-335">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-335">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-336">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-339">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-340">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-340">Event</span></span>|<span data-ttu-id="90f2d-341">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-341">Event ID</span></span>|<span data-ttu-id="90f2d-342">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="90f2d-343">9</span><span class="sxs-lookup"><span data-stu-id="90f2d-343">9</span></span>|<span data-ttu-id="90f2d-344">ガベージ コレクションのための実行エンジンの中断の開始。</span><span class="sxs-lookup"><span data-stu-id="90f2d-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="90f2d-345">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-346">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-346">Field name</span></span>|<span data-ttu-id="90f2d-347">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-347">Data type</span></span>|<span data-ttu-id="90f2d-348">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-349">理由</span><span class="sxs-lookup"><span data-stu-id="90f2d-349">Reason</span></span>|<span data-ttu-id="90f2d-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-350">win:UInt16</span></span>|<span data-ttu-id="90f2d-351">0x0 - その他。</span><span class="sxs-lookup"><span data-stu-id="90f2d-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="90f2d-352">0x1 - ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="90f2d-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="90f2d-353">0x2 - アプリケーション ドメインのシャットダウン。</span><span class="sxs-lookup"><span data-stu-id="90f2d-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="90f2d-354">0x3 - コード ピッチ。</span><span class="sxs-lookup"><span data-stu-id="90f2d-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="90f2d-355">0x4 - シャットダウン。</span><span class="sxs-lookup"><span data-stu-id="90f2d-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="90f2d-356">0x5 - デバッガー。</span><span class="sxs-lookup"><span data-stu-id="90f2d-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="90f2d-357">0x6 - ガベージ コレクションの準備。</span><span class="sxs-lookup"><span data-stu-id="90f2d-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="90f2d-358">カウント</span><span class="sxs-lookup"><span data-stu-id="90f2d-358">Count</span></span>|<span data-ttu-id="90f2d-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-359">win:UInt32</span></span>|<span data-ttu-id="90f2d-360">その時点の GC カウント。</span><span class="sxs-lookup"><span data-stu-id="90f2d-360">The GC count at the time.</span></span> <span data-ttu-id="90f2d-361">通常、この後に後続の GC 開始イベントが表示され、そのカウントは、ガベージ コレクション中に、GC インデックスが増えるため、このカウント + 1 になります。</span><span class="sxs-lookup"><span data-stu-id="90f2d-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="90f2d-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-362">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-363">win:UInt16</span></span>|<span data-ttu-id="90f2d-364">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90f2d-365">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="90f2d-366">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="90f2d-367">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="90f2d-368">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-368">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-369">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-371">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-372">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="90f2d-373">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-373">Event</span></span>|<span data-ttu-id="90f2d-374">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-374">Event ID</span></span>|<span data-ttu-id="90f2d-375">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="90f2d-376">9</span><span class="sxs-lookup"><span data-stu-id="90f2d-376">8</span></span>|<span data-ttu-id="90f2d-377">ガベージ コレクションのための実行エンジンの中断の終了。</span><span class="sxs-lookup"><span data-stu-id="90f2d-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="90f2d-378">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-378">No event data.</span></span>  
  
 [<span data-ttu-id="90f2d-379">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="90f2d-380">GCAllocationTick_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="90f2d-381">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-382">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-382">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-383">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-385">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-386">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-387">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-387">Event</span></span>|<span data-ttu-id="90f2d-388">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-388">Event ID</span></span>|<span data-ttu-id="90f2d-389">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="90f2d-390">10</span><span class="sxs-lookup"><span data-stu-id="90f2d-390">10</span></span>|<span data-ttu-id="90f2d-391">約 100 KB が割り当てられるたび。</span><span class="sxs-lookup"><span data-stu-id="90f2d-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="90f2d-392">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-393">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-393">Field name</span></span>|<span data-ttu-id="90f2d-394">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-394">Data type</span></span>|<span data-ttu-id="90f2d-395">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="90f2d-396">AllocationAmount</span></span>|<span data-ttu-id="90f2d-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-397">win:UInt32</span></span>|<span data-ttu-id="90f2d-398">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-398">The allocation size, in bytes.</span></span> <span data-ttu-id="90f2d-399">この値は、ULONG (4,294,967,295 バイト) の長さより短い割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="90f2d-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="90f2d-400">割り当てがこれを超える場合、このフィールドには切り捨てられた値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="90f2d-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="90f2d-401">非常に大きな割り当てには `AllocationAmount64` を使用します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="90f2d-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="90f2d-402">AllocationKind</span></span>|<span data-ttu-id="90f2d-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-403">win:UInt32</span></span>|<span data-ttu-id="90f2d-404">0x0 - 小さなオブジェクトの割り当て (小さなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="90f2d-405">0x1 - 大きなオブジェクトの割り当て (大きなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="90f2d-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-406">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-407">win:UInt16</span></span>|<span data-ttu-id="90f2d-408">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="90f2d-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="90f2d-409">AllocationAmount64</span></span>|<span data-ttu-id="90f2d-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90f2d-410">win:UInt64</span></span>|<span data-ttu-id="90f2d-411">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="90f2d-411">The allocation size, in bytes.</span></span> <span data-ttu-id="90f2d-412">この値は非常に大きな割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="90f2d-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="90f2d-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="90f2d-413">TypeId</span></span>|<span data-ttu-id="90f2d-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="90f2d-414">win:Pointer</span></span>|<span data-ttu-id="90f2d-415">MethodTable のアドレス。</span><span class="sxs-lookup"><span data-stu-id="90f2d-415">The address of the MethodTable.</span></span> <span data-ttu-id="90f2d-416">このイベント中に複数の型のオブジェクトが割り当てられた場合、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) に対応する MethodTable のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="90f2d-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="90f2d-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="90f2d-417">TypeName</span></span>|<span data-ttu-id="90f2d-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90f2d-418">win:UnicodeString</span></span>|<span data-ttu-id="90f2d-419">割り当てられた型の名前。</span><span class="sxs-lookup"><span data-stu-id="90f2d-419">The name of the type that was allocated.</span></span> <span data-ttu-id="90f2d-420">このイベント中に複数の型のオブジェクトが割り当てられた場合は、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) の型です。</span><span class="sxs-lookup"><span data-stu-id="90f2d-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="90f2d-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="90f2d-421">HeapIndex</span></span>|<span data-ttu-id="90f2d-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-422">win:UInt32</span></span>|<span data-ttu-id="90f2d-423">オブジェクトが割り当てられたヒープ。</span><span class="sxs-lookup"><span data-stu-id="90f2d-423">The heap where the object was allocated.</span></span> <span data-ttu-id="90f2d-424">ワークステーションのガベージ コレクションと共に実行する場合、この値は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="90f2d-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="90f2d-425">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="90f2d-426">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="90f2d-427">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-428">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-428">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-429">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-431">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-432">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-433">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-433">Event</span></span>|<span data-ttu-id="90f2d-434">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-434">Event ID</span></span>|<span data-ttu-id="90f2d-435">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="90f2d-436">14</span><span class="sxs-lookup"><span data-stu-id="90f2d-436">14</span></span>|<span data-ttu-id="90f2d-437">ファイナライザーの実行の開始。</span><span class="sxs-lookup"><span data-stu-id="90f2d-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="90f2d-438">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-438">No event data.</span></span>  
  
 [<span data-ttu-id="90f2d-439">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="90f2d-440">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="90f2d-441">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-442">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-442">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-443">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-445">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-446">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-447">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-447">Event</span></span>|<span data-ttu-id="90f2d-448">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-448">Event ID</span></span>|<span data-ttu-id="90f2d-449">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="90f2d-450">13</span><span class="sxs-lookup"><span data-stu-id="90f2d-450">13</span></span>|<span data-ttu-id="90f2d-451">ファイナライザーの実行の終了。</span><span class="sxs-lookup"><span data-stu-id="90f2d-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="90f2d-452">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90f2d-453">フィールド名</span><span class="sxs-lookup"><span data-stu-id="90f2d-453">Field name</span></span>|<span data-ttu-id="90f2d-454">データ型</span><span class="sxs-lookup"><span data-stu-id="90f2d-454">Data type</span></span>|<span data-ttu-id="90f2d-455">説明</span><span class="sxs-lookup"><span data-stu-id="90f2d-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90f2d-456">カウント</span><span class="sxs-lookup"><span data-stu-id="90f2d-456">Count</span></span>|<span data-ttu-id="90f2d-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90f2d-457">win:UInt32</span></span>|<span data-ttu-id="90f2d-458">実行されたファイナライザーの数。</span><span class="sxs-lookup"><span data-stu-id="90f2d-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="90f2d-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90f2d-459">ClrInstanceID</span></span>|<span data-ttu-id="90f2d-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90f2d-460">win:UInt16</span></span>|<span data-ttu-id="90f2d-461">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="90f2d-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90f2d-462">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="90f2d-463">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="90f2d-464">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-465">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-465">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-466">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-468">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-468">Informational (4)</span></span>|  
|<span data-ttu-id="90f2d-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="90f2d-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="90f2d-470">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-471">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-472">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-472">Event</span></span>|<span data-ttu-id="90f2d-473">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-473">Event ID</span></span>|<span data-ttu-id="90f2d-474">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="90f2d-475">11</span><span class="sxs-lookup"><span data-stu-id="90f2d-475">11</span></span>|<span data-ttu-id="90f2d-476">同時実行ガベージ コレクション スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="90f2d-477">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-477">No event data.</span></span>  
  
 [<span data-ttu-id="90f2d-478">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="90f2d-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="90f2d-479">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="90f2d-480">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90f2d-481">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="90f2d-481">Keyword for raising the event</span></span>|<span data-ttu-id="90f2d-482">レベル</span><span class="sxs-lookup"><span data-stu-id="90f2d-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90f2d-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="90f2d-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="90f2d-484">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-484">Informational (4)</span></span>|  
|<span data-ttu-id="90f2d-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="90f2d-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="90f2d-486">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="90f2d-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="90f2d-487">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="90f2d-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90f2d-488">イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-488">Event</span></span>|<span data-ttu-id="90f2d-489">イベント ID</span><span class="sxs-lookup"><span data-stu-id="90f2d-489">Event ID</span></span>|<span data-ttu-id="90f2d-490">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="90f2d-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="90f2d-491">12</span><span class="sxs-lookup"><span data-stu-id="90f2d-491">12</span></span>|<span data-ttu-id="90f2d-492">同時実行ガベージ コレクションスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="90f2d-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="90f2d-493">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="90f2d-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f2d-494">関連項目</span><span class="sxs-lookup"><span data-stu-id="90f2d-494">See Also</span></span>  
 [<span data-ttu-id="90f2d-495">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="90f2d-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
