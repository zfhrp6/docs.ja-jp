---
title: ガベージ コレクション ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13f7e935ab999ccc3cd3ea1e308e8d686bed4171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396936"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="43f72-102">ガベージ コレクション ETW イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="43f72-103">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="43f72-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="43f72-104">ガベージ コレクションが実行された回数、ガベージ コレクションの間に解放されたメモリの量など、診断やデバッグに役立つ情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="43f72-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="43f72-105">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="43f72-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="43f72-106">GCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
-   [<span data-ttu-id="43f72-107">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
-   [<span data-ttu-id="43f72-108">GCHeapStats_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
-   [<span data-ttu-id="43f72-109">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
-   [<span data-ttu-id="43f72-110">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
-   [<span data-ttu-id="43f72-111">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
-   [<span data-ttu-id="43f72-112">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
-   [<span data-ttu-id="43f72-113">GCSuspendEE_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
-   [<span data-ttu-id="43f72-114">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
-   [<span data-ttu-id="43f72-115">GCAllocationTick_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
-   [<span data-ttu-id="43f72-116">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
-   [<span data-ttu-id="43f72-117">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
-   [<span data-ttu-id="43f72-118">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
-   [<span data-ttu-id="43f72-119">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a><span data-ttu-id="43f72-120">GCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="43f72-121">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="43f72-122">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="43f72-122">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="43f72-123">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-123">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-124">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-127">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-128">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-128">Event</span></span>|<span data-ttu-id="43f72-129">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-129">Event ID</span></span>|<span data-ttu-id="43f72-130">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="43f72-131">1</span><span class="sxs-lookup"><span data-stu-id="43f72-131">1</span></span>|<span data-ttu-id="43f72-132">ガベージ コレクションが開始されました。</span><span class="sxs-lookup"><span data-stu-id="43f72-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="43f72-133">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-134">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-134">Field name</span></span>|<span data-ttu-id="43f72-135">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-135">Data type</span></span>|<span data-ttu-id="43f72-136">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-137">カウント</span><span class="sxs-lookup"><span data-stu-id="43f72-137">Count</span></span>|<span data-ttu-id="43f72-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-138">win:UInt32</span></span>|<span data-ttu-id="43f72-139">*n*回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="43f72-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="43f72-140">奥行</span><span class="sxs-lookup"><span data-stu-id="43f72-140">Depth</span></span>|<span data-ttu-id="43f72-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-141">win:UInt32</span></span>|<span data-ttu-id="43f72-142">収集されるジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="43f72-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="43f72-143">理由</span><span class="sxs-lookup"><span data-stu-id="43f72-143">Reason</span></span>|<span data-ttu-id="43f72-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-144">win:UInt32</span></span>|<span data-ttu-id="43f72-145">ガベージ コレクションが発生した理由:</span><span class="sxs-lookup"><span data-stu-id="43f72-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="43f72-146">0x0 - 小さなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="43f72-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="43f72-147">0x1 - 強制実行。</span><span class="sxs-lookup"><span data-stu-id="43f72-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="43f72-148">0x2 - メモリ不足。</span><span class="sxs-lookup"><span data-stu-id="43f72-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="43f72-149">0x3 - 空。</span><span class="sxs-lookup"><span data-stu-id="43f72-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="43f72-150">0x4 - 大きなオブジェクト ヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="43f72-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="43f72-151">0x5 - 領域不足 (小さなオブジェクト ヒープが対象)。</span><span class="sxs-lookup"><span data-stu-id="43f72-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="43f72-152">0x6 - 領域不足 (大きなオブジェクト ヒープが対象)。</span><span class="sxs-lookup"><span data-stu-id="43f72-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="43f72-153">0x7 - 強制実行されるが、ブロッキングとして強制されない。</span><span class="sxs-lookup"><span data-stu-id="43f72-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="43f72-154">型</span><span class="sxs-lookup"><span data-stu-id="43f72-154">Type</span></span>|<span data-ttu-id="43f72-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-155">win:UInt32</span></span>|<span data-ttu-id="43f72-156">0x0 - バックグラウンド ガベージ コレクションの外部で発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="43f72-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="43f72-157">0x1 - バックグラウンド ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="43f72-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="43f72-158">0x2 - バックグラウンド ガベージ コレクションの実行中に発生するブロッキング ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="43f72-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="43f72-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-159">ClrInstanceID</span></span>|<span data-ttu-id="43f72-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-160">win:UInt16</span></span>|<span data-ttu-id="43f72-161">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="43f72-162">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a><span data-ttu-id="43f72-163">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="43f72-164">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-165">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-165">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-166">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-168">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-169">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-170">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-170">Event</span></span>|<span data-ttu-id="43f72-171">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-171">Event ID</span></span>|<span data-ttu-id="43f72-172">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="43f72-173">2</span><span class="sxs-lookup"><span data-stu-id="43f72-173">2</span></span>|<span data-ttu-id="43f72-174">ガベージ コレクションが終了しました。</span><span class="sxs-lookup"><span data-stu-id="43f72-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="43f72-175">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-176">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-176">Field name</span></span>|<span data-ttu-id="43f72-177">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-177">Data type</span></span>|<span data-ttu-id="43f72-178">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-179">カウント</span><span class="sxs-lookup"><span data-stu-id="43f72-179">Count</span></span>|<span data-ttu-id="43f72-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-180">win:UInt32</span></span>|<span data-ttu-id="43f72-181">*n*回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="43f72-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="43f72-182">奥行</span><span class="sxs-lookup"><span data-stu-id="43f72-182">Depth</span></span>|<span data-ttu-id="43f72-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-183">win:UInt32</span></span>|<span data-ttu-id="43f72-184">収集されたジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="43f72-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="43f72-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-185">ClrInstanceID</span></span>|<span data-ttu-id="43f72-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-186">win:UInt16</span></span>|<span data-ttu-id="43f72-187">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="43f72-188">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a><span data-ttu-id="43f72-189">GCHeapStats_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="43f72-190">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-191">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-191">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-192">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-194">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-195">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-196">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-196">Event</span></span>|<span data-ttu-id="43f72-197">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-197">Event ID</span></span>|<span data-ttu-id="43f72-198">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="43f72-199">4</span><span class="sxs-lookup"><span data-stu-id="43f72-199">4</span></span>|<span data-ttu-id="43f72-200">各ガベージ コレクション終了時のヒープの統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="43f72-201">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-202">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-202">Field name</span></span>|<span data-ttu-id="43f72-203">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-203">Data type</span></span>|<span data-ttu-id="43f72-204">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="43f72-205">GenerationSize0</span></span>|<span data-ttu-id="43f72-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-206">win:UInt64</span></span>|<span data-ttu-id="43f72-207">ジェネレーション 0 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="43f72-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="43f72-208">TotalPromotedSize0</span></span>|<span data-ttu-id="43f72-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-209">win:UInt64</span></span>|<span data-ttu-id="43f72-210">ジェネレーション 0 からジェネレーション 1 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="43f72-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="43f72-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="43f72-211">GenerationSize1</span></span>|<span data-ttu-id="43f72-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-212">win:UInt64</span></span>|<span data-ttu-id="43f72-213">ジェネレーション 1 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="43f72-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="43f72-214">TotalPromotedSize1</span></span>|<span data-ttu-id="43f72-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-215">win:UInt64</span></span>|<span data-ttu-id="43f72-216">ジェネレーション 1 からジェネレーション 2 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="43f72-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="43f72-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="43f72-217">GenerationSize2</span></span>|<span data-ttu-id="43f72-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-218">win:UInt64</span></span>|<span data-ttu-id="43f72-219">ジェネレーション 2 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="43f72-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="43f72-220">TotalPromotedSize2</span></span>|<span data-ttu-id="43f72-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-221">win:UInt64</span></span>|<span data-ttu-id="43f72-222">最後のガベージ コレクションの後にジェネレーション 2 に残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="43f72-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="43f72-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="43f72-223">GenerationSize3</span></span>|<span data-ttu-id="43f72-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-224">win:UInt64</span></span>|<span data-ttu-id="43f72-225">大きなオブジェクト ヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="43f72-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="43f72-226">TotalPromotedSize3</span></span>|<span data-ttu-id="43f72-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-227">win:UInt64</span></span>|<span data-ttu-id="43f72-228">最後のガベージ コレクションの後に大きなオブジェクト ヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="43f72-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="43f72-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="43f72-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="43f72-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-230">win:UInt64</span></span>|<span data-ttu-id="43f72-231">終了準備が完了しているオブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="43f72-232">FinalizationPromotedCount</span><span class="sxs-lookup"><span data-stu-id="43f72-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="43f72-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-233">win:UInt64</span></span>|<span data-ttu-id="43f72-234">終了準備が完了しているオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="43f72-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="43f72-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="43f72-235">PinnedObjectCount</span></span>|<span data-ttu-id="43f72-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-236">win:UInt32</span></span>|<span data-ttu-id="43f72-237">ピン止めオブジェクト (移動できないオブジェクト) の数。</span><span class="sxs-lookup"><span data-stu-id="43f72-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="43f72-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="43f72-238">SinkBlockCount</span></span>|<span data-ttu-id="43f72-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-239">win:UInt32</span></span>|<span data-ttu-id="43f72-240">使用中の同期ブロックの数。</span><span class="sxs-lookup"><span data-stu-id="43f72-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="43f72-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="43f72-241">GCHandleCount</span></span>|<span data-ttu-id="43f72-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-242">win:UInt32</span></span>|<span data-ttu-id="43f72-243">使用中のガベージ コレクション ハンドルの数。</span><span class="sxs-lookup"><span data-stu-id="43f72-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="43f72-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-244">ClrInstanceID</span></span>|<span data-ttu-id="43f72-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-245">win:UInt16</span></span>|<span data-ttu-id="43f72-246">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="43f72-247">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a><span data-ttu-id="43f72-248">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="43f72-249">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-250">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-250">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-251">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-253">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-254">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-255">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-255">Event</span></span>|<span data-ttu-id="43f72-256">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-256">Event ID</span></span>|<span data-ttu-id="43f72-257">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="43f72-258">5</span><span class="sxs-lookup"><span data-stu-id="43f72-258">5</span></span>|<span data-ttu-id="43f72-259">新しいガベージ コレクション セグメントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="43f72-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="43f72-260">既に実行されているプロセスでトレースを有効にした場合は、このイベントが各既存セグメントについて発生します。</span><span class="sxs-lookup"><span data-stu-id="43f72-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="43f72-261">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-262">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-262">Field name</span></span>|<span data-ttu-id="43f72-263">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-263">Data type</span></span>|<span data-ttu-id="43f72-264">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-265">アドレス</span><span class="sxs-lookup"><span data-stu-id="43f72-265">Address</span></span>|<span data-ttu-id="43f72-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-266">win:UInt64</span></span>|<span data-ttu-id="43f72-267">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="43f72-267">The address of the segment.</span></span>|  
|<span data-ttu-id="43f72-268">サイズ</span><span class="sxs-lookup"><span data-stu-id="43f72-268">Size</span></span>|<span data-ttu-id="43f72-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-269">win:UInt64</span></span>|<span data-ttu-id="43f72-270">セグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="43f72-270">The size of the segment.</span></span>|  
|<span data-ttu-id="43f72-271">型</span><span class="sxs-lookup"><span data-stu-id="43f72-271">Type</span></span>|<span data-ttu-id="43f72-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-272">win:UInt32</span></span>|<span data-ttu-id="43f72-273">0x0 - 小さなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="43f72-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="43f72-274">0x1 - 大きなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="43f72-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="43f72-275">0x2 - 読み取り専用ヒープ。</span><span class="sxs-lookup"><span data-stu-id="43f72-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="43f72-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-276">ClrInstanceID</span></span>|<span data-ttu-id="43f72-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-277">win:UInt16</span></span>|<span data-ttu-id="43f72-278">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="43f72-279">ガベージ コレクターによって割り当てられるセグメントのサイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="43f72-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="43f72-280">アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。</span><span class="sxs-lookup"><span data-stu-id="43f72-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="43f72-281">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a><span data-ttu-id="43f72-282">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="43f72-283">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-284">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-284">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-285">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-287">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-288">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-289">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-289">Event</span></span>|<span data-ttu-id="43f72-290">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-290">Event ID</span></span>|<span data-ttu-id="43f72-291">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="43f72-292">6</span><span class="sxs-lookup"><span data-stu-id="43f72-292">6</span></span>|<span data-ttu-id="43f72-293">ガベージ コレクション セグメントが解放されました。</span><span class="sxs-lookup"><span data-stu-id="43f72-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="43f72-294">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-295">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-295">Field name</span></span>|<span data-ttu-id="43f72-296">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-296">Data type</span></span>|<span data-ttu-id="43f72-297">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-298">アドレス</span><span class="sxs-lookup"><span data-stu-id="43f72-298">Address</span></span>|<span data-ttu-id="43f72-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-299">win:UInt64</span></span>|<span data-ttu-id="43f72-300">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="43f72-300">The address of the segment.</span></span>|  
|<span data-ttu-id="43f72-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-301">ClrInstanceID</span></span>|<span data-ttu-id="43f72-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-302">win:UInt16</span></span>|<span data-ttu-id="43f72-303">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="43f72-304">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a><span data-ttu-id="43f72-305">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="43f72-306">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-307">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-307">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-308">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-310">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-311">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-312">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-312">Event</span></span>|<span data-ttu-id="43f72-313">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-313">Event ID</span></span>|<span data-ttu-id="43f72-314">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="43f72-315">7</span><span class="sxs-lookup"><span data-stu-id="43f72-315">7</span></span>|<span data-ttu-id="43f72-316">共通言語ランタイムの中断からの再開が開始されました。</span><span class="sxs-lookup"><span data-stu-id="43f72-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="43f72-317">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="43f72-317">No event data.</span></span>  
  
 [<span data-ttu-id="43f72-318">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a><span data-ttu-id="43f72-319">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="43f72-320">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-321">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-321">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-322">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-324">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-325">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-326">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-326">Event</span></span>|<span data-ttu-id="43f72-327">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-327">Event Id</span></span>|<span data-ttu-id="43f72-328">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="43f72-329">3</span><span class="sxs-lookup"><span data-stu-id="43f72-329">3</span></span>|<span data-ttu-id="43f72-330">共通言語ランタイムの中断からの再開が終了しました。</span><span class="sxs-lookup"><span data-stu-id="43f72-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="43f72-331">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="43f72-331">No event data.</span></span>  
  
 [<span data-ttu-id="43f72-332">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a><span data-ttu-id="43f72-333">GCSuspendEE_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="43f72-334">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-335">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-335">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-336">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-339">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-340">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-340">Event</span></span>|<span data-ttu-id="43f72-341">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-341">Event ID</span></span>|<span data-ttu-id="43f72-342">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="43f72-343">9</span><span class="sxs-lookup"><span data-stu-id="43f72-343">9</span></span>|<span data-ttu-id="43f72-344">ガベージ コレクションのための実行エンジンの中断の開始。</span><span class="sxs-lookup"><span data-stu-id="43f72-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="43f72-345">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-346">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-346">Field name</span></span>|<span data-ttu-id="43f72-347">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-347">Data type</span></span>|<span data-ttu-id="43f72-348">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-349">理由</span><span class="sxs-lookup"><span data-stu-id="43f72-349">Reason</span></span>|<span data-ttu-id="43f72-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-350">win:UInt16</span></span>|<span data-ttu-id="43f72-351">0x0 - その他。</span><span class="sxs-lookup"><span data-stu-id="43f72-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="43f72-352">0x1 - ガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="43f72-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="43f72-353">0x2 - アプリケーション ドメインのシャットダウン。</span><span class="sxs-lookup"><span data-stu-id="43f72-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="43f72-354">0x3 - コード ピッチ。</span><span class="sxs-lookup"><span data-stu-id="43f72-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="43f72-355">0x4 - シャットダウン。</span><span class="sxs-lookup"><span data-stu-id="43f72-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="43f72-356">0x5 - デバッガー。</span><span class="sxs-lookup"><span data-stu-id="43f72-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="43f72-357">0x6 - ガベージ コレクションの準備。</span><span class="sxs-lookup"><span data-stu-id="43f72-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="43f72-358">カウント</span><span class="sxs-lookup"><span data-stu-id="43f72-358">Count</span></span>|<span data-ttu-id="43f72-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-359">win:UInt32</span></span>|<span data-ttu-id="43f72-360">その時点の GC カウント。</span><span class="sxs-lookup"><span data-stu-id="43f72-360">The GC count at the time.</span></span> <span data-ttu-id="43f72-361">通常、この後に後続の GC 開始イベントが表示され、そのカウントは、ガベージ コレクション中に、GC インデックスが増えるため、このカウント + 1 になります。</span><span class="sxs-lookup"><span data-stu-id="43f72-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="43f72-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-362">ClrInstanceID</span></span>|<span data-ttu-id="43f72-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-363">win:UInt16</span></span>|<span data-ttu-id="43f72-364">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="43f72-365">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a><span data-ttu-id="43f72-366">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="43f72-367">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="43f72-368">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-368">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-369">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-371">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-372">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="43f72-373">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-373">Event</span></span>|<span data-ttu-id="43f72-374">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-374">Event ID</span></span>|<span data-ttu-id="43f72-375">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="43f72-376">8</span><span class="sxs-lookup"><span data-stu-id="43f72-376">8</span></span>|<span data-ttu-id="43f72-377">ガベージ コレクションのための実行エンジンの中断の終了。</span><span class="sxs-lookup"><span data-stu-id="43f72-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="43f72-378">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="43f72-378">No event data.</span></span>  
  
 [<span data-ttu-id="43f72-379">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a><span data-ttu-id="43f72-380">GCAllocationTick_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="43f72-381">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-382">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-382">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-383">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-385">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-386">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-387">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-387">Event</span></span>|<span data-ttu-id="43f72-388">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-388">Event ID</span></span>|<span data-ttu-id="43f72-389">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="43f72-390">10</span><span class="sxs-lookup"><span data-stu-id="43f72-390">10</span></span>|<span data-ttu-id="43f72-391">約 100 KB が割り当てられるたび。</span><span class="sxs-lookup"><span data-stu-id="43f72-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="43f72-392">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-393">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-393">Field name</span></span>|<span data-ttu-id="43f72-394">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-394">Data type</span></span>|<span data-ttu-id="43f72-395">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="43f72-396">AllocationAmount</span></span>|<span data-ttu-id="43f72-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-397">win:UInt32</span></span>|<span data-ttu-id="43f72-398">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-398">The allocation size, in bytes.</span></span> <span data-ttu-id="43f72-399">この値は、ULONG (4,294,967,295 バイト) の長さより短い割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="43f72-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="43f72-400">割り当てがこれを超える場合、このフィールドには切り捨てられた値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43f72-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="43f72-401">非常に大きな割り当てには `AllocationAmount64` を使用します。</span><span class="sxs-lookup"><span data-stu-id="43f72-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="43f72-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="43f72-402">AllocationKind</span></span>|<span data-ttu-id="43f72-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-403">win:UInt32</span></span>|<span data-ttu-id="43f72-404">0x0 - 小さなオブジェクトの割り当て (小さなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="43f72-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="43f72-405">0x1 - 大きなオブジェクトの割り当て (大きなオブジェクト ヒープへの割り当て)。</span><span class="sxs-lookup"><span data-stu-id="43f72-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="43f72-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-406">ClrInstanceID</span></span>|<span data-ttu-id="43f72-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-407">win:UInt16</span></span>|<span data-ttu-id="43f72-408">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="43f72-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="43f72-409">AllocationAmount64</span></span>|<span data-ttu-id="43f72-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="43f72-410">win:UInt64</span></span>|<span data-ttu-id="43f72-411">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="43f72-411">The allocation size, in bytes.</span></span> <span data-ttu-id="43f72-412">この値は非常に大きな割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="43f72-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="43f72-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="43f72-413">TypeId</span></span>|<span data-ttu-id="43f72-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="43f72-414">win:Pointer</span></span>|<span data-ttu-id="43f72-415">MethodTable のアドレス。</span><span class="sxs-lookup"><span data-stu-id="43f72-415">The address of the MethodTable.</span></span> <span data-ttu-id="43f72-416">このイベント中に複数の型のオブジェクトが割り当てられた場合、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) に対応する MethodTable のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="43f72-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="43f72-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="43f72-417">TypeName</span></span>|<span data-ttu-id="43f72-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="43f72-418">win:UnicodeString</span></span>|<span data-ttu-id="43f72-419">割り当てられた型の名前。</span><span class="sxs-lookup"><span data-stu-id="43f72-419">The name of the type that was allocated.</span></span> <span data-ttu-id="43f72-420">このイベント中に複数の型のオブジェクトが割り当てられた場合は、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) の型です。</span><span class="sxs-lookup"><span data-stu-id="43f72-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="43f72-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="43f72-421">HeapIndex</span></span>|<span data-ttu-id="43f72-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-422">win:UInt32</span></span>|<span data-ttu-id="43f72-423">オブジェクトが割り当てられたヒープ。</span><span class="sxs-lookup"><span data-stu-id="43f72-423">The heap where the object was allocated.</span></span> <span data-ttu-id="43f72-424">ワークステーションのガベージ コレクションと共に実行する場合、この値は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="43f72-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="43f72-425">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a><span data-ttu-id="43f72-426">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="43f72-427">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-428">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-428">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-429">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-431">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-432">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-433">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-433">Event</span></span>|<span data-ttu-id="43f72-434">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-434">Event ID</span></span>|<span data-ttu-id="43f72-435">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="43f72-436">14</span><span class="sxs-lookup"><span data-stu-id="43f72-436">14</span></span>|<span data-ttu-id="43f72-437">ファイナライザーの実行の開始。</span><span class="sxs-lookup"><span data-stu-id="43f72-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="43f72-438">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="43f72-438">No event data.</span></span>  
  
 [<span data-ttu-id="43f72-439">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a><span data-ttu-id="43f72-440">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="43f72-441">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-442">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-442">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-443">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-445">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-446">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-447">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-447">Event</span></span>|<span data-ttu-id="43f72-448">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-448">Event ID</span></span>|<span data-ttu-id="43f72-449">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="43f72-450">13</span><span class="sxs-lookup"><span data-stu-id="43f72-450">13</span></span>|<span data-ttu-id="43f72-451">ファイナライザーの実行の終了。</span><span class="sxs-lookup"><span data-stu-id="43f72-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="43f72-452">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="43f72-453">フィールド名</span><span class="sxs-lookup"><span data-stu-id="43f72-453">Field name</span></span>|<span data-ttu-id="43f72-454">データ型</span><span class="sxs-lookup"><span data-stu-id="43f72-454">Data type</span></span>|<span data-ttu-id="43f72-455">説明</span><span class="sxs-lookup"><span data-stu-id="43f72-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="43f72-456">カウント</span><span class="sxs-lookup"><span data-stu-id="43f72-456">Count</span></span>|<span data-ttu-id="43f72-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="43f72-457">win:UInt32</span></span>|<span data-ttu-id="43f72-458">実行されたファイナライザーの数。</span><span class="sxs-lookup"><span data-stu-id="43f72-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="43f72-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="43f72-459">ClrInstanceID</span></span>|<span data-ttu-id="43f72-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="43f72-460">win:UInt16</span></span>|<span data-ttu-id="43f72-461">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="43f72-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="43f72-462">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a><span data-ttu-id="43f72-463">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="43f72-464">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-465">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-465">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-466">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-468">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-468">Informational (4)</span></span>|  
|<span data-ttu-id="43f72-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="43f72-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="43f72-470">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-471">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-472">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-472">Event</span></span>|<span data-ttu-id="43f72-473">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-473">Event ID</span></span>|<span data-ttu-id="43f72-474">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="43f72-475">11</span><span class="sxs-lookup"><span data-stu-id="43f72-475">11</span></span>|<span data-ttu-id="43f72-476">同時実行ガベージ コレクション スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="43f72-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="43f72-477">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="43f72-477">No event data.</span></span>  
  
 [<span data-ttu-id="43f72-478">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="43f72-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a><span data-ttu-id="43f72-479">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="43f72-480">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="43f72-481">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="43f72-481">Keyword for raising the event</span></span>|<span data-ttu-id="43f72-482">レベル</span><span class="sxs-lookup"><span data-stu-id="43f72-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="43f72-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="43f72-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="43f72-484">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-484">Informational (4)</span></span>|  
|<span data-ttu-id="43f72-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="43f72-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="43f72-486">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="43f72-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="43f72-487">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="43f72-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="43f72-488">イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-488">Event</span></span>|<span data-ttu-id="43f72-489">イベント ID</span><span class="sxs-lookup"><span data-stu-id="43f72-489">Event ID</span></span>|<span data-ttu-id="43f72-490">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="43f72-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="43f72-491">12</span><span class="sxs-lookup"><span data-stu-id="43f72-491">12</span></span>|<span data-ttu-id="43f72-492">同時実行ガベージ コレクションスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="43f72-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="43f72-493">イベント データはありません。</span><span class="sxs-lookup"><span data-stu-id="43f72-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f72-494">関連項目</span><span class="sxs-lookup"><span data-stu-id="43f72-494">See Also</span></span>  
 [<span data-ttu-id="43f72-495">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="43f72-495">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
