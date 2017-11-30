---
title: "スレッド処理オブジェクトと機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="a8417-102">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="a8417-102">Threading Objects and Features</span></span>
<span data-ttu-id="a8417-103">.NET Framework には、マルチスレッド アプリケーションの作成と管理に役立つ多くのオブジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a8417-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="a8417-104">マネージ スレッドは、<xref:System.Threading.Thread> クラスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="a8417-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="a8417-105"><xref:System.Threading.ThreadPool> クラスを使用すると、マルチスレッドのバックグラウンド タスクを簡単に作成し、管理できます。</span><span class="sxs-lookup"><span data-stu-id="a8417-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="a8417-106"><xref:System.ComponentModel.BackgroundWorker> クラスは、ユーザー インターフェイスと対話するタスクについてそれと同じことを実現します。</span><span class="sxs-lookup"><span data-stu-id="a8417-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="a8417-107"><xref:System.Threading.Timer> クラスは、指定された間隔でバックグラウンド タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="a8417-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="a8417-108">さらに、.NET Framework Version 2.0 で導入された <xref:System.Threading.Semaphore> クラスや <xref:System.Threading.EventWaitHandle> クラスなど、スレッドの活動を同期するクラスも数多くあります。</span><span class="sxs-lookup"><span data-stu-id="a8417-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a8417-109">これらのクラスの機能の比較については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8417-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8417-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a8417-110">In This Section</span></span>  
 [<span data-ttu-id="a8417-111">マネージ スレッド プール</span><span class="sxs-lookup"><span data-stu-id="a8417-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="a8417-112">**ThreadPool** クラスについて説明します。このクラスを利用すると、開発者はスレッド管理を意識する必要なく、スレッドにタスクの実行を要求できます。</span><span class="sxs-lookup"><span data-stu-id="a8417-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="a8417-113">タイマー</span><span class="sxs-lookup"><span data-stu-id="a8417-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="a8417-114">**Timer** を使用して、指定された時間に呼び出されるデリゲートを指定する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="a8417-115">モニター</span><span class="sxs-lookup"><span data-stu-id="a8417-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="a8417-116">**Monitor** クラスを使用してメンバーへのアクセスを同期したり、独自の種類のスレッド管理を構築したりする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="a8417-117">待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="a8417-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="a8417-118"><xref:System.Threading.WaitHandle> クラスについて説明します。このクラスは、イベント待機ハンドル、ミューテックス、およびセマフォ用の抽象基底クラスで、複数の同期イベントを待機できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a8417-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="a8417-119">EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a8417-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="a8417-120">通知を行ったり通知を待機したりすることによりスレッドの活動を同期するために使用するマネージ イベント待機ハンドルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="a8417-121">ミューテックス</span><span class="sxs-lookup"><span data-stu-id="a8417-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="a8417-122">使用する方法について説明します、<xref:System.Threading.Mutex>オブジェクトへのアクセスを同期するために、または独自の同期機構を構築します。</span><span class="sxs-lookup"><span data-stu-id="a8417-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="a8417-123">インタロックされた操作</span><span class="sxs-lookup"><span data-stu-id="a8417-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="a8417-124"><xref:System.Threading.Interlocked> クラスを使用して、値の増減と値の格納をアトミックな 1 回の操作で実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="a8417-125">読み取り/書き込みロック</span><span class="sxs-lookup"><span data-stu-id="a8417-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="a8417-126">単一ライター/複数リーダーのセマンティクスを実装するロックを定義します。</span><span class="sxs-lookup"><span data-stu-id="a8417-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="a8417-127">Semaphore と SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="a8417-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="a8417-128"><xref:System.Threading.Semaphore> オブジェクトについて説明し、このオブジェクトを使用して、制限されたリソースへのアクセスを制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8417-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="a8417-129">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="a8417-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="a8417-130">マネージ スレッドをロックおよび同期するために用意されている .NET Framework のクラスの機能を比較します。</span><span class="sxs-lookup"><span data-stu-id="a8417-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="a8417-131">バリア</span><span class="sxs-lookup"><span data-stu-id="a8417-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="a8417-132">段階的な操作におけるスレッドの調整のためのバリア パターンを実装する <xref:System.Threading.Barrier> オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="a8417-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="a8417-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="a8417-134">特定の下位レベルのシナリオで Monitor クラスの代わりに軽量のプリミティブとして使用できる <xref:System.Threading.SpinLock> について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="a8417-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="a8417-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="a8417-136">カーネル ベースの待機を開始する前にビジー スピンを実行する下位レベルの同期プリミティブである <xref:System.Threading.SpinWait> について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a8417-137">参照</span><span class="sxs-lookup"><span data-stu-id="a8417-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="a8417-138">**Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="a8417-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="a8417-139">ユーザー インターフェイスと対話し、ユーザー インターフェイス スレッドで生成されるイベントを介して通信するバックグラウンド タスクを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a8417-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a8417-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8417-140">Related Sections</span></span>  
 [<span data-ttu-id="a8417-141">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="a8417-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="a8417-142">入力/出力操作が完了した場合にのみ非同期 I/O 完了ポートがスレッド プールを使用して処理を要求する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="a8417-143">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="a8417-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="a8417-144">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降でマルチスレッド プログラミングのための推奨される方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8417-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
