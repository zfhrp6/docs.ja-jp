---
title: マネージ スレッド処理
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26f69429bb6ee479bd981474513698bf27993564
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="managed-threading"></a><span data-ttu-id="621ed-102">マネージ スレッド処理</span><span class="sxs-lookup"><span data-stu-id="621ed-102">Managed Threading</span></span>
<span data-ttu-id="621ed-103">アプリケーションを開発する場合、対象のコンピューターがプロセッサがシングルまたはマルチのいずれの場合でも、アプリケーションにユーザーとの迅速な対話を提供する必要があります。これはアプリケーションがほかの処理の実行中であっても同じことです。</span><span class="sxs-lookup"><span data-stu-id="621ed-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="621ed-104">アプリケーションによるユーザーへの迅速な応答を維持すると同時に、ユーザー イベントの合間やその処理中にプロセッサを使用する最も強力な方法は、複数の実行スレッドを使用することです。</span><span class="sxs-lookup"><span data-stu-id="621ed-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="621ed-105">ここでは、スレッド処理の基本概念について、マネージ スレッド処理の概念と使用方法を中心に説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="621ed-106">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> クラスおよび <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラス、[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=nameWithType> 名前空間の新しい同時実行コレクション クラス、スレッドではなくタスクの概念をベースにした新しいプログラミング モデルにより、マルチスレッド プログラミングが大幅に簡略化されています。</span><span class="sxs-lookup"><span data-stu-id="621ed-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="621ed-107">詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="621ed-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="621ed-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="621ed-108">In This Section</span></span>  
 [<span data-ttu-id="621ed-109">マネージ スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="621ed-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="621ed-110">マネージ スレッド処理の概要と、マルチ スレッドをどのようなときに使用するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="621ed-111">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="621ed-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="621ed-112">スレッドの作成、開始、一時停止、再開、および中止について説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="621ed-113">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="621ed-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="621ed-114">同期のレベル、デッドロックと競合状態の回避方法、シングル プロセッサのコンピューターとマルチ プロセッサのコンピューターの問題など、スレッド処理の各種の注意点について説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, single-processor and multiprocessor computers, and other threading issues.</span></span>  
  
 [<span data-ttu-id="621ed-115">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="621ed-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="621ed-116">スレッドの動作や、別のスレッドによってアクセスされるオブジェクトのデータを同期するために使用するマネージ クラスについて説明し、スレッド プールのスレッドの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="621ed-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="621ed-117">参照</span><span class="sxs-lookup"><span data-stu-id="621ed-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="621ed-118">マネージ スレッドを使用したり同期したりするためのクラスを含みます。</span><span class="sxs-lookup"><span data-stu-id="621ed-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="621ed-119">複数のスレッドで使用する安全なコレクション クラスを含みます。</span><span class="sxs-lookup"><span data-stu-id="621ed-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="621ed-120">同時処理タスクを作成およびスケジュールするためのクラスを含みます。</span><span class="sxs-lookup"><span data-stu-id="621ed-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="621ed-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="621ed-121">Related Sections</span></span>  
 [<span data-ttu-id="621ed-122">アプリケーション ドメイン</span><span class="sxs-lookup"><span data-stu-id="621ed-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="621ed-123">アプリケーション ドメインと、その共通言語インフラストラクチャでの使用に関する概要を示します。</span><span class="sxs-lookup"><span data-stu-id="621ed-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="621ed-124">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="621ed-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="621ed-125">非同期 I/O のパフォーマンス上の利点と基本的な操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="621ed-126">タスク ベースの非同期パターン (TAP)</span><span class="sxs-lookup"><span data-stu-id="621ed-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="621ed-127">.NET での非同期プログラミングの推奨パターンの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="621ed-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="621ed-128">同期メソッドの非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="621ed-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="621ed-129">デリゲートの組み込み機能を使用してスレッド プールのスレッドでメソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="621ed-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="621ed-130">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="621ed-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="621ed-131">アプリケーションで複数のスレッドを簡単に使用できるようにする並列プログラミング ライブラリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="621ed-132">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="621ed-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="621ed-133">複数のプロセッサを利用するために、クエリを並列で実行するシステムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="621ed-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
