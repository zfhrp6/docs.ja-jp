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
ms.workload: dotnet
ms.openlocfilehash: 133d48baa9613ea698b6d6a21f0dfe88a798859c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="029ff-102">ガベージ コレクション ETW イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="029ff-103">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="029ff-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="029ff-104">ガベージ コレクションが実行された回数、ガベージ コレクションの間に解放されたメモリの量など、診断やデバッグに役立つ情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="029ff-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="029ff-105">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="029ff-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="029ff-106">GCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="029ff-107">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="029ff-108">GCHeapStats_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="029ff-109">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="029ff-110">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="029ff-111">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="029ff-112">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="029ff-113">GCSuspendEE_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="029ff-114">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="029ff-115">GCAllocationTick_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="029ff-116">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="029ff-117">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="029ff-118">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="029ff-119">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="029ff-120">GCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="029ff-121">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="029ff-122">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="029ff-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="029ff-123">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-123">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-124">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-127">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-128">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-128">Event</span></span>|<span data-ttu-id="029ff-129">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-129">Event ID</span></span>|<span data-ttu-id="029ff-130">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="029ff-131">1</span><span class="sxs-lookup"><span data-stu-id="029ff-131">1</span></span>|<span data-ttu-id="029ff-132">ガベージ コレクションが開始されました。</span><span class="sxs-lookup"><span data-stu-id="029ff-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="029ff-133">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-134">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-134">Field name</span></span>|<span data-ttu-id="029ff-135">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-135">Data type</span></span>|<span data-ttu-id="029ff-136">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-137">カウント</span><span class="sxs-lookup"><span data-stu-id="029ff-137">Count</span></span>|<span data-ttu-id="029ff-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-138">win:UInt32</span></span>|<span data-ttu-id="029ff-139">*n* 回目のガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="029ff-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="029ff-140">奥行</span><span class="sxs-lookup"><span data-stu-id="029ff-140">Depth</span></span>|<span data-ttu-id="029ff-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-141">win:UInt32</span></span>|<span data-ttu-id="029ff-142">収集されるジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="029ff-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="029ff-143">理由</span><span class="sxs-lookup"><span data-stu-id="029ff-143">Reason</span></span>|<span data-ttu-id="029ff-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-144">win:UInt32</span></span>|<span data-ttu-id="029ff-145">ガベージ コレクションが発生した理由:</span><span class="sxs-lookup"><span data-stu-id="029ff-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="029ff-146">0x0 - 小さなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="029ff-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="029ff-147">0x1 - 強制実行。</span><span class="sxs-lookup"><span data-stu-id="029ff-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="029ff-148">0x2 - メモリ不足。</span><span class="sxs-lookup"><span data-stu-id="029ff-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="029ff-149">0x3 - 空。</span><span class="sxs-lookup"><span data-stu-id="029ff-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="029ff-150">0x4 - 大きなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="029ff-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="029ff-151">0x5 - 領域不足 (小さなオブジェクト ヒープが対象)。</span><span class="sxs-lookup"><span data-stu-id="029ff-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="029ff-152">0x6 - 領域不足 (大きなオブジェクト ヒープが対象)。</span><span class="sxs-lookup"><span data-stu-id="029ff-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="029ff-153">0x7 - 強制実行されるが、ブロッキングとして強制されない。</span><span class="sxs-lookup"><span data-stu-id="029ff-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="029ff-154">型</span><span class="sxs-lookup"><span data-stu-id="029ff-154">Type</span></span>|<span data-ttu-id="029ff-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-155">win:UInt32</span></span>|<span data-ttu-id="029ff-156">0x0 - バックグラウンド ガベージ コレクションの外部で発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="029ff-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="029ff-157">0x1 - バックグラウンド ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="029ff-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="029ff-158">0x2 - バックグラウンド ガベージ コレクションの実行中に発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="029ff-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="029ff-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-159">ClrInstanceID</span></span>|<span data-ttu-id="029ff-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-160">win:UInt16</span></span>|<span data-ttu-id="029ff-161">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="029ff-162">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="029ff-163">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="029ff-164">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-165">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-165">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-166">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-168">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-169">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-170">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-170">Event</span></span>|<span data-ttu-id="029ff-171">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-171">Event ID</span></span>|<span data-ttu-id="029ff-172">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="029ff-173">2</span><span class="sxs-lookup"><span data-stu-id="029ff-173">2</span></span>|<span data-ttu-id="029ff-174">ガベージ コレクションが終了しました。</span><span class="sxs-lookup"><span data-stu-id="029ff-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="029ff-175">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-176">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-176">Field name</span></span>|<span data-ttu-id="029ff-177">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-177">Data type</span></span>|<span data-ttu-id="029ff-178">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-179">カウント</span><span class="sxs-lookup"><span data-stu-id="029ff-179">Count</span></span>|<span data-ttu-id="029ff-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-180">win:UInt32</span></span>|<span data-ttu-id="029ff-181">*n* 回目のガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="029ff-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="029ff-182">奥行</span><span class="sxs-lookup"><span data-stu-id="029ff-182">Depth</span></span>|<span data-ttu-id="029ff-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-183">win:UInt32</span></span>|<span data-ttu-id="029ff-184">収集されたジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="029ff-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="029ff-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-185">ClrInstanceID</span></span>|<span data-ttu-id="029ff-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-186">win:UInt16</span></span>|<span data-ttu-id="029ff-187">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="029ff-188">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="029ff-189">GCHeapStats_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="029ff-190">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-191">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-191">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-192">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-194">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-195">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-196">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-196">Event</span></span>|<span data-ttu-id="029ff-197">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-197">Event ID</span></span>|<span data-ttu-id="029ff-198">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="029ff-199">4</span><span class="sxs-lookup"><span data-stu-id="029ff-199">4</span></span>|<span data-ttu-id="029ff-200">各ガベージ コレクション終了時のヒープの統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="029ff-201">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-202">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-202">Field name</span></span>|<span data-ttu-id="029ff-203">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-203">Data type</span></span>|<span data-ttu-id="029ff-204">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="029ff-205">GenerationSize0</span></span>|<span data-ttu-id="029ff-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-206">win:UInt64</span></span>|<span data-ttu-id="029ff-207">ジェネレーション 0 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="029ff-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="029ff-208">TotalPromotedSize0</span></span>|<span data-ttu-id="029ff-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-209">win:UInt64</span></span>|<span data-ttu-id="029ff-210">ジェネレーション 0 からジェネレーション 1 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="029ff-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="029ff-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="029ff-211">GenerationSize1</span></span>|<span data-ttu-id="029ff-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-212">win:UInt64</span></span>|<span data-ttu-id="029ff-213">ジェネレーション 1 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="029ff-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="029ff-214">TotalPromotedSize1</span></span>|<span data-ttu-id="029ff-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-215">win:UInt64</span></span>|<span data-ttu-id="029ff-216">ジェネレーション 1 からジェネレーション 2 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="029ff-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="029ff-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="029ff-217">GenerationSize2</span></span>|<span data-ttu-id="029ff-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-218">win:UInt64</span></span>|<span data-ttu-id="029ff-219">ジェネレーション 2 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="029ff-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="029ff-220">TotalPromotedSize2</span></span>|<span data-ttu-id="029ff-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-221">win:UInt64</span></span>|<span data-ttu-id="029ff-222">最後のガベージ コレクションの後にジェネレーション 2 に残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="029ff-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="029ff-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="029ff-223">GenerationSize3</span></span>|<span data-ttu-id="029ff-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-224">win:UInt64</span></span>|<span data-ttu-id="029ff-225">大きなオブジェクト ヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="029ff-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="029ff-226">TotalPromotedSize3</span></span>|<span data-ttu-id="029ff-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-227">win:UInt64</span></span>|<span data-ttu-id="029ff-228">最後のガベージ コレクションの後に大きなオブジェクト ヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="029ff-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="029ff-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="029ff-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="029ff-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-230">win:UInt64</span></span>|<span data-ttu-id="029ff-231">終了準備が完了しているオブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="029ff-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="029ff-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="029ff-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-233">win:UInt64</span></span>|<span data-ttu-id="029ff-234">終了準備が完了しているオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="029ff-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="029ff-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="029ff-235">PinnedObjectCount</span></span>|<span data-ttu-id="029ff-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-236">win:UInt32</span></span>|<span data-ttu-id="029ff-237">ピン止めオブジェクト (移動できないオブジェクト) の数。</span><span class="sxs-lookup"><span data-stu-id="029ff-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="029ff-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="029ff-238">SinkBlockCount</span></span>|<span data-ttu-id="029ff-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-239">win:UInt32</span></span>|<span data-ttu-id="029ff-240">使用中の同期ブロックの数。</span><span class="sxs-lookup"><span data-stu-id="029ff-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="029ff-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="029ff-241">GCHandleCount</span></span>|<span data-ttu-id="029ff-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-242">win:UInt32</span></span>|<span data-ttu-id="029ff-243">使用中のガベージ コレクション ハンドルの数。</span><span class="sxs-lookup"><span data-stu-id="029ff-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="029ff-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-244">ClrInstanceID</span></span>|<span data-ttu-id="029ff-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-245">win:UInt16</span></span>|<span data-ttu-id="029ff-246">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="029ff-247">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="029ff-248">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="029ff-249">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-250">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-250">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-251">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-253">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-254">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-255">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-255">Event</span></span>|<span data-ttu-id="029ff-256">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-256">Event ID</span></span>|<span data-ttu-id="029ff-257">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="029ff-258">5</span><span class="sxs-lookup"><span data-stu-id="029ff-258">5</span></span>|<span data-ttu-id="029ff-259">新しいガベージ コレクション セグメントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="029ff-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="029ff-260">既に実行されているプロセスでトレースを有効にした場合は、このイベントが各既存セグメントについて発生します。</span><span class="sxs-lookup"><span data-stu-id="029ff-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="029ff-261">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-262">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-262">Field name</span></span>|<span data-ttu-id="029ff-263">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-263">Data type</span></span>|<span data-ttu-id="029ff-264">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-265">アドレス</span><span class="sxs-lookup"><span data-stu-id="029ff-265">Address</span></span>|<span data-ttu-id="029ff-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-266">win:UInt64</span></span>|<span data-ttu-id="029ff-267">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="029ff-267">The address of the segment.</span></span>|  
|<span data-ttu-id="029ff-268">サイズ</span><span class="sxs-lookup"><span data-stu-id="029ff-268">Size</span></span>|<span data-ttu-id="029ff-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-269">win:UInt64</span></span>|<span data-ttu-id="029ff-270">セグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="029ff-270">The size of the segment.</span></span>|  
|<span data-ttu-id="029ff-271">型</span><span class="sxs-lookup"><span data-stu-id="029ff-271">Type</span></span>|<span data-ttu-id="029ff-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-272">win:UInt32</span></span>|<span data-ttu-id="029ff-273">0x0 - 小さなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="029ff-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="029ff-274">0x1 - 大きなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="029ff-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="029ff-275">0x2 - 読み取り専用ヒープ。</span><span class="sxs-lookup"><span data-stu-id="029ff-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="029ff-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-276">ClrInstanceID</span></span>|<span data-ttu-id="029ff-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-277">win:UInt16</span></span>|<span data-ttu-id="029ff-278">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="029ff-279">ガベージ コレクターによって割り当てられるセグメントのサイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="029ff-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="029ff-280">アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。</span><span class="sxs-lookup"><span data-stu-id="029ff-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="029ff-281">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="029ff-282">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="029ff-283">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-284">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-284">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-285">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-287">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-288">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-289">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-289">Event</span></span>|<span data-ttu-id="029ff-290">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-290">Event ID</span></span>|<span data-ttu-id="029ff-291">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="029ff-292">6</span><span class="sxs-lookup"><span data-stu-id="029ff-292">6</span></span>|<span data-ttu-id="029ff-293">ガベージ コレクション セグメントが解放されました。</span><span class="sxs-lookup"><span data-stu-id="029ff-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="029ff-294">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-295">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-295">Field name</span></span>|<span data-ttu-id="029ff-296">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-296">Data type</span></span>|<span data-ttu-id="029ff-297">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-298">アドレス</span><span class="sxs-lookup"><span data-stu-id="029ff-298">Address</span></span>|<span data-ttu-id="029ff-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-299">win:UInt64</span></span>|<span data-ttu-id="029ff-300">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="029ff-300">The address of the segment.</span></span>|  
|<span data-ttu-id="029ff-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-301">ClrInstanceID</span></span>|<span data-ttu-id="029ff-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-302">win:UInt16</span></span>|<span data-ttu-id="029ff-303">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="029ff-304">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="029ff-305">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="029ff-306">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-307">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-307">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-308">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-310">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-311">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-312">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-312">Event</span></span>|<span data-ttu-id="029ff-313">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-313">Event ID</span></span>|<span data-ttu-id="029ff-314">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="029ff-315">7</span><span class="sxs-lookup"><span data-stu-id="029ff-315">7</span></span>|<span data-ttu-id="029ff-316">共通言語ランタイムの中断からの再開が開始されました。</span><span class="sxs-lookup"><span data-stu-id="029ff-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="029ff-317">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="029ff-317">No event data.</span></span>  
  
 [<span data-ttu-id="029ff-318">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="029ff-319">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="029ff-320">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-321">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-321">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-322">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-324">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-325">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-326">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-326">Event</span></span>|<span data-ttu-id="029ff-327">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-327">Event Id</span></span>|<span data-ttu-id="029ff-328">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="029ff-329">3</span><span class="sxs-lookup"><span data-stu-id="029ff-329">3</span></span>|<span data-ttu-id="029ff-330">共通言語ランタイムの中断からの再開が終了しました。</span><span class="sxs-lookup"><span data-stu-id="029ff-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="029ff-331">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="029ff-331">No event data.</span></span>  
  
 [<span data-ttu-id="029ff-332">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="029ff-333">GCSuspendEE_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="029ff-334">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-335">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-335">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-336">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-339">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-340">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-340">Event</span></span>|<span data-ttu-id="029ff-341">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-341">Event ID</span></span>|<span data-ttu-id="029ff-342">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="029ff-343">9</span><span class="sxs-lookup"><span data-stu-id="029ff-343">9</span></span>|<span data-ttu-id="029ff-344">ガベージ コレクションのための実行エンジンの中断の開始。</span><span class="sxs-lookup"><span data-stu-id="029ff-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="029ff-345">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-346">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-346">Field name</span></span>|<span data-ttu-id="029ff-347">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-347">Data type</span></span>|<span data-ttu-id="029ff-348">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-349">理由</span><span class="sxs-lookup"><span data-stu-id="029ff-349">Reason</span></span>|<span data-ttu-id="029ff-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-350">win:UInt16</span></span>|<span data-ttu-id="029ff-351">0x0 - その他。</span><span class="sxs-lookup"><span data-stu-id="029ff-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="029ff-352">0x1 - ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="029ff-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="029ff-353">0x2 - アプリケーション ドメインのシャットダウン。</span><span class="sxs-lookup"><span data-stu-id="029ff-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="029ff-354">0x3 - コード ピッチ。</span><span class="sxs-lookup"><span data-stu-id="029ff-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="029ff-355">0x4 - シャットダウン。</span><span class="sxs-lookup"><span data-stu-id="029ff-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="029ff-356">0x5 - デバッガー。</span><span class="sxs-lookup"><span data-stu-id="029ff-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="029ff-357">0x6 - ガベージ コレクションの準備。</span><span class="sxs-lookup"><span data-stu-id="029ff-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="029ff-358">カウント</span><span class="sxs-lookup"><span data-stu-id="029ff-358">Count</span></span>|<span data-ttu-id="029ff-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-359">win:UInt32</span></span>|<span data-ttu-id="029ff-360">その時点の GC カウント。</span><span class="sxs-lookup"><span data-stu-id="029ff-360">The GC count at the time.</span></span> <span data-ttu-id="029ff-361">通常、この後に後続の GC 開始イベントが表示され、そのカウントは、ガベージ コレクション中に、GC インデックスが増えるため、このカウント + 1 になります。</span><span class="sxs-lookup"><span data-stu-id="029ff-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="029ff-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-362">ClrInstanceID</span></span>|<span data-ttu-id="029ff-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-363">win:UInt16</span></span>|<span data-ttu-id="029ff-364">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="029ff-365">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="029ff-366">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="029ff-367">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="029ff-368">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-368">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-369">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-371">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-372">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="029ff-373">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-373">Event</span></span>|<span data-ttu-id="029ff-374">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-374">Event ID</span></span>|<span data-ttu-id="029ff-375">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="029ff-376">9</span><span class="sxs-lookup"><span data-stu-id="029ff-376">8</span></span>|<span data-ttu-id="029ff-377">ガベージ コレクションのための実行エンジンの中断の終了。</span><span class="sxs-lookup"><span data-stu-id="029ff-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="029ff-378">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="029ff-378">No event data.</span></span>  
  
 [<span data-ttu-id="029ff-379">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="029ff-380">GCAllocationTick_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="029ff-381">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-382">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-382">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-383">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-385">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-386">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-387">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-387">Event</span></span>|<span data-ttu-id="029ff-388">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-388">Event ID</span></span>|<span data-ttu-id="029ff-389">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="029ff-390">10</span><span class="sxs-lookup"><span data-stu-id="029ff-390">10</span></span>|<span data-ttu-id="029ff-391">約 100 KB が割り当てられるたび。</span><span class="sxs-lookup"><span data-stu-id="029ff-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="029ff-392">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-393">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-393">Field name</span></span>|<span data-ttu-id="029ff-394">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-394">Data type</span></span>|<span data-ttu-id="029ff-395">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="029ff-396">AllocationAmount</span></span>|<span data-ttu-id="029ff-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-397">win:UInt32</span></span>|<span data-ttu-id="029ff-398">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-398">The allocation size, in bytes.</span></span> <span data-ttu-id="029ff-399">この値は、ULONG (4,294,967,295 バイト) の長さより短い割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="029ff-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="029ff-400">割り当てがこれを超える場合、このフィールドには切り捨てられた値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="029ff-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="029ff-401">非常に大きな割り当てには `AllocationAmount64` を使用します。</span><span class="sxs-lookup"><span data-stu-id="029ff-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="029ff-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="029ff-402">AllocationKind</span></span>|<span data-ttu-id="029ff-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-403">win:UInt32</span></span>|<span data-ttu-id="029ff-404">0x0 - 小さなオブジェクトの割り当て (小さなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="029ff-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="029ff-405">0x1 - 大きなオブジェクトの割り当て (大きなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="029ff-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="029ff-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-406">ClrInstanceID</span></span>|<span data-ttu-id="029ff-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-407">win:UInt16</span></span>|<span data-ttu-id="029ff-408">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="029ff-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="029ff-409">AllocationAmount64</span></span>|<span data-ttu-id="029ff-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="029ff-410">win:UInt64</span></span>|<span data-ttu-id="029ff-411">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="029ff-411">The allocation size, in bytes.</span></span> <span data-ttu-id="029ff-412">この値は非常に大きな割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="029ff-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="029ff-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="029ff-413">TypeId</span></span>|<span data-ttu-id="029ff-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="029ff-414">win:Pointer</span></span>|<span data-ttu-id="029ff-415">MethodTable のアドレス。</span><span class="sxs-lookup"><span data-stu-id="029ff-415">The address of the MethodTable.</span></span> <span data-ttu-id="029ff-416">このイベント中に複数の型のオブジェクトが割り当てられた場合、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) に対応する MethodTable のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="029ff-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="029ff-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="029ff-417">TypeName</span></span>|<span data-ttu-id="029ff-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="029ff-418">win:UnicodeString</span></span>|<span data-ttu-id="029ff-419">割り当てられた型の名前。</span><span class="sxs-lookup"><span data-stu-id="029ff-419">The name of the type that was allocated.</span></span> <span data-ttu-id="029ff-420">このイベント中に複数の型のオブジェクトが割り当てられた場合は、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) の型です。</span><span class="sxs-lookup"><span data-stu-id="029ff-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="029ff-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="029ff-421">HeapIndex</span></span>|<span data-ttu-id="029ff-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-422">win:UInt32</span></span>|<span data-ttu-id="029ff-423">オブジェクトが割り当てられたヒープ。</span><span class="sxs-lookup"><span data-stu-id="029ff-423">The heap where the object was allocated.</span></span> <span data-ttu-id="029ff-424">ワークステーションのガベージ コレクションと共に実行する場合、この値は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="029ff-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="029ff-425">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="029ff-426">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="029ff-427">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-428">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-428">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-429">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-431">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-432">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-433">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-433">Event</span></span>|<span data-ttu-id="029ff-434">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-434">Event ID</span></span>|<span data-ttu-id="029ff-435">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="029ff-436">14</span><span class="sxs-lookup"><span data-stu-id="029ff-436">14</span></span>|<span data-ttu-id="029ff-437">ファイナライザーの実行の開始。</span><span class="sxs-lookup"><span data-stu-id="029ff-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="029ff-438">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="029ff-438">No event data.</span></span>  
  
 [<span data-ttu-id="029ff-439">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="029ff-440">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="029ff-441">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-442">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-442">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-443">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-445">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-446">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-447">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-447">Event</span></span>|<span data-ttu-id="029ff-448">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-448">Event ID</span></span>|<span data-ttu-id="029ff-449">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="029ff-450">13</span><span class="sxs-lookup"><span data-stu-id="029ff-450">13</span></span>|<span data-ttu-id="029ff-451">ファイナライザーの実行の終了。</span><span class="sxs-lookup"><span data-stu-id="029ff-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="029ff-452">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="029ff-453">フィールド名</span><span class="sxs-lookup"><span data-stu-id="029ff-453">Field name</span></span>|<span data-ttu-id="029ff-454">データ型</span><span class="sxs-lookup"><span data-stu-id="029ff-454">Data type</span></span>|<span data-ttu-id="029ff-455">説明</span><span class="sxs-lookup"><span data-stu-id="029ff-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="029ff-456">カウント</span><span class="sxs-lookup"><span data-stu-id="029ff-456">Count</span></span>|<span data-ttu-id="029ff-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="029ff-457">win:UInt32</span></span>|<span data-ttu-id="029ff-458">実行されたファイナライザーの数。</span><span class="sxs-lookup"><span data-stu-id="029ff-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="029ff-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="029ff-459">ClrInstanceID</span></span>|<span data-ttu-id="029ff-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="029ff-460">win:UInt16</span></span>|<span data-ttu-id="029ff-461">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="029ff-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="029ff-462">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="029ff-463">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="029ff-464">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-465">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-465">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-466">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-468">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-468">Informational (4)</span></span>|  
|<span data-ttu-id="029ff-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="029ff-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="029ff-470">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-471">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-472">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-472">Event</span></span>|<span data-ttu-id="029ff-473">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-473">Event ID</span></span>|<span data-ttu-id="029ff-474">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="029ff-475">11</span><span class="sxs-lookup"><span data-stu-id="029ff-475">11</span></span>|<span data-ttu-id="029ff-476">同時実行ガベージ コレクション スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="029ff-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="029ff-477">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="029ff-477">No event data.</span></span>  
  
 [<span data-ttu-id="029ff-478">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="029ff-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="029ff-479">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="029ff-480">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="029ff-481">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="029ff-481">Keyword for raising the event</span></span>|<span data-ttu-id="029ff-482">レベル</span><span class="sxs-lookup"><span data-stu-id="029ff-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="029ff-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="029ff-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="029ff-484">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-484">Informational (4)</span></span>|  
|<span data-ttu-id="029ff-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="029ff-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="029ff-486">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="029ff-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="029ff-487">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="029ff-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="029ff-488">イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-488">Event</span></span>|<span data-ttu-id="029ff-489">イベント ID</span><span class="sxs-lookup"><span data-stu-id="029ff-489">Event ID</span></span>|<span data-ttu-id="029ff-490">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="029ff-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="029ff-491">12</span><span class="sxs-lookup"><span data-stu-id="029ff-491">12</span></span>|<span data-ttu-id="029ff-492">同時実行ガベージ コレクションスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="029ff-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="029ff-493">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="029ff-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="029ff-494">参照</span><span class="sxs-lookup"><span data-stu-id="029ff-494">See Also</span></span>  
 [<span data-ttu-id="029ff-495">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="029ff-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
