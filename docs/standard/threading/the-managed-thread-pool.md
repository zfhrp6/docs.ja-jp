---
title: マネージ スレッド プール
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3894229ff5561e50d42a36f576a89ee7bf01c067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592419"
---
# <a name="the-managed-thread-pool"></a><span data-ttu-id="f6117-102">マネージ スレッド プール</span><span class="sxs-lookup"><span data-stu-id="f6117-102">The Managed Thread Pool</span></span>
<span data-ttu-id="f6117-103"><xref:System.Threading.ThreadPool> クラスを使用すると、システムによって管理されるワーカー スレッドのプールがアプリケーションに提供されます。これを利用すると、開発者は、スレッド管理ではなくアプリケーション タスクに注意を集中できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f6117-103">The <xref:System.Threading.ThreadPool> class provides your application with a pool of worker threads that are managed by the system, allowing you to concentrate on application tasks rather than thread management.</span></span> <span data-ttu-id="f6117-104">バックグラウンド処理が必要な短いタスクがある場合、マネージ スレッド プールを使用すると、複数のスレッドを簡単に利用できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-104">If you have short tasks that require background processing, the managed thread pool is an easy way to take advantage of multiple threads.</span></span> <span data-ttu-id="f6117-105">たとえば、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、スレッド プールのスレッドで非同期タスクを実行する <xref:System.Threading.Tasks.Task> オブジェクトと <xref:System.Threading.Tasks.Task%601> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-105">For example, beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] you can create <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects, which perform asynchronous tasks on thread pool threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6117-106">[!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 以降では、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の以前のリリースでボトルネックとして識別されていた 3 つの重要な分野 (キューへのタスクの配置、スレッド プールのスレッドのディスパッチ、および I/O 完了スレッドのディスパッチ) において、スレッド プールのスループットが大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="f6117-106">Starting with the [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], the throughput of the thread pool is significantly improved in three key areas that were identified as bottlenecks in previous releases of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]: queuing tasks, dispatching thread pool threads, and dispatching I/O completion threads.</span></span> <span data-ttu-id="f6117-107">この機能を使用するには、アプリケーションで [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] 以降を対象とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-107">To use this functionality, your application should target the [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] or later.</span></span>  
  
 <span data-ttu-id="f6117-108">ユーザー インターフェイスと対話するバックグラウンド タスクの場合、.NET Framework Version 2.0 では、ユーザー インターフェイス スレッドで生成されたイベントを使用して通信する <xref:System.ComponentModel.BackgroundWorker> クラスも利用できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-108">For background tasks that interact with the user interface, the .NET Framework version 2.0 also provides the <xref:System.ComponentModel.BackgroundWorker> class, which communicates using events raised on the user interface thread.</span></span>  
  
 <span data-ttu-id="f6117-109">.NET Framework では、非同期 I/O 完了、タイマー コールバック、登録済みの待機操作、デリゲートを使用した非同期メソッド呼び出し、<xref:System.Net> ソケット接続などのさまざまな目的でスレッド プールのスレッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6117-109">The .NET Framework uses thread pool threads for many purposes, including asynchronous I/O completion, timer callbacks, registered wait operations, asynchronous method calls using delegates, and <xref:System.Net> socket connections.</span></span>  
  
## <a name="when-not-to-use-thread-pool-threads"></a><span data-ttu-id="f6117-110">スレッド プールのスレッドを使用しない場合</span><span class="sxs-lookup"><span data-stu-id="f6117-110">When Not to Use Thread Pool Threads</span></span>  
 <span data-ttu-id="f6117-111">次のような場合は、スレッド プールのスレッドを使用する代わりに独自のスレッドを作成して管理する方が適切です。</span><span class="sxs-lookup"><span data-stu-id="f6117-111">There are several scenarios in which it is appropriate to create and manage your own threads instead of using thread pool threads:</span></span>  
  
-   <span data-ttu-id="f6117-112">フォア グラウンド スレッドが必要な場合。</span><span class="sxs-lookup"><span data-stu-id="f6117-112">You require a foreground thread.</span></span>  
  
