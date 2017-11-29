---
title: "スレッド プール ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3dfd8b17e4ca01802651087ff20988744a411ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="e464a-102">スレッド プール ETW イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-102">Thread Pool ETW Events</span></span>
<span data-ttu-id="e464a-103"><a name="top"></a> これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="e464a-103"><a name="top"></a> These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="e464a-104">スレッド プール イベントには 2 つのグループがあります。</span><span class="sxs-lookup"><span data-stu-id="e464a-104">There are two groups of thread pool events:</span></span>  
  
-   <span data-ttu-id="e464a-105">[ワーカー スレッド プール イベント](#worker)は、アプリケーションがどのようにスレッド プールを使用するかに関する情報と、同時実行制御におけるワークロードの効果に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e464a-105">[Worker thread pool events](#worker), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
-   <span data-ttu-id="e464a-106">[I/O スレッド プール イベント](#io)は、スレッド プールで作成、無効化、無効化解除、または終了した I/O スレッドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e464a-106">[I/O thread pool events](#io), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a><span data-ttu-id="e464a-107">ワーカー スレッド プール イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-107">Worker Thread Pool Events</span></span>  
 <span data-ttu-id="e464a-108">これらのイベントは、ランタイムのワーカー スレッドのプールに関連付けられており、スレッド イベントに関する通知 (スレッドが作成されたり停止されたりした場合など) を提供します。</span><span class="sxs-lookup"><span data-stu-id="e464a-108">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="e464a-109">ワーカー スレッド プールは、スレッドの数が計測されたスループットに基づいて計算されるアダプティブ アルゴリズムを使用して、同時実行制御を実行します。</span><span class="sxs-lookup"><span data-stu-id="e464a-109">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="e464a-110">ワーカー スレッド プール イベントを使用すると、アプリケーションで使用されるスレッド プールの様子や特定のワークロードが同時実行制御に与える影響などを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="e464a-110">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="e464a-111">ThreadPoolWorkerThreadStart および ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="e464a-111">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  
 <span data-ttu-id="e464a-112">次の表に、これらのイベントのキーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-112">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="e464a-113">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="e464a-113">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e464a-114">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-114">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-115">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-115">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-116">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-116">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-117">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-117">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-118">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-118">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-119">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-119">Event</span></span>|<span data-ttu-id="e464a-120">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-120">Event ID</span></span>|<span data-ttu-id="e464a-121">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="e464a-121">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="e464a-122">50</span><span class="sxs-lookup"><span data-stu-id="e464a-122">50</span></span>|<span data-ttu-id="e464a-123">ワーカー スレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="e464a-123">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="e464a-124">51</span><span class="sxs-lookup"><span data-stu-id="e464a-124">51</span></span>|<span data-ttu-id="e464a-125">ワーカー スレッドが停止された。</span><span class="sxs-lookup"><span data-stu-id="e464a-125">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="e464a-126">52</span><span class="sxs-lookup"><span data-stu-id="e464a-126">52</span></span>|<span data-ttu-id="e464a-127">ワーカー スレッドが無効にされた。</span><span class="sxs-lookup"><span data-stu-id="e464a-127">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="e464a-128">53</span><span class="sxs-lookup"><span data-stu-id="e464a-128">53</span></span>|<span data-ttu-id="e464a-129">提供終了になったワーカー スレッドが再びアクティブになった。</span><span class="sxs-lookup"><span data-stu-id="e464a-129">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="e464a-130">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-130">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-131">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-131">Field name</span></span>|<span data-ttu-id="e464a-132">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-132">Data type</span></span>|<span data-ttu-id="e464a-133">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-133">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-134">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="e464a-134">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="e464a-135">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e464a-135">win:UInt32</span></span>|<span data-ttu-id="e464a-136">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="e464a-136">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="e464a-137">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="e464a-137">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="e464a-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e464a-138">win:UInt32</span></span>|<span data-ttu-id="e464a-139">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-139">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="e464a-140">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-140">ClrInstanceID</span></span>|<span data-ttu-id="e464a-141">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-141">Win:UInt16</span></span>|<span data-ttu-id="e464a-142">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-142">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="e464a-143">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="e464a-143">ThreadPoolWorkerThreadAdjustment</span></span>  
 <span data-ttu-id="e464a-144">これらのスレッド プール イベントは、スレッドの挿入 (同時実行制御) アルゴリズムの動作を理解したりデバッグしたりするための情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e464a-144">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="e464a-145">この情報は、ワーカー スレッド プールによって内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e464a-145">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="e464a-146">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="e464a-146">ThreadPoolWorkerThreadAdjustmentSample</span></span>  
 <span data-ttu-id="e464a-147">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-147">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-148">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-148">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-149">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-149">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-150">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-150">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-151">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-151">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-152">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-152">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-153">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-153">Event</span></span>|<span data-ttu-id="e464a-154">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-154">Event ID</span></span>|<span data-ttu-id="e464a-155">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-155">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="e464a-156">54</span><span class="sxs-lookup"><span data-stu-id="e464a-156">54</span></span>|<span data-ttu-id="e464a-157">1 つのサンプルの情報のコレクションを参照します。つまり、特定の同時実行レベルの特定の時刻におけるスループットの測定値です。</span><span class="sxs-lookup"><span data-stu-id="e464a-157">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="e464a-158">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-158">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-159">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-159">Field name</span></span>|<span data-ttu-id="e464a-160">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-160">Data type</span></span>|<span data-ttu-id="e464a-161">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-161">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-162">スループット</span><span class="sxs-lookup"><span data-stu-id="e464a-162">Throughput</span></span>|<span data-ttu-id="e464a-163">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-163">win:Double</span></span>|<span data-ttu-id="e464a-164">時間の単位あたりの入力候補の数です。</span><span class="sxs-lookup"><span data-stu-id="e464a-164">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="e464a-165">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-165">ClrInstanceID</span></span>|<span data-ttu-id="e464a-166">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-166">Win:UInt16</span></span>|<span data-ttu-id="e464a-167">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-167">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="e464a-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="e464a-168">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  
 <span data-ttu-id="e464a-169">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-169">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-170">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-170">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-171">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-171">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-172">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-172">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-173">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-173">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-174">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-174">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-175">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-175">Event</span></span>|<span data-ttu-id="e464a-176">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-176">Event ID</span></span>|<span data-ttu-id="e464a-177">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-177">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="e464a-178">55</span><span class="sxs-lookup"><span data-stu-id="e464a-178">55</span></span>|<span data-ttu-id="e464a-179">スレッドの挿入 (山登り法) アルゴリズムが、同時実行レベルに変更があったと判断した場合に、コントロールの変更を記録します。</span><span class="sxs-lookup"><span data-stu-id="e464a-179">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="e464a-180">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-180">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-181">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-181">Field name</span></span>|<span data-ttu-id="e464a-182">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-182">Data type</span></span>|<span data-ttu-id="e464a-183">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-183">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-184">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="e464a-184">AverageThroughput</span></span>|<span data-ttu-id="e464a-185">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-185">win:Double</span></span>|<span data-ttu-id="e464a-186">計測のサンプルの平均のスループット。</span><span class="sxs-lookup"><span data-stu-id="e464a-186">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="e464a-187">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="e464a-187">NewWorkerThreadCount</span></span>|<span data-ttu-id="e464a-188">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e464a-188">win:UInt32</span></span>|<span data-ttu-id="e464a-189">新しいアクティブなワーカー スレッド数。</span><span class="sxs-lookup"><span data-stu-id="e464a-189">New number of active worker threads.</span></span>|  
|<span data-ttu-id="e464a-190">理由</span><span class="sxs-lookup"><span data-stu-id="e464a-190">Reason</span></span>|<span data-ttu-id="e464a-191">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e464a-191">win:UInt32</span></span>|<span data-ttu-id="e464a-192">調整の理由。</span><span class="sxs-lookup"><span data-stu-id="e464a-192">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="e464a-193">0x00 - ウォーム アップ。</span><span class="sxs-lookup"><span data-stu-id="e464a-193">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="e464a-194">0x01 - 初期化。</span><span class="sxs-lookup"><span data-stu-id="e464a-194">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="e464a-195">0x02 - ランダムな移動。</span><span class="sxs-lookup"><span data-stu-id="e464a-195">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="e464a-196">0x03 - 上昇移動。</span><span class="sxs-lookup"><span data-stu-id="e464a-196">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="e464a-197">0x04 - 変更点。</span><span class="sxs-lookup"><span data-stu-id="e464a-197">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="e464a-198">0x05 - 安定化。</span><span class="sxs-lookup"><span data-stu-id="e464a-198">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="e464a-199">0x06 - 不足。</span><span class="sxs-lookup"><span data-stu-id="e464a-199">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="e464a-200">0x07 - スレッドのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="e464a-200">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="e464a-201">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-201">ClrInstanceID</span></span>|<span data-ttu-id="e464a-202">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-202">Win:UInt16</span></span>|<span data-ttu-id="e464a-203">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="e464a-204">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="e464a-204">ThreadPoolWorkerThreadAdjustmentStats</span></span>  
 <span data-ttu-id="e464a-205">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-205">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-206">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-206">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-207">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-207">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-208">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-208">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-209">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-209">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-210">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-210">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-211">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-211">Event</span></span>|<span data-ttu-id="e464a-212">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-212">Event ID</span></span>|<span data-ttu-id="e464a-213">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-213">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="e464a-214">56</span><span class="sxs-lookup"><span data-stu-id="e464a-214">56</span></span>|<span data-ttu-id="e464a-215">スレッド プールに関するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="e464a-215">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="e464a-216">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-216">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-217">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-217">Field name</span></span>|<span data-ttu-id="e464a-218">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-218">Data type</span></span>|<span data-ttu-id="e464a-219">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-219">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-220">期間</span><span class="sxs-lookup"><span data-stu-id="e464a-220">Duration</span></span>|<span data-ttu-id="e464a-221">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-221">win:Double</span></span>|<span data-ttu-id="e464a-222">これらの統計情報が収集される時間数 (秒)。</span><span class="sxs-lookup"><span data-stu-id="e464a-222">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="e464a-223">スループット</span><span class="sxs-lookup"><span data-stu-id="e464a-223">Throughput</span></span>|<span data-ttu-id="e464a-224">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-224">win:Double</span></span>|<span data-ttu-id="e464a-225">この間隔中の 1 秒あたりの入力候補の平均数。</span><span class="sxs-lookup"><span data-stu-id="e464a-225">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="e464a-226">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="e464a-226">ThreadWave</span></span>|<span data-ttu-id="e464a-227">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-227">win:Double</span></span>|<span data-ttu-id="e464a-228">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e464a-228">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e464a-229">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="e464a-229">ThroughputWave</span></span>|<span data-ttu-id="e464a-230">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-230">win:Double</span></span>|<span data-ttu-id="e464a-231">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e464a-231">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e464a-232">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="e464a-232">ThroughputErrorEstimate</span></span>|<span data-ttu-id="e464a-233">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-233">win:Double</span></span>|<span data-ttu-id="e464a-234">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e464a-234">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e464a-235">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="e464a-235">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="e464a-236">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-236">win:Double</span></span>|<span data-ttu-id="e464a-237">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="e464a-237">Reserved for internal use.</span></span>|  
|<span data-ttu-id="e464a-238">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="e464a-238">ThroughputRatio</span></span>|<span data-ttu-id="e464a-239">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-239">win:Double</span></span>|<span data-ttu-id="e464a-240">この間隔中にアクティブなワーカー スレッドの数の変動によって引き起こされる、スループットの相対的な向上。</span><span class="sxs-lookup"><span data-stu-id="e464a-240">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="e464a-241">信頼度</span><span class="sxs-lookup"><span data-stu-id="e464a-241">Confidence</span></span>|<span data-ttu-id="e464a-242">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-242">win:Double</span></span>|<span data-ttu-id="e464a-243">ThroughputRatio フィールドの有効性の測定結果。</span><span class="sxs-lookup"><span data-stu-id="e464a-243">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="e464a-244">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="e464a-244">NewcontrolSetting</span></span>|<span data-ttu-id="e464a-245">win:Double</span><span class="sxs-lookup"><span data-stu-id="e464a-245">win:Double</span></span>|<span data-ttu-id="e464a-246">アクティブなスレッド数の将来のバリエーションのベースラインとして使用するアクティブなワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-246">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="e464a-247">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="e464a-247">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="e464a-248">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-248">Win:UInt16</span></span>|<span data-ttu-id="e464a-249">アクティブなスレッド数の、将来のバリエーションの大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="e464a-249">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="e464a-250">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-250">ClrInstanceID</span></span>|<span data-ttu-id="e464a-251">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-251">Win:UInt16</span></span>|<span data-ttu-id="e464a-252">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-252">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e464a-253">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="e464a-253">Back to top</span></span>](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a><span data-ttu-id="e464a-254">I/O スレッド イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-254">I/O Thread Events</span></span>  
 <span data-ttu-id="e464a-255">これらのスレッド プール イベントは、I/O スレッド プール (完了ポート) にあるスレッドで発生します。これは非同期です。</span><span class="sxs-lookup"><span data-stu-id="e464a-255">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreatev1"></a><span data-ttu-id="e464a-256">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="e464a-256">IOThreadCreate_V1</span></span>  
 <span data-ttu-id="e464a-257">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-257">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-258">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-258">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-259">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-259">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-260">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-260">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-261">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-261">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-262">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-262">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-263">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-263">Event</span></span>|<span data-ttu-id="e464a-264">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-264">Event ID</span></span>|<span data-ttu-id="e464a-265">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="e464a-265">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="e464a-266">44</span><span class="sxs-lookup"><span data-stu-id="e464a-266">44</span></span>|<span data-ttu-id="e464a-267">I/O スレッドがスレッド プールに作成された。</span><span class="sxs-lookup"><span data-stu-id="e464a-267">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="e464a-268">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-268">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-269">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-269">Field name</span></span>|<span data-ttu-id="e464a-270">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-270">Data type</span></span>|<span data-ttu-id="e464a-271">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-271">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-272">カウント</span><span class="sxs-lookup"><span data-stu-id="e464a-272">Count</span></span>|<span data-ttu-id="e464a-273">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-273">win:UInt64</span></span>|<span data-ttu-id="e464a-274">新しく作成されたスレッドを含む、I/O のスレッドの数です。</span><span class="sxs-lookup"><span data-stu-id="e464a-274">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="e464a-275">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e464a-275">NumRetired</span></span>|<span data-ttu-id="e464a-276">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-276">win:UInt64</span></span>|<span data-ttu-id="e464a-277">提供終了になったワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-277">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="e464a-278">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-278">ClrInstanceID</span></span>|<span data-ttu-id="e464a-279">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-279">Win:UInt16</span></span>|<span data-ttu-id="e464a-280">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretirev1"></a><span data-ttu-id="e464a-281">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="e464a-281">IOThreadRetire_V1</span></span>  
 <span data-ttu-id="e464a-282">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-282">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-283">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-283">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-284">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-284">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-286">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-286">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-287">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-287">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-288">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-288">Event</span></span>|<span data-ttu-id="e464a-289">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-289">Event ID</span></span>|<span data-ttu-id="e464a-290">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="e464a-290">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="e464a-291">46</span><span class="sxs-lookup"><span data-stu-id="e464a-291">46</span></span>|<span data-ttu-id="e464a-292">I/O スレッドが、提供終了の候補になる。</span><span class="sxs-lookup"><span data-stu-id="e464a-292">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="e464a-293">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-293">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-294">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-294">Field name</span></span>|<span data-ttu-id="e464a-295">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-295">Data type</span></span>|<span data-ttu-id="e464a-296">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-296">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-297">カウント</span><span class="sxs-lookup"><span data-stu-id="e464a-297">Count</span></span>|<span data-ttu-id="e464a-298">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-298">win:UInt64</span></span>|<span data-ttu-id="e464a-299">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-299">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="e464a-300">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e464a-300">NumRetired</span></span>|<span data-ttu-id="e464a-301">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-301">win:UInt64</span></span>|<span data-ttu-id="e464a-302">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-302">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="e464a-303">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-303">ClrInstanceID</span></span>|<span data-ttu-id="e464a-304">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-304">Win:UInt16</span></span>|<span data-ttu-id="e464a-305">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-305">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretirev1"></a><span data-ttu-id="e464a-306">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="e464a-306">IOThreadUnretire_V1</span></span>  
 <span data-ttu-id="e464a-307">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-307">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-308">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-308">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-309">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-309">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-310">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-310">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-311">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-311">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-312">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-312">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-313">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-313">Event</span></span>|<span data-ttu-id="e464a-314">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-314">Event ID</span></span>|<span data-ttu-id="e464a-315">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="e464a-315">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="e464a-316">47</span><span class="sxs-lookup"><span data-stu-id="e464a-316">47</span></span>|<span data-ttu-id="e464a-317">スレッドが提供終了の候補になってから待機期間内に I/O が到着したため I/O スレッドが提供終了解除された。</span><span class="sxs-lookup"><span data-stu-id="e464a-317">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="e464a-318">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-318">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-319">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-319">Field name</span></span>|<span data-ttu-id="e464a-320">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-320">Data type</span></span>|<span data-ttu-id="e464a-321">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-321">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-322">カウント</span><span class="sxs-lookup"><span data-stu-id="e464a-322">Count</span></span>|<span data-ttu-id="e464a-323">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-323">win:UInt64</span></span>|<span data-ttu-id="e464a-324">これを含む、スレッド プール内の I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-324">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="e464a-325">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e464a-325">NumRetired</span></span>|<span data-ttu-id="e464a-326">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-326">win:UInt64</span></span>|<span data-ttu-id="e464a-327">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-327">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="e464a-328">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-328">ClrInstanceID</span></span>|<span data-ttu-id="e464a-329">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-329">Win:UInt16</span></span>|<span data-ttu-id="e464a-330">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-330">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="e464a-331">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="e464a-331">IOThreadTerminate</span></span>  
 <span data-ttu-id="e464a-332">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-332">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e464a-333">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="e464a-333">Keyword for raising the event</span></span>|<span data-ttu-id="e464a-334">レベル</span><span class="sxs-lookup"><span data-stu-id="e464a-334">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e464a-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="e464a-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="e464a-336">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="e464a-336">Informational (4)</span></span>|  
  
 <span data-ttu-id="e464a-337">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-337">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e464a-338">イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-338">Event</span></span>|<span data-ttu-id="e464a-339">イベント ID</span><span class="sxs-lookup"><span data-stu-id="e464a-339">Event ID</span></span>|<span data-ttu-id="e464a-340">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="e464a-340">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="e464a-341">45</span><span class="sxs-lookup"><span data-stu-id="e464a-341">45</span></span>|<span data-ttu-id="e464a-342">I/O スレッドがスレッド プールに作成された。</span><span class="sxs-lookup"><span data-stu-id="e464a-342">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="e464a-343">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="e464a-343">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e464a-344">フィールド名</span><span class="sxs-lookup"><span data-stu-id="e464a-344">Field name</span></span>|<span data-ttu-id="e464a-345">データ型</span><span class="sxs-lookup"><span data-stu-id="e464a-345">Data type</span></span>|<span data-ttu-id="e464a-346">説明</span><span class="sxs-lookup"><span data-stu-id="e464a-346">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e464a-347">カウント</span><span class="sxs-lookup"><span data-stu-id="e464a-347">Count</span></span>|<span data-ttu-id="e464a-348">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-348">win:UInt64</span></span>|<span data-ttu-id="e464a-349">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-349">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="e464a-350">NumRetired</span><span class="sxs-lookup"><span data-stu-id="e464a-350">NumRetired</span></span>|<span data-ttu-id="e464a-351">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e464a-351">win:UInt64</span></span>|<span data-ttu-id="e464a-352">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="e464a-352">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="e464a-353">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e464a-353">ClrInstanceID</span></span>|<span data-ttu-id="e464a-354">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e464a-354">Win:UInt16</span></span>|<span data-ttu-id="e464a-355">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e464a-355">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e464a-356">関連項目</span><span class="sxs-lookup"><span data-stu-id="e464a-356">See Also</span></span>  
 [<span data-ttu-id="e464a-357">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="e464a-357">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
