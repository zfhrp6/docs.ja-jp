---
title: "スレッドのスケジューリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e1fb7d61b8e250884b2c57cad8c5106bc77787a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="scheduling-threads"></a><span data-ttu-id="94359-102">スレッドのスケジューリング</span><span class="sxs-lookup"><span data-stu-id="94359-102">Scheduling Threads</span></span>
<span data-ttu-id="94359-103">すべてのスレッドが、スレッド優先順位が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="94359-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="94359-104">共通言語ランタイム内で作成されたスレッドは、の優先順位を割り当てられた最初に**ThreadPriority.Normal**です。</span><span class="sxs-lookup"><span data-stu-id="94359-104">Threads created within the common language runtime are initially assigned the priority of **ThreadPriority.Normal**.</span></span> <span data-ttu-id="94359-105">ランタイム外部で作成されたスレッドは、マネージ環境に入る前にされていた優先順位を保持します。</span><span class="sxs-lookup"><span data-stu-id="94359-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="94359-106">取得またはとの任意のスレッドの優先順位を設定することができます、 **Thread.Priority**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="94359-106">You can get or set the priority of any thread with the **Thread.Priority** property.</span></span>  
  
 <span data-ttu-id="94359-107">優先度に基づいて実行するためのスレッドがスケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="94359-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="94359-108">場合でも、ランタイム内のスレッドが、すべてのスレッドは、オペレーティング システムでプロセッサのタイム スライスを割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="94359-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="94359-109">スレッドが実行される順序を決定するために使用するスケジューリング アルゴリズムの詳細については、各オペレーティング システムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="94359-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="94359-110">いくつかのオペレーティング システムでは、最初に実行する (実行可能なスレッド) の優先順位が高いスレッドが常にスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="94359-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="94359-111">優先順位が同じ複数のスレッドが使用可能なすべての場合は、スケジューラを循環その優先順位にあるスレッドの各スレッドに実行するための固定されたタイム スライスを提供します。</span><span class="sxs-lookup"><span data-stu-id="94359-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="94359-112">優先順位の高いスレッドが実行できるように、実行する優先度の低いスレッドは発生しません。</span><span class="sxs-lookup"><span data-stu-id="94359-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="94359-113">指定された優先順位で実行可能なスレッドがある場合は、スケジューラは優先順位の低い [次へ] に移動し、実行の優先度のスレッドをスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="94359-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="94359-114">高い優先順位のスレッドが実行可能になった場合は、低い優先順位のスレッドがプリエンプションの対象し、優先順位の高いスレッドをもう一度実行できます。</span><span class="sxs-lookup"><span data-stu-id="94359-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="94359-115">上に、オペレーティング システムことができますもスレッドの優先順位を動的に調整、アプリケーションのユーザー インターフェイスがフォア グラウンドとバック グラウンドの間で移動されるとします。</span><span class="sxs-lookup"><span data-stu-id="94359-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="94359-116">他のオペレーティング システムは、別のスケジューリング アルゴリズムを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="94359-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94359-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="94359-117">See Also</span></span>  
 [<span data-ttu-id="94359-118">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="94359-118">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="94359-119">Windows でのマネージ スレッド処理とアンマネージ スレッド処理</span><span class="sxs-lookup"><span data-stu-id="94359-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