-   <span data-ttu-id="f6117-113">スレッドに特定の優先順位を設定する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="f6117-113">You require a thread to have a particular priority.</span></span>  
  
-   <span data-ttu-id="f6117-114">スレッドを長時間にわたってブロックするタスクがある場合。</span><span class="sxs-lookup"><span data-stu-id="f6117-114">You have tasks that cause the thread to block for long periods of time.</span></span> <span data-ttu-id="f6117-115">スレッド プールには最大数のスレッドが存在するため、多数のスレッド プール スレッドがブロックされると、タスクを開始できなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="f6117-115">The thread pool has a maximum number of threads, so a large number of blocked thread pool threads might prevent tasks from starting.</span></span>  
  
-   <span data-ttu-id="f6117-116">スレッドをシングルスレッド アパートメント内に配置する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="f6117-116">You need to place threads into a single-threaded apartment.</span></span> <span data-ttu-id="f6117-117"><xref:System.Threading.ThreadPool> スレッドはすべてマルチスレッド アパートメント内にあります。</span><span class="sxs-lookup"><span data-stu-id="f6117-117">All <xref:System.Threading.ThreadPool> threads are in the multithreaded apartment.</span></span>  
  
-   <span data-ttu-id="f6117-118">安定した ID をスレッドに関連付ける必要がある場合、またはスレッドを特定のタスク専用にする必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="f6117-118">You need to have a stable identity associated with the thread, or to dedicate a thread to a task.</span></span>  
  
