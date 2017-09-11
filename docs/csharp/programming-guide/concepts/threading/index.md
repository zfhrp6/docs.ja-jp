---
title: "スレッド処理 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 45ffa38254717c9aee29c3922bf801f6a90c716e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="threading-c"></a><span data-ttu-id="12e7a-102">スレッド処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-102">Threading (C#)</span></span>
<span data-ttu-id="12e7a-103">スレッド処理により、C# プログラムが同時処理を実行できるようになり、一度に複数の操作を行うことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-103">Threading enables your C# program to perform concurrent processing so that you can do more than one operation at a time.</span></span> <span data-ttu-id="12e7a-104">たとえば、スレッド処理を使用してユーザーの入力を監視したり、バックグラウンド タスクを実行したり、入力の同時ストリームを処理したりできます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-104">For example, you can use threading to monitor input from the user, perform background tasks, and handle simultaneous streams of input.</span></span>  
  
 <span data-ttu-id="12e7a-105">スレッドには次のようなプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-105">Threads have the following properties:</span></span>  
  
-   <span data-ttu-id="12e7a-106">スレッドにより、プログラムの同時処理の実行が可能になります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-106">Threads enable your program to perform concurrent processing.</span></span>  
  
-   <span data-ttu-id="12e7a-107">.NET Framework の <xref:System.Threading> 名前空間により、スレッドの使用が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-107">The .NET Framework <xref:System.Threading> namespace makes using threads easier.</span></span>  
  
-   <span data-ttu-id="12e7a-108">スレッドは、アプリケーションのリソースを共有します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-108">Threads share the application's resources.</span></span> <span data-ttu-id="12e7a-109">詳細については、「[Using Threads and Threading](https://msdn.microsoft.com/library/e1dx6b2h)」(スレッドの使用とスレッド処理) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12e7a-109">For more information, see [Using Threads and Threading](https://msdn.microsoft.com/library/e1dx6b2h).</span></span>  
  
 <span data-ttu-id="12e7a-110">既定では、C# プログラムにはスレッドが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-110">By default, a C# program has one thread.</span></span> <span data-ttu-id="12e7a-111">ただし、補助スレッドを作成し、プライマリ スレッドと並行してコードを実行するために使用することができます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-111">However, auxiliary threads can be created and used to execute code in parallel with the primary thread.</span></span> <span data-ttu-id="12e7a-112">このようなスレッドは、よく*ワーカー スレッド*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-112">These threads are often called *worker threads*.</span></span>  
  
 <span data-ttu-id="12e7a-113">ワーカー スレッドを使用すると、プライマリ スレッドに拘束されることなく、時間がかかるタスクやタイム クリティカルなタスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-113">Worker threads can be used to perform time-consuming or time-critical tasks without tying up the primary thread.</span></span> <span data-ttu-id="12e7a-114">たとえば、ワーカー スレッドは、前の要求が完了するのを待たずに受信する要求を処理するために、サーバー アプリケーションで多く使用されます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-114">For example, worker threads are often used in server applications to fulfill incoming requests without waiting for the previous request to be completed.</span></span> <span data-ttu-id="12e7a-115">ワーカー スレッドは、デスクトップ アプリケーションで "バックグラウンド" タスクを実行するためにも使用されます。これにより、ユーザー インターフェイス要素を動かすメイン スレッドは引き続きユーザー操作に応答できます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-115">Worker threads are also used to perform "background" tasks in desktop applications so that the main thread--which drives user interface elements--remains responsive to user actions.</span></span>  
  
 <span data-ttu-id="12e7a-116">スレッド処理はスループットと応答速度の問題を解決しますが、その一方で、デッドロックや競合状態のようなリソース共有の問題を発生させます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-116">Threading solves problems with throughput and responsiveness, but it can also introduce resource-sharing issues such as deadlocks and race conditions.</span></span> <span data-ttu-id="12e7a-117">複数のスレッドは、ファイル ハンドルやネットワーク接続など、さまざまなリソースを必要とするタスクに最適です。</span><span class="sxs-lookup"><span data-stu-id="12e7a-117">Multiple threads are best for tasks that require different resources such as file handles and network connections.</span></span> <span data-ttu-id="12e7a-118">複数のスレッドを 1 つのリソースに割り当てると、同期の問題が発生しやすくなり、他のスレッドの待機中に頻繁にブロックされるスレッドがあると、複数のスレッドを使用する目的が果たされなくなります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-118">Assigning multiple threads to a single resource is likely to cause synchronization issues, and having threads frequently blocked when waiting for other threads defeats the purpose of using multiple threads.</span></span>  
  
 <span data-ttu-id="12e7a-119">一般的な方法としては、ワーカー スレッドを使用して、他のスレッドで使用されるリソースをあまり必要としない、時間がかかるタスクやタイム クリティカルなタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-119">A common strategy is to use worker threads to perform time-consuming or time-critical tasks that do not require many of the resources used by other threads.</span></span> <span data-ttu-id="12e7a-120">当然ながら、プログラムの一部のリソースは、複数のスレッドによってアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-120">Naturally, some resources in your program must be accessed by multiple threads.</span></span> <span data-ttu-id="12e7a-121">このような場合に、<xref:System.Threading> 名前空間によってスレッドを同期するためのクラスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="12e7a-121">For these cases, the <xref:System.Threading> namespace provides classes for synchronizing threads.</span></span> <span data-ttu-id="12e7a-122">これらのクラスには、<xref:System.Threading.Mutex>、<xref:System.Threading.Monitor>、<xref:System.Threading.Interlocked>、<xref:System.Threading.AutoResetEvent>、および <xref:System.Threading.ManualResetEvent> があります。</span><span class="sxs-lookup"><span data-stu-id="12e7a-122">These classes include <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.ManualResetEvent>.</span></span>  
  
 <span data-ttu-id="12e7a-123">これらのクラスの一部またはすべてを使用して、複数のスレッドのアクティビティを同期できますが、スレッド処理一部のサポートは C# 言語によりサポートされています。</span><span class="sxs-lookup"><span data-stu-id="12e7a-123">You can use some or all these classes to synchronize the activities of multiple threads, but some support for threading is supported by the C# language.</span></span> <span data-ttu-id="12e7a-124">たとえば、[lock ステートメント](../../../../csharp/language-reference/keywords/lock-statement.md)は、<xref:System.Threading.Monitor> を暗黙的に使用することで同期機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-124">For example, the [Lock Statement](../../../../csharp/language-reference/keywords/lock-statement.md) provides synchronization features through implicit use of <xref:System.Threading.Monitor>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12e7a-125">[!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)] 以降では、<xref:System.Threading.Tasks.Parallel?displayProperty=fullName> クラスおよび <xref:System.Threading.Tasks.Task?displayProperty=fullName> クラス、[Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688)、<xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間の新しい同時実行コレクション クラス、スレッドではなくタスクの概念をベースにした新しいプログラミング モデルにより、マルチスレッド プログラミングが大幅に簡略化されています。</span><span class="sxs-lookup"><span data-stu-id="12e7a-125">Beginning with the [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=fullName> and <xref:System.Threading.Tasks.Task?displayProperty=fullName> classes, [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=fullName> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="12e7a-126">詳細については、[並列プログラミング](https://msdn.microsoft.com/library/dd460693)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="12e7a-126">For more information, see [Parallel Programming](https://msdn.microsoft.com/library/dd460693).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="12e7a-127">関連トピック</span><span class="sxs-lookup"><span data-stu-id="12e7a-127">Related Topics</span></span>  
  
|<span data-ttu-id="12e7a-128">タイトル</span><span class="sxs-lookup"><span data-stu-id="12e7a-128">Title</span></span>|<span data-ttu-id="12e7a-129">説明</span><span class="sxs-lookup"><span data-stu-id="12e7a-129">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="12e7a-130">マルチスレッド アプリケーション (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-130">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|<span data-ttu-id="12e7a-131">スレッドの作成方法および使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-131">Describes how to create and use threads.</span></span>|  
|[<span data-ttu-id="12e7a-132">マルチスレッド プロシージャのパラメーターと戻り値 (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-132">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|<span data-ttu-id="12e7a-133">マルチ スレッド アプリケーションでパラメーターを受け渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-133">Describes how to pass and return parameters with multithreaded applications.</span></span>|  
|[<span data-ttu-id="12e7a-134">チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-134">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|<span data-ttu-id="12e7a-135">簡単なマルチスレッド アプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-135">Shows how to create a simple multithreaded application.</span></span>|  
|[<span data-ttu-id="12e7a-136">スレッドの同期 (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-136">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|<span data-ttu-id="12e7a-137">スレッドの相互作用を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-137">Describes how to control the interactions of threads.</span></span>|  
|[<span data-ttu-id="12e7a-138">スレッド タイマー (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-138">Thread Timers (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|<span data-ttu-id="12e7a-139">一定の間隔で個別のスレッド上でプロシージャを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-139">Describes how to run procedures on separate threads at fixed intervals.</span></span>|  
|[<span data-ttu-id="12e7a-140">スレッド プール (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-140">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|<span data-ttu-id="12e7a-141">システムで管理されるワーカー スレッドのプールを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-141">Describes how to use a pool of worker threads that are managed by the system.</span></span>|  
|[<span data-ttu-id="12e7a-142">方法: スレッド プールを使用する (C#)</span><span class="sxs-lookup"><span data-stu-id="12e7a-142">How to: Use a Thread Pool (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|<span data-ttu-id="12e7a-143">スレッド プール内の複数スレッドの同期された使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-143">Demonstrates synchronized use of multiple threads in the thread pool.</span></span>|  
|[<span data-ttu-id="12e7a-144">スレッド化</span><span class="sxs-lookup"><span data-stu-id="12e7a-144">Threading</span></span>](https://msdn.microsoft.com/library/3e8s7xdd)|<span data-ttu-id="12e7a-145">.NET Framework でのスレッドの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12e7a-145">Describes how to implement threading in the .NET Framework.</span></span>|

