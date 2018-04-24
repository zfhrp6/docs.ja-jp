---
title: タスク並列ライブラリ (TPL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET, concurrency in
- .NET, parallel programming in
- Parallel Programming
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: 37
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f63237e139e4be1d8cbb13e1534c894626fd72d
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="task-parallel-library-tpl"></a><span data-ttu-id="cd06a-102">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="cd06a-102">Task Parallel Library (TPL)</span></span>
<span data-ttu-id="cd06a-103">タスク並列ライブラリ (TPL: Task Parallel Library) は、<xref:System.Threading?displayProperty=nameWithType> 名前空間および <xref:System.Threading.Tasks?displayProperty=nameWithType> 名前空間におけるパブリック型と API のセットです。</span><span class="sxs-lookup"><span data-stu-id="cd06a-103">The Task Parallel Library (TPL) is a set of public types and APIs in the <xref:System.Threading?displayProperty=nameWithType> and <xref:System.Threading.Tasks?displayProperty=nameWithType> namespaces.</span></span> <span data-ttu-id="cd06a-104">TPL の目的は、アプリケーションに並列処理と同時実行を追加するプロセスを簡略化して、開発者の生産性を高めることです。</span><span class="sxs-lookup"><span data-stu-id="cd06a-104">The purpose of the TPL is to make developers more productive by simplifying the process of adding parallelism and concurrency to applications.</span></span> <span data-ttu-id="cd06a-105">TPL は、使用可能なすべてのプロセッサを最も効率的に使用するように、同時実行の程度を動的に拡大します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-105">The TPL scales the degree of concurrency dynamically to most efficiently use all the processors that are available.</span></span> <span data-ttu-id="cd06a-106">さらに TPL は、作業のパーティション分割、<xref:System.Threading.ThreadPool> 上のスレッドのスケジュール、キャンセルのサポート、状態管理、および他の低水準の詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-106">In addition, the TPL handles the partitioning of the work, the scheduling of threads on the <xref:System.Threading.ThreadPool>, cancellation support, state management, and other low-level details.</span></span> <span data-ttu-id="cd06a-107">TPL を使用すると、コードのパフォーマンスが大幅に向上し、目的を達成するためのプログラミング作業に集中できます。</span><span class="sxs-lookup"><span data-stu-id="cd06a-107">By using TPL, you can maximize the performance of your code while focusing on the work that your program is designed to accomplish.</span></span>  
  
 <span data-ttu-id="cd06a-108">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降では、マルチスレッド コードおよび並列コードを作成する際に TPL を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd06a-108">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the TPL is the preferred way to write multithreaded and parallel code.</span></span> <span data-ttu-id="cd06a-109">ただし、すべてのコードが並列化に適している訳ではありません。ループの各反復処理で少量の作業のみを実行する場合、または多数の反復処理のために実行しない場合、並列化のオーバーヘッドによってコードの実行が遅くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd06a-109">However, not all code is suitable for parallelization; for example, if a loop performs only a small amount of work on each iteration, or it doesn't run for many iterations, then the overhead of parallelization can cause the code to run more slowly.</span></span> <span data-ttu-id="cd06a-110">さらに、マルチスレッド コードのような並列化によって、プログラムの実行がより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="cd06a-110">Furthermore, parallelization like any multithreaded code adds complexity to your program execution.</span></span> <span data-ttu-id="cd06a-111">TPL はマルチスレッドのシナリオを簡略化しますが、たとえばロック、デッドロックおよび競合状態のスレッド処理の基本的な概念を理解し、TPL を効率的に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd06a-111">Although the TPL simplifies multithreaded scenarios, we recommend that you have a basic understanding of threading concepts, for example, locks, deadlocks, and race conditions, so that you can use the TPL effectively.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="cd06a-112">関連トピック</span><span class="sxs-lookup"><span data-stu-id="cd06a-112">Related Topics</span></span>  
  
|<span data-ttu-id="cd06a-113">Title</span><span class="sxs-lookup"><span data-stu-id="cd06a-113">Title</span></span>|<span data-ttu-id="cd06a-114">説明</span><span class="sxs-lookup"><span data-stu-id="cd06a-114">Description</span></span>|  
|-|-|  
|[<span data-ttu-id="cd06a-115">データの並列化</span><span class="sxs-lookup"><span data-stu-id="cd06a-115">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|<span data-ttu-id="cd06a-116">並列の `for` ループおよび `foreach` ループ (Visual Basic では `For` および `For Each`) を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-116">Describes how to create parallel `for` and `foreach` loops (`For` and `For Each` in Visual Basic).</span></span>|  
|[<span data-ttu-id="cd06a-117">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="cd06a-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|<span data-ttu-id="cd06a-118"><xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> を使用して暗黙的にタスクを作成および実行する方法、または <xref:System.Threading.Tasks.Task> オブジェクトを直接使用して明示的にタスクを作成および実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-118">Describes how to create and run tasks implicitly by using <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> or explicitly by using <xref:System.Threading.Tasks.Task> objects directly.</span></span>|  
|[<span data-ttu-id="cd06a-119">データフロー</span><span class="sxs-lookup"><span data-stu-id="cd06a-119">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|<span data-ttu-id="cd06a-120">相互に非同期通信を行う必要がある複数の操作を処理する場合、またはデータが使用可能になったときにデータを処理する場合に、TPL データ フロー ライブラリのデータ フロー コンポーネントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-120">Describes how to use the dataflow components in the TPL Dataflow Library to handle multiple operations that must communicate with one another or to process data as it becomes available.</span></span>|  
|[<span data-ttu-id="cd06a-121">TPL と他の非同期パターンの使用</span><span class="sxs-lookup"><span data-stu-id="cd06a-121">Using TPL with Other Asynchronous Patterns</span></span>](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|<span data-ttu-id="cd06a-122">TPL と他の非同期パターンを .NET で使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-122">Describes how to use TPL with other asynchronous patterns in .NET</span></span>|  
|[<span data-ttu-id="cd06a-123">データとタスクの並列化における注意点</span><span class="sxs-lookup"><span data-stu-id="cd06a-123">Potential Pitfalls in Data and Task Parallelism</span></span>](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|<span data-ttu-id="cd06a-124">一般的な落とし穴とその回避方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-124">Describes some common pitfalls and how to avoid them.</span></span>|  
|[<span data-ttu-id="cd06a-125">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="cd06a-125">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|<span data-ttu-id="cd06a-126">LINQ クエリでデータの並列化を達成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cd06a-126">Describes how to achieve data parallelism with LINQ queries.</span></span>|  
|[<span data-ttu-id="cd06a-127">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="cd06a-127">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)|<span data-ttu-id="cd06a-128">.NET 並列プログラミングのトップ レベル ノード。</span><span class="sxs-lookup"><span data-stu-id="cd06a-128">Top level node for .NET parallel programming.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd06a-129">参照</span><span class="sxs-lookup"><span data-stu-id="cd06a-129">See Also</span></span>  
 [<span data-ttu-id="cd06a-130">.NET Framework による並列プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="cd06a-130">Samples for Parallel Programming with the .NET Framework</span></span>](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