## <a name="thread-pool-characteristics"></a><span data-ttu-id="f6117-119">スレッド プールの特徴</span><span class="sxs-lookup"><span data-stu-id="f6117-119">Thread Pool Characteristics</span></span>  
 <span data-ttu-id="f6117-120">スレッド プールのスレッドはバックグラウンド スレッドです。</span><span class="sxs-lookup"><span data-stu-id="f6117-120">Thread pool threads are background threads.</span></span> <span data-ttu-id="f6117-121">「[フォアグラウンド スレッドとバックグラウンド スレッド](../../../docs/standard/threading/foreground-and-background-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6117-121">See [Foreground and Background Threads](../../../docs/standard/threading/foreground-and-background-threads.md).</span></span> <span data-ttu-id="f6117-122">各スレッドは、既定のスタック サイズを使用し、既定の優先順位で実行されます。また、各スレッドはマルチスレッド アパートメント内にあります。</span><span class="sxs-lookup"><span data-stu-id="f6117-122">Each thread uses the default stack size, runs at the default priority, and is in the multithreaded apartment.</span></span>  
  
 <span data-ttu-id="f6117-123">プロセスごとにスレッド プールが 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="f6117-123">There is only one thread pool per process.</span></span>  
  
### <a name="exceptions-in-thread-pool-threads"></a><span data-ttu-id="f6117-124">スレッド プールのスレッドでの例外</span><span class="sxs-lookup"><span data-stu-id="f6117-124">Exceptions in Thread Pool Threads</span></span>  
 <span data-ttu-id="f6117-125">スレッド プールのスレッドで未処理の例外が発生すると、プロセスが終了します。</span><span class="sxs-lookup"><span data-stu-id="f6117-125">Unhandled exceptions on thread pool threads terminate the process.</span></span> <span data-ttu-id="f6117-126">この規則には、次の 3 つの例外があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-126">There are three exceptions to this rule:</span></span>  
  
-   <span data-ttu-id="f6117-127"><xref:System.Threading.Thread.Abort%2A> が呼び出されたため、スレッド プールのスレッドに <xref:System.Threading.ThreadAbortException> がスローされる。</span><span class="sxs-lookup"><span data-stu-id="f6117-127">A <xref:System.Threading.ThreadAbortException> is thrown in a thread pool thread, because <xref:System.Threading.Thread.Abort%2A> was called.</span></span>  
  
-   <span data-ttu-id="f6117-128">アプリケーション ドメインがアンロードされるため、スレッド プールのスレッドに <xref:System.AppDomainUnloadedException> がスローされる。</span><span class="sxs-lookup"><span data-stu-id="f6117-128">An <xref:System.AppDomainUnloadedException> is thrown in a thread pool thread, because the application domain is being unloaded.</span></span>  
  
-   <span data-ttu-id="f6117-129">共通言語ランタイムまたはホスト プロセスがスレッドを終了する。</span><span class="sxs-lookup"><span data-stu-id="f6117-129">The common language runtime or a host process terminates the thread.</span></span>  
  
 <span data-ttu-id="f6117-130">詳しくは、「[マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6117-130">For more information, see [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6117-131">.NET Framework Version 1.0 および 1.1 では、スレッド プールのスレッドの未処理の例外は、共通言語ランタイムによって通知なしにトラップされます。</span><span class="sxs-lookup"><span data-stu-id="f6117-131">In the .NET Framework versions 1.0 and 1.1, the common language runtime silently traps unhandled exceptions in thread pool threads.</span></span> <span data-ttu-id="f6117-132">このため、アプリケーション状態が破損し、最終的にアプリケーションが停止することになり、デバッグが困難になることがあります。</span><span class="sxs-lookup"><span data-stu-id="f6117-132">This might corrupt application state and eventually cause applications to hang, which might be very difficult to debug.</span></span>  
  
### <a name="maximum-number-of-thread-pool-threads"></a><span data-ttu-id="f6117-133">スレッド プールのスレッドの最大数</span><span class="sxs-lookup"><span data-stu-id="f6117-133">Maximum Number of Thread Pool Threads</span></span>  
 <span data-ttu-id="f6117-134">スレッド プールのキューに配置できる操作の数は、使用できるメモリの容量によってのみ制限されますが、スレッド プールでは、プロセス内で同時にアクティブにできるスレッドの数が制限されます。</span><span class="sxs-lookup"><span data-stu-id="f6117-134">The number of operations that can be queued to the thread pool is limited only by available memory; however, the thread pool limits the number of threads that can be active in the process simultaneously.</span></span> <span data-ttu-id="f6117-135">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、プロセスのスレッド プールの既定のサイズは、仮想アドレス空間のサイズなど、いくつかの要素によって決まります。</span><span class="sxs-lookup"><span data-stu-id="f6117-135">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the default size of the thread pool for a process depends on several factors, such as the size of the virtual address space.</span></span> <span data-ttu-id="f6117-136">スレッドの数は、プロセスで <xref:System.Threading.ThreadPool.GetMaxThreads%2A> メソッドを呼び出せば確認できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-136">A process can call the <xref:System.Threading.ThreadPool.GetMaxThreads%2A> method to determine the number of threads.</span></span>  
  
 <span data-ttu-id="f6117-137">スレッドの最大数を制御するには、<xref:System.Threading.ThreadPool.GetMaxThreads%2A> メソッドと <xref:System.Threading.ThreadPool.SetMaxThreads%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f6117-137">You can control the maximum number of threads by using the <xref:System.Threading.ThreadPool.GetMaxThreads%2A> and <xref:System.Threading.ThreadPool.SetMaxThreads%2A> methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6117-138">.NET Framework Version 1.0 および 1.1 では、スレッド プールのサイズはマネージ コードから設定できません。</span><span class="sxs-lookup"><span data-stu-id="f6117-138">In the .NET Framework versions 1.0 and 1.1, the size of the thread pool cannot be set from managed code.</span></span> <span data-ttu-id="f6117-139">共通言語ランタイムをホストするコードでは、mscoree.h で定義された `CorSetMaxThreads` を使用してサイズを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-139">Code that hosts the common language runtime can set the size using `CorSetMaxThreads`, defined in mscoree.h.</span></span>  
  
### <a name="thread-pool-minimums"></a><span data-ttu-id="f6117-140">スレッド プールの最小値</span><span class="sxs-lookup"><span data-stu-id="f6117-140">Thread Pool Minimums</span></span>  
 <span data-ttu-id="f6117-141">スレッド プールでは、カテゴリごとに指定された最小値に達するまで、要求に応じて新しいワーカー スレッドまたは I/O 完了スレッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="f6117-141">The thread pool provides new worker threads or I/O completion threads on demand until it reaches a specified minimum for each category.</span></span> <span data-ttu-id="f6117-142">これらの最小値は、<xref:System.Threading.ThreadPool.GetMinThreads%2A> メソッドを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-142">You can use the <xref:System.Threading.ThreadPool.GetMinThreads%2A> method to obtain these minimum values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6117-143">要求が少ないときは、スレッド プールの実際のスレッド数が最小値を下回る場合があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-143">When demand is low, the actual number of thread pool threads can fall below the minimum values.</span></span>  
  
 <span data-ttu-id="f6117-144">スレッド プールの最小値に達すると、追加のスレッドが作成されるか、いくつかのタスクが完了するまで待機状態になります。</span><span class="sxs-lookup"><span data-stu-id="f6117-144">When a minimum is reached, the thread pool can create additional threads or wait until some tasks complete.</span></span> <span data-ttu-id="f6117-145">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降では、スループットを最適化するために、スレッド プールでワーカー スレッドの作成と破棄が行われます。スループットは、タスクの単位時間あたりの完了数として定義されます。</span><span class="sxs-lookup"><span data-stu-id="f6117-145">Beginning with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the thread pool creates and destroys worker threads in order to optimize throughput, which is defined as the number of tasks that complete per unit of time.</span></span> <span data-ttu-id="f6117-146">スレッドが少なすぎると使用可能なリソースが最適に使用されない可能性があり、スレッドが多すぎるとリソースの競合が増える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-146">Too few threads might not make optimal use of available resources, whereas too many threads could increase resource contention.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f6117-147">アイドル スレッドの最小数は、<xref:System.Threading.ThreadPool.SetMinThreads%2A> メソッドを使用して増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="f6117-147">You can use the <xref:System.Threading.ThreadPool.SetMinThreads%2A> method to increase the minimum number of idle threads.</span></span> <span data-ttu-id="f6117-148">ただし、これらの値を必要以上に大きくすると、パフォーマンスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-148">However, unnecessarily increasing these values can cause performance problems.</span></span> <span data-ttu-id="f6117-149">同時に開始するタスクの数が多すぎる場合は、すべてのタスクで処理速度が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-149">If too many tasks start at the same time, all of them might appear to be slow.</span></span> <span data-ttu-id="f6117-150">ほとんどの場合、スレッドを割り当てるためのスレッド プール独自のアルゴリズムを使用することでスレッド プールのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f6117-150">In most cases the thread pool will perform better with its own algorithm for allocating threads.</span></span>  
  
## <a name="skipping-security-checks"></a><span data-ttu-id="f6117-151">セキュリティ チェックのスキップ</span><span class="sxs-lookup"><span data-stu-id="f6117-151">Skipping Security Checks</span></span>  
 <span data-ttu-id="f6117-152">スレッド プールでは、<xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> メソッドと <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f6117-152">The thread pool also provides the <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> and <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="f6117-153">これらのメソッドは、呼び出し元のスタックが、キューに配置されているタスクの実行時に行われるセキュリティ チェックと無関係であることが確認できる場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="f6117-153">Use these methods only when you are certain that the caller's stack is irrelevant to any security checks performed during the execution of the queued task.</span></span> <span data-ttu-id="f6117-154"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> と <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> はどちらも呼び出し元のスタックを取り込みます。このスタックは、スレッドがタスクの実行を開始するときにスレッド プールのスレッドのスタックにマージされます。</span><span class="sxs-lookup"><span data-stu-id="f6117-154"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> and <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> both capture the caller's stack, which is merged into the stack of the thread pool thread when the thread begins to execute a task.</span></span> <span data-ttu-id="f6117-155">セキュリティ チェックが必要な場合は、そのスタック全体をチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6117-155">If a security check is required, the entire stack must be checked.</span></span> <span data-ttu-id="f6117-156">チェックは安全性を提供しますが、パフォーマンスへの影響もあります。</span><span class="sxs-lookup"><span data-stu-id="f6117-156">Although the check provides safety, it also has a performance cost.</span></span>  
  
## <a name="using-the-thread-pool"></a><span data-ttu-id="f6117-157">スレッド プールの使用</span><span class="sxs-lookup"><span data-stu-id="f6117-157">Using the Thread Pool</span></span>  
 <span data-ttu-id="f6117-158">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降でスレッド プールを使用する場合は、[タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) を使用すると最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="f6117-158">Beginning with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the easiest way to use the thread pool is to use the [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md).</span></span> <span data-ttu-id="f6117-159"><xref:System.Threading.Tasks.Task> や <xref:System.Threading.Tasks.Task%601> などの並列ライブラリの型では、既定でスレッド プールのスレッドを使用してタスクが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f6117-159">By default, parallel library types like <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> use thread pool threads to run tasks.</span></span> <span data-ttu-id="f6117-160">また、マネージ コードから <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> (またはアンマネージ コードから `CorQueueUserWorkItem`) を呼び出し、タスクを実行するメソッドを表す <xref:System.Threading.WaitCallback> デリゲートを渡すことによってスレッド プールを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f6117-160">You can also use the thread pool by calling <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> from managed code (or `CorQueueUserWorkItem` from unmanaged code) and passing a <xref:System.Threading.WaitCallback> delegate representing the method that performs the task.</span></span> <span data-ttu-id="f6117-161">スレッド プールを使用するもう 1 つの方法として、待機操作の関連ワーク アイテムをキューに置く方法もあります。これには、<xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドを使用し、<xref:System.Threading.WaitHandle> を渡します。その WaitHandle がシグナル状態になるかタイムアウトになると、<xref:System.Threading.WaitOrTimerCallback> デリゲートによって表されるメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f6117-161">Another way to use the thread pool is to queue work items that are related to a wait operation by using the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method and passing a <xref:System.Threading.WaitHandle> that, when signaled or when timed out, calls the method represented by the <xref:System.Threading.WaitOrTimerCallback> delegate.</span></span> <span data-ttu-id="f6117-162">スレッド プールのスレッドを使用してコールバック メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f6117-162">Thread pool threads are used to invoke callback methods.</span></span>  
  
## <a name="threadpool-examples"></a><span data-ttu-id="f6117-163">ThreadPool の例</span><span class="sxs-lookup"><span data-stu-id="f6117-163">ThreadPool Examples</span></span>  
 <span data-ttu-id="f6117-164">このセクションのコード例では、<xref:System.Threading.Tasks.Task> クラス、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> メソッド、および <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドを使用したスレッド プールの例を示します。</span><span class="sxs-lookup"><span data-stu-id="f6117-164">The code examples in this section demonstrate the thread pool by using the <xref:System.Threading.Tasks.Task> class, the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method, and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method.</span></span>  
  
-   [<span data-ttu-id="f6117-165">タスク並列ライブラリを使用した非同期タスクの実行</span><span class="sxs-lookup"><span data-stu-id="f6117-165">Executing Asynchronous Tasks with the Task Parallel Library</span></span>](#TaskParallelLibrary)  
  
-   [<span data-ttu-id="f6117-166">QueueUserWorkItem を使用した非同期のコード実行</span><span class="sxs-lookup"><span data-stu-id="f6117-166">Executing Code Asynchronously with QueueUserWorkItem</span></span>](#ExecuteCodeWithQUWI)  
  
-   [<span data-ttu-id="f6117-167">QueueUserWorkItem へのタスク データの供給</span><span class="sxs-lookup"><span data-stu-id="f6117-167">Supplying Task Data for QueueUserWorkItem</span></span>](#TaskDataForQUWI)  
  
-   [<span data-ttu-id="f6117-168">RegisterWaitForSingleObject の使用</span><span class="sxs-lookup"><span data-stu-id="f6117-168">Using RegisterWaitForSingleObject</span></span>](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a><span data-ttu-id="f6117-169">タスク並列ライブラリを使用した非同期タスクの実行</span><span class="sxs-lookup"><span data-stu-id="f6117-169">Executing Asynchronous Tasks with the Task Parallel Library</span></span>  
 <span data-ttu-id="f6117-170">次の例では、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> メソッドを呼び出すことにより、<xref:System.Threading.Tasks.Task> オブジェクトを作成して使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f6117-170">The following example shows how to create and use a <xref:System.Threading.Tasks.Task> object by calling the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f6117-171"><xref:System.Threading.Tasks.Task%601> クラスを使用して非同期タスクから値を返す方法の例については、「[方法: タスクから値を返す](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6117-171">For an example that uses the <xref:System.Threading.Tasks.Task%601> class to return a value from an asynchronous task, see [How to: Return a Value from a Task](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).</span></span>  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a><span data-ttu-id="f6117-172">QueueUserWorkItem を使用した非同期のコード実行</span><span class="sxs-lookup"><span data-stu-id="f6117-172">Executing Code Asynchronously with QueueUserWorkItem</span></span>  
 <span data-ttu-id="f6117-173">次の例では、`ThreadProc` メソッドで表される単純なタスクを <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドを使用してキューに置きます。</span><span class="sxs-lookup"><span data-stu-id="f6117-173">The following example queues a very simple task, represented by the `ThreadProc` method, using the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span>  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a><span data-ttu-id="f6117-174">QueueUserWorkItem へのタスク データの供給</span><span class="sxs-lookup"><span data-stu-id="f6117-174">Supplying Task Data for QueueUserWorkItem</span></span>  
 <span data-ttu-id="f6117-175"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドを使用してタスクをキューに置き、そのタスクにデータを与えるコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f6117-175">The following code example uses the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method to queue a task and supply the data for the task.</span></span>  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a><span data-ttu-id="f6117-176">RegisterWaitForSingleObject の使用</span><span class="sxs-lookup"><span data-stu-id="f6117-176">Using RegisterWaitForSingleObject</span></span>  
 <span data-ttu-id="f6117-177">次の例では、スレッド処理のいくつかの機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6117-177">The following example demonstrates several threading features.</span></span>  
  
-   <span data-ttu-id="f6117-178"><xref:System.Threading.ThreadPool> スレッドで実行するタスクを、<xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> メソッドを使用してキューに配置します。</span><span class="sxs-lookup"><span data-stu-id="f6117-178">Queuing a task for execution by <xref:System.Threading.ThreadPool> threads, with the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method.</span></span>  
  
-   <span data-ttu-id="f6117-179"><xref:System.Threading.AutoResetEvent> を使用して、実行するようにタスクに通知します。</span><span class="sxs-lookup"><span data-stu-id="f6117-179">Signaling a task to execute, with <xref:System.Threading.AutoResetEvent>.</span></span> <span data-ttu-id="f6117-180">「[EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6117-180">See [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).</span></span>  
  
-   <span data-ttu-id="f6117-181"><xref:System.Threading.WaitOrTimerCallback> デリゲートを使用して、タイムアウトと通知の両方を処理します。</span><span class="sxs-lookup"><span data-stu-id="f6117-181">Handling both time-outs and signals with a <xref:System.Threading.WaitOrTimerCallback> delegate.</span></span>  
  
-   <span data-ttu-id="f6117-182"><xref:System.Threading.RegisteredWaitHandle> を使用して、キューに置かれたタスクを取り消します。</span><span class="sxs-lookup"><span data-stu-id="f6117-182">Canceling a queued task with <xref:System.Threading.RegisteredWaitHandle>.</span></span>  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f6117-183">参照</span><span class="sxs-lookup"><span data-stu-id="f6117-183">See Also</span></span>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [<span data-ttu-id="f6117-184">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="f6117-184">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [<span data-ttu-id="f6117-185">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="f6117-185">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [<span data-ttu-id="f6117-186">方法: タスクから値を返す</span><span class="sxs-lookup"><span data-stu-id="f6117-186">How to: Return a Value from a Task</span></span>](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [<span data-ttu-id="f6117-187">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="f6117-187">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="f6117-188">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="f6117-188">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 [<span data-ttu-id="f6117-189">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="f6117-189">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="f6117-190">タイマー</span><span class="sxs-lookup"><span data-stu-id="f6117-190">Timers</span></span>](../../../docs/standard/threading/timers.md)
