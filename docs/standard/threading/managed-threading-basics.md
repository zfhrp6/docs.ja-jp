---
title: マネージ スレッド処理の基本
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fa91bb22de6492815f79bfd50e1fefc800c6047
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="managed-threading-basics"></a><span data-ttu-id="e1ec1-102">マネージ スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="e1ec1-102">Managed Threading Basics</span></span>
<span data-ttu-id="e1ec1-103">このセクションの最初の 5 つのトピックは、マネージ スレッド処理を使用するタイミングを判断するのに役立つように設計されており、また、いくつかの基本的な機能について説明するためのものです。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="e1ec1-104">その他の機能を提供するクラスについては、「[スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)」と「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="e1ec1-105">このセクションの残りのトピックには、マネージ スレッド処理と Windows オペレーティング システムとの相互作用など、高度なトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1ec1-106">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、タスク並列ライブラリと PLINQ は、マルチスレッド プログラムでのタスクとデータの並列処理のための API を提供します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="e1ec1-107">詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1ec1-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e1ec1-108">In This Section</span></span>  
 [<span data-ttu-id="e1ec1-109">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="e1ec1-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="e1ec1-110">複数のスレッドの利点と欠点について説明し、スレッドを作成またはスレッド プール スレッドを使用する可能性のあるシナリオの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="e1ec1-111">マネージ スレッドの例外</span><span class="sxs-lookup"><span data-stu-id="e1ec1-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="e1ec1-112">さまざまなバージョンの .NET Framework のスレッドでのハンドルされていない例外の動作、特に、アプリケーションの終了の原因となる状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="e1ec1-113">マルチスレッド処理のためのデータの同期</span><span class="sxs-lookup"><span data-stu-id="e1ec1-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="e1ec1-114">複数のスレッドで使用されるクラスのデータを同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="e1ec1-115">マネージ スレッドの状態</span><span class="sxs-lookup"><span data-stu-id="e1ec1-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="e1ec1-116">基本的なスレッドの状態と、スレッドが実行されているかどうかの検出方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="e1ec1-117">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="e1ec1-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="e1ec1-118">フォアグラウンド スレッドとバック グラウンド スレッドの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="e1ec1-119">Windows でのマネージ スレッド処理とアンマネージ スレッド処理</span><span class="sxs-lookup"><span data-stu-id="e1ec1-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="e1ec1-120">マネージ スレッド処理とアンマネージ スレッド処理の関係について説明し、Windows のスレッド処理 API に相当するマネージ API をリストし、COM アパートメントとマネージ スレッドの相互作用について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="e1ec1-121">Thread.Suspend、ガベージ コレクション、およびセーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="e1ec1-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="e1ec1-122">スレッドの中断とガベージ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="e1ec1-123">スレッド ローカル ストレージ: スレッド相対静的フィールドとデータ スロット</span><span class="sxs-lookup"><span data-stu-id="e1ec1-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="e1ec1-124">スレッド相対ストレージ メカニズムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="e1ec1-125">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="e1ec1-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="e1ec1-126">取り消しトークンを使用して、非同期または長時間実行されている同期操作の取り消し方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e1ec1-127">参照</span><span class="sxs-lookup"><span data-stu-id="e1ec1-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="e1ec1-128">**Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="e1ec1-129">ユーザー インターフェイス オブジェクトと共にマルチスレッドを実装するための安全な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1ec1-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1ec1-130">Related Sections</span></span>  
 [<span data-ttu-id="e1ec1-131">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="e1ec1-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="e1ec1-132">複数のスレッドのアクティビティを同期するために使用されるマネージ クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="e1ec1-133">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="e1ec1-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="e1ec1-134">マルチスレッドに関する一般的な問題と、問題を回避するための方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="e1ec1-135">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="e1ec1-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="e1ec1-136">非同期およびマルチスレッドの .NET Framework アプリケーションを作成する作業を大幅に簡素化する、タスク並列ライブラリと PLINQ について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ec1-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
