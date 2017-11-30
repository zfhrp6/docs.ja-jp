---
title: "マネージ スレッド処理の基本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a><span data-ttu-id="f4b91-102">マネージ スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="f4b91-102">Managed Threading Basics</span></span>
<span data-ttu-id="f4b91-103">このセクションの最初の 5 つのトピックでは、どのようなときか、マネージ スレッド処理を使用して、いくつかの基本的な機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="f4b91-104">その他の機能を提供するクラスについては、次を参照してください。[スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)と[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4b91-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="f4b91-105">このセクションでカバーのトピックの残りの部分には、Windows オペレーティング システムとマネージ スレッド処理とのやり取りなどのトピックが高度な。</span><span class="sxs-lookup"><span data-stu-id="f4b91-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4b91-106">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、タスク並列ライブラリおよび PLINQ は、マルチ スレッド プログラムでのタスクとデータの並列処理の Api を提供します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="f4b91-107">詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f4b91-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4b91-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f4b91-108">In This Section</span></span>  
 [<span data-ttu-id="f4b91-109">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="f4b91-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="f4b91-110">利点と、複数のスレッドの欠点について説明しするまたはスレッドを作成する場合があります、スレッド プールのスレッドを使用できるシナリオの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="f4b91-111">マネージ スレッドの例外</span><span class="sxs-lookup"><span data-stu-id="f4b91-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="f4b91-112">具体的には、ような状況で異なるバージョンの .NET Framework 用のスレッドでハンドルされない例外の動作を説明するその結果、アプリケーションの終了にします。</span><span class="sxs-lookup"><span data-stu-id="f4b91-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="f4b91-113">マルチスレッド処理のためのデータの同期</span><span class="sxs-lookup"><span data-stu-id="f4b91-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="f4b91-114">複数のスレッドで使用されるクラスのデータを同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="f4b91-115">マネージ スレッドの状態</span><span class="sxs-lookup"><span data-stu-id="f4b91-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="f4b91-116">基本的なスレッドの状態と、スレッドが実行されているかどうかを検出する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="f4b91-117">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="f4b91-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="f4b91-118">フォア グラウンドとバック グラウンド スレッド間の相違点をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="f4b91-119">Windows でのマネージ スレッド処理とアンマネージ スレッド処理</span><span class="sxs-lookup"><span data-stu-id="f4b91-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="f4b91-120">マネージ コードとアンマネージ スレッド処理の間のリレーションシップについて説明します、リスト相当するマネージ スレッド処理 Api、Windows 用および COM アパートメントおよびマネージ スレッドの相互作用について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="f4b91-121">Thread.Suspend、ガベージ コレクション、およびセーフ ポイント</span><span class="sxs-lookup"><span data-stu-id="f4b91-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="f4b91-122">スレッドの中断、ガベージ コレクションをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="f4b91-123">スレッド ローカル ストレージ: スレッド相対静的フィールドとデータ スロット</span><span class="sxs-lookup"><span data-stu-id="f4b91-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="f4b91-124">スレッドごとの相対ストレージ機構をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="f4b91-125">マネージ スレッドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="f4b91-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="f4b91-126">非同期操作または長時間同期操作について説明します、キャンセル トークンを使用して取り消されたことができます。</span><span class="sxs-lookup"><span data-stu-id="f4b91-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f4b91-127">参照</span><span class="sxs-lookup"><span data-stu-id="f4b91-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="f4b91-128">**Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="f4b91-129">実装する安全な方法は、ユーザー インターフェイス オブジェクトと共にマルチ スレッドです。</span><span class="sxs-lookup"><span data-stu-id="f4b91-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f4b91-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4b91-130">Related Sections</span></span>  
 [<span data-ttu-id="f4b91-131">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="f4b91-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="f4b91-132">複数のスレッドの活動を同期するために使用するマネージ クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="f4b91-133">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="f4b91-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="f4b91-134">に関する一般的な問題について説明するマルチ スレッドおよび問題を回避するための方法です。</span><span class="sxs-lookup"><span data-stu-id="f4b91-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="f4b91-135">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="f4b91-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="f4b91-136">タスク並列ライブラリおよび PLINQ では、非同期およびマルチ スレッドの .NET Framework アプリケーションを作成する作業を大幅に簡素化について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4b91-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
