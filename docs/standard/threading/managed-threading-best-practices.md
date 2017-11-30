---
title: "マネージ スレッド処理の実施"
ms.custom: 
ms.date: 11/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="9efed-102">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="9efed-102">Managed Threading Best Practices</span></span>
<span data-ttu-id="9efed-103">マルチスレッドには慎重なプログラミングが必要です。</span><span class="sxs-lookup"><span data-stu-id="9efed-103">Multithreading requires careful programming.</span></span> <span data-ttu-id="9efed-104">ほとんどのタスクでは、スレッド プールのスレッドを使って実行の要求をキューに置くことによって、処理の複雑さを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-104">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="9efed-105">このトピックでは、マルチ スレッド動作の調整や、ブロックするスレッドの処理など、より難しい状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="9efed-105">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9efed-106">複雑さの一部とマルチ スレッド プログラミングのリスクを軽減する Api は、.NET Framework 4 以降では Task Parallel Library および PLINQ から提供します。</span><span class="sxs-lookup"><span data-stu-id="9efed-106">Starting with the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="9efed-107">詳細については、次を参照してください。 [.NET での並行プログラミング](../../../docs/standard/parallel-programming/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9efed-107">For more information, see [Parallel Programming in .NET](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="9efed-108">デッドロックと競合状態</span><span class="sxs-lookup"><span data-stu-id="9efed-108">Deadlocks and Race Conditions</span></span>  
 <span data-ttu-id="9efed-109">マルチスレッドはスループットと応答速度の問題を解決しますが、その一方で、デッドロックと競合状態という新たな問題を発生させます。</span><span class="sxs-lookup"><span data-stu-id="9efed-109">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="9efed-110">デッドロック</span><span class="sxs-lookup"><span data-stu-id="9efed-110">Deadlocks</span></span>  
 <span data-ttu-id="9efed-111">デッドロックは、2 つのスレッドのうちの一方が、もう一方によって既にロックされているリソースをロックしようとすると発生します。</span><span class="sxs-lookup"><span data-stu-id="9efed-111">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="9efed-112">こうなると、どちらのスレッドも続行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9efed-112">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="9efed-113">マネージ スレッド処理クラスの多くのメソッドには、ロックアウトを検出するためのタイムアウト機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9efed-113">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="9efed-114">たとえば、次のコードがという名前のオブジェクトに対するロックを取得しようと`lockObject`です。</span><span class="sxs-lookup"><span data-stu-id="9efed-114">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="9efed-115">ロックが 300 ミリ秒単位で取得されていない場合<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>返します`false`です。</span><span class="sxs-lookup"><span data-stu-id="9efed-115">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="9efed-116">競合状態</span><span class="sxs-lookup"><span data-stu-id="9efed-116">Race Conditions</span></span>  
 <span data-ttu-id="9efed-117">競合状態は、2 つ以上のスレッドのうちのどれが特定のコード ブロックに最初に到達するかによって、プログラムの結果が変わってしまうバグのことです。</span><span class="sxs-lookup"><span data-stu-id="9efed-117">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="9efed-118">プログラムを何回か実行すると、異なる結果が得られ、実行の結果は予測できません。</span><span class="sxs-lookup"><span data-stu-id="9efed-118">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="9efed-119">競合状態の簡単な例として、フィールドのインクリメントがあります。</span><span class="sxs-lookup"><span data-stu-id="9efed-119">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="9efed-120">クラスにプライベートの **static** フィールド (Visual Basic では **Shared**) があり、このフィールドは、`objCt++;` (C# の場合) または `objCt += 1` (Visual Basic の場合) のようなコードを使用して、クラスのインスタンスが生成されるたびにインクリメントされるものとします。</span><span class="sxs-lookup"><span data-stu-id="9efed-120">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="9efed-121">この演算によって、`objCt` からレジスタへの値の読み込み、値のインクリメント、および `objCt` への値の格納が行われます。</span><span class="sxs-lookup"><span data-stu-id="9efed-121">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="9efed-122">マルチスレッドされたアプリケーションでは、値の読み込みとインクリメントを行ったスレッドが、この 3 つの処理を実行する別のスレッドに先を越される可能性があります。最初のスレッドは、実行を再開して値を格納するとき、待機中に値が変更されたかどうかを考慮せずに、`objCt` の値を上書きしてしまいます。</span><span class="sxs-lookup"><span data-stu-id="9efed-122">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="9efed-123">このような特定の競合状態は、<xref:System.Threading.Interlocked> など、<xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> クラスのメソッドを使用することによって容易に回避できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-123">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9efed-124">複数のスレッド間でデータを同期する他の手法については、「[マルチスレッド処理のためのデータの同期](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-124">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="9efed-125">競合状態は、複数のスレッドの動作を同期するときにも発生します。</span><span class="sxs-lookup"><span data-stu-id="9efed-125">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="9efed-126">コードを記述するときには、そのコードの行 (または行を構成する各マシン命令) を実行するスレッドが別のスレッドに追い越された場合に何が起きるのかを考慮しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9efed-126">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="number-of-processors"></a><span data-ttu-id="9efed-127">プロセッサの数</span><span class="sxs-lookup"><span data-stu-id="9efed-127">Number of Processors</span></span>  
 <span data-ttu-id="9efed-128">ほとんどのコンピューターは、タブレットや携帯電話のような小型のデバイスでさえも、複数のプロセッサ (コアともいいます) を持ちます。</span><span class="sxs-lookup"><span data-stu-id="9efed-128">Most computers now have multiple processors (also called cores), even small devices such as tablets and phones.</span></span> <span data-ttu-id="9efed-129">シングル プロセッサ コンピューターでも動作するソフトウェアを開発する場合は、マルチスレッドによってシングル プロセッサ コンピューターとマルチプロセッサ コンピューターとで異なる問題が解決される点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-129">If you know you're developing software that will also run on single-processor computers, you should be aware that multithreading solves different problems for single-processor computers and multiprocessor computers.</span></span>  
  
### <a name="multiprocessor-computers"></a><span data-ttu-id="9efed-130">マルチプロセッサ コンピューター</span><span class="sxs-lookup"><span data-stu-id="9efed-130">Multiprocessor Computers</span></span>  
 <span data-ttu-id="9efed-131">マルチスレッドによって、スループットが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="9efed-131">Multithreading provides greater throughput.</span></span> <span data-ttu-id="9efed-132">10 個のプロセッサは 1 個のプロセッサの 10 倍の仕事をします。ただし、これは仕事が分割され、10 個のプロセッサが同時に働いた場合です。スレッドを使用すると、簡単な方法で仕事を分割し、プロセッサの能力を活用できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-132">Ten processors can do ten times the work of one, but only if the work is divided so that all ten can be working at once; threads provide an easy way to divide the work and exploit the extra processing power.</span></span> <span data-ttu-id="9efed-133">マルチプロセッサ コンピューターでマルチスレッドを使用する場合は、次の点に注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="9efed-133">If you use multithreading on a multiprocessor computer:</span></span>  
  
-   <span data-ttu-id="9efed-134">同時に実行できるスレッドの数は、プロセッサの数によって制限されます。</span><span class="sxs-lookup"><span data-stu-id="9efed-134">The number of threads that can execute concurrently is limited by the number of processors.</span></span>  
  
-   <span data-ttu-id="9efed-135">実行されているフォアグラウンド スレッドの数がプロセッサの数よりも少ないときだけ、バックグラウンド スレッドが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9efed-135">A background thread executes only when the number of foreground threads executing is smaller than the number of processors.</span></span>  
  
-   <span data-ttu-id="9efed-136">スレッドで <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッドを呼び出しても、プロセッサの数と待機中のスレッドの数によっては、スレッドがすぐに開始されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9efed-136">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread might or might not start executing immediately, depending on the number of processors and the number of threads currently waiting to execute.</span></span>  
  
-   <span data-ttu-id="9efed-137">競合状態は、別のスレッドによる予期していなかった割り込みがあった場合に発生するだけでなく、別々のプロセッサで実行されている 2 つのスレッドが特定のコード ブロックに到達するタイミングによって発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9efed-137">Race conditions can occur not only because threads are preempted unexpectedly, but because two threads executing on different processors might be racing to reach the same code block.</span></span>  
  
### <a name="single-processor-computers"></a><span data-ttu-id="9efed-138">シングル プロセッサ コンピューター</span><span class="sxs-lookup"><span data-stu-id="9efed-138">Single-Processor Computers</span></span>  
 <span data-ttu-id="9efed-139">マルチスレッドによって、ユーザーへの応答速度が向上し、アイドル時間はバックグランド タスクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9efed-139">Multithreading provides greater responsiveness to the computer user, and uses idle time for background tasks.</span></span> <span data-ttu-id="9efed-140">シングル プロセッサ コンピューターでマルチスレッドを使用するときは、次の点に注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="9efed-140">If you use multithreading on a single-processor computer:</span></span>  
  
-   <span data-ttu-id="9efed-141">各瞬間には、1 つのスレッドだけが実行されています。</span><span class="sxs-lookup"><span data-stu-id="9efed-141">Only one thread runs at any instant.</span></span>  
  
-   <span data-ttu-id="9efed-142">バックグラウンド スレッドは、メイン ユーザー スレッドがアイドル状態のときだけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="9efed-142">A background thread executes only when the main user thread is idle.</span></span> <span data-ttu-id="9efed-143">フォアグラウンド スレッドが連続して実行されると、バックグラウンド スレッドのプロセッサ時間が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="9efed-143">A foreground thread that executes constantly starves background threads of processor time.</span></span>  
  
-   <span data-ttu-id="9efed-144">スレッドで <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> メソッドを呼び出しても、現在実行中のスレッドがプロセッサを解放するか、オペレーティング システムによって割り込まれるまでは、スレッドの実行が開始されません。</span><span class="sxs-lookup"><span data-stu-id="9efed-144">When you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method on a thread, that thread does not start executing until the current thread yields or is preempted by the operating system.</span></span>  
  
-   <span data-ttu-id="9efed-145">スレッドが別のスレッドに割り込まれてしまい、特定のコード ブロックに先に到達されてしまう可能性をプログラマが予測できていない場合に、競合状態が発生しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="9efed-145">Race conditions typically occur because the programmer did not anticipate the fact that a thread can be preempted at an awkward moment, sometimes allowing another thread to reach a code block first.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="9efed-146">静的メンバーと静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="9efed-146">Static Members and Static Constructors</span></span>  
 <span data-ttu-id="9efed-147">クラスは、そのクラス コンストラクター (C# では `static` コンストラクター、Visual Basic では `Shared Sub New`) の実行が完了するまで初期化されません。</span><span class="sxs-lookup"><span data-stu-id="9efed-147">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="9efed-148">初期化されていない型のコードの実行を防止するため、共通言語ランタイムは、クラス コンストラクターの実行が完了するまで、他のスレッドからのそのクラスの `static` メンバー (Visual Basic では `Shared` メンバー) 呼び出しをすべてブロックします。</span><span class="sxs-lookup"><span data-stu-id="9efed-148">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="9efed-149">たとえば、クラス コンストラクターが新しいスレッドを起動し、そのスレッドのプロシージャがクラスの `static` メンバーを呼び出した場合、その新しいスレッドは、クラス コンストラクターが完了するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="9efed-149">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="9efed-150">このことは、`static` コンストラクターを持つことができるすべての型に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="9efed-150">This applies to any type that can have a `static` constructor.</span></span>  
  
## <a name="general-recommendations"></a><span data-ttu-id="9efed-151">一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="9efed-151">General Recommendations</span></span>  
 <span data-ttu-id="9efed-152">マルチスレッドを使用するときは、以下のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-152">Consider the following guidelines when using multiple threads:</span></span>  
  
-   <span data-ttu-id="9efed-153">他のスレッドを終了させるために <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="9efed-153">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="9efed-154">他のスレッド **Abort** を呼び出すことは、そのスレッドの処理がどこまで到達しているかを把握せずに例外をスローするのと同じことになります。</span><span class="sxs-lookup"><span data-stu-id="9efed-154">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
-   <span data-ttu-id="9efed-155"><xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> と <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> を使用して複数のスレッドの動作を同期することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="9efed-155">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="9efed-156"><xref:System.Threading.Mutex>、<xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent>、および <xref:System.Threading.Monitor> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-156">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
-   <span data-ttu-id="9efed-157">メイン プログラムから、イベントなどを使用して、ワーカー スレッドの実行を制御しないでください。</span><span class="sxs-lookup"><span data-stu-id="9efed-157">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="9efed-158">ワーカー スレッドの側で、作業ができるようになるまでの待機、作業の実行、および実行終了後のプログラムへの通知を行うように、プログラムをデザインします。</span><span class="sxs-lookup"><span data-stu-id="9efed-158">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="9efed-159">ワーカー スレッドによるブロックを行わない場合は、スレッド プールのスレッドを使用することを考慮します。</span><span class="sxs-lookup"><span data-stu-id="9efed-159">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="9efed-160">ワーカー スレッドがブロックを行う場合は、<xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9efed-160"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
-   <span data-ttu-id="9efed-161">ロック オブジェクトとして型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9efed-161">Don't use types as lock objects.</span></span> <span data-ttu-id="9efed-162">つまり、C# の `lock(typeof(X))`、Visual Basic の `SyncLock(GetType(X))` などのコードを使用すること、または <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> を <xref:System.Type> オブジェクトと組み合わせて使用することを避けます。</span><span class="sxs-lookup"><span data-stu-id="9efed-162">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="9efed-163"><xref:System.Type?displayProperty=nameWithType> のインスタンスは、1 つの型につきアプリケーション ドメインごとに 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="9efed-163">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="9efed-164">ロックする型がパブリックの場合、自分以外のコードでもその型をロックできるため、デッドロックになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9efed-164">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="9efed-165">詳細については、「[信頼性に関するベスト プラクティス](../../../docs/framework/performance/reliability-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-165">For additional issues, see [Reliability Best Practices](../../../docs/framework/performance/reliability-best-practices.md).</span></span>  
  
-   <span data-ttu-id="9efed-166">インスタンスをロックする場合 (たとえば、C# の `lock(this)`、Visual Basic の `SyncLock(Me)`) には注意してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-166">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="9efed-167">アプリケーション内の、その型以外の他のコードがオブジェクトをロックすると、デッドロックが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="9efed-167">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
-   <span data-ttu-id="9efed-168">モニター状態に入った (ロックを取得した) スレッドは、モニター状態である間に例外が発生した場合でも、必ずモニター状態から出すようにします。</span><span class="sxs-lookup"><span data-stu-id="9efed-168">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="9efed-169">C#[ロック](~/docs/csharp/language-reference/keywords/lock-statement.md)ステートメントと Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md)ステートメントこの動作を自動的に提供を採用すること、 **finally**いることを確認するブロック<xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>はと呼ばれる。</span><span class="sxs-lookup"><span data-stu-id="9efed-169">The C# [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="9efed-170">**Exit** を確実に呼び出すことができない場合は、**Mutex** を使用するようにデザインを変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-170">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="9efed-171">ミューテックスは、現在それを保持しているスレッドが終了すると、自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="9efed-171">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
-   <span data-ttu-id="9efed-172">マルチ スレッドは異なるリソースを必要とするタスクに使用し、1 つのリソースに複数のスレッドを割り当てることがないように注意します。</span><span class="sxs-lookup"><span data-stu-id="9efed-172">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="9efed-173">たとえば、I/O を含む作業であれば、その作業専用のスレッドを用意すると有益です。I/O 操作の間、このスレッドはブロックを行いますが、他のスレッドは実行できるからです。</span><span class="sxs-lookup"><span data-stu-id="9efed-173">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="9efed-174">ユーザー入力も、専用のスレッドが役に立つリソースの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9efed-174">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="9efed-175">シングル プロセッサのコンピューターでは、計算中心のタスクがユーザー入力や I/O タスクと共存することはできますが、計算中心タスクどうしは競合してしまいます。</span><span class="sxs-lookup"><span data-stu-id="9efed-175">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
-   <span data-ttu-id="9efed-176">単純な状態変更については、<xref:System.Threading.Interlocked> ステートメント (Visual Basic では `lock`) ではなく、`SyncLock` クラスのメソッドの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="9efed-176">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="9efed-177">`lock` ステートメントは汎用的なツールとして優れていますが、<xref:System.Threading.Interlocked> クラスは、分離不可能な状態であることが必要な更新のパフォーマンスに優れています。</span><span class="sxs-lookup"><span data-stu-id="9efed-177">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="9efed-178">内部的には、競合がない場合は、単一の lock プレフィックスが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9efed-178">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="9efed-179">コードの校閲で、次に示す例のようなコードを探します。</span><span class="sxs-lookup"><span data-stu-id="9efed-179">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="9efed-180">最初の例では、状態変数をインクリメントしています。</span><span class="sxs-lookup"><span data-stu-id="9efed-180">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="9efed-181"><xref:System.Threading.Interlocked.Increment%2A> ステートメントの代わりに `lock` メソッドを次のように使用すると、パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-181">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9efed-182">.NET Framework Version 2.0 では、1 より大きなインクリメントでのアトミック更新を <xref:System.Threading.Interlocked.Add%2A> メソッドで実現できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-182">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method provides atomic updates in increments larger than 1.</span></span>  
  
     <span data-ttu-id="9efed-183">2 番目の例では、参照型の変数を、null 参照 (Visual Basic では `Nothing`) の場合にのみ更新しています。</span><span class="sxs-lookup"><span data-stu-id="9efed-183">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="9efed-184">この代わりに <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドを次のように使用すると、パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-184">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9efed-185">.NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.CompareExchange%2A> メソッドに、任意の参照型のタイプ セーフな置換に使用できるジェネリック オーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="9efed-185">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.CompareExchange%2A> method has a generic overload that can be used for type-safe replacement of any reference type.</span></span>  
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="9efed-186">クラス ライブラリに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="9efed-186">Recommendations for Class Libraries</span></span>  
 <span data-ttu-id="9efed-187">マルチスレッド用のクラス ライブラリをデザインするときには、次のガイドラインを検討します。</span><span class="sxs-lookup"><span data-stu-id="9efed-187">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
-   <span data-ttu-id="9efed-188">可能な限り、同期の必要を避けるようにします。</span><span class="sxs-lookup"><span data-stu-id="9efed-188">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="9efed-189">これは、頻繁に使用するコードの場合に特に言えます。</span><span class="sxs-lookup"><span data-stu-id="9efed-189">This is especially true for heavily used code.</span></span> <span data-ttu-id="9efed-190">たとえば、競合状態をなくすのではなく、競合状態に対応できるようにアルゴリズムを調整できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9efed-190">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="9efed-191">不要な同期があると、パフォーマンスが低下し、デッドロックや競合状態が発生する可能性が生じます。</span><span class="sxs-lookup"><span data-stu-id="9efed-191">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
-   <span data-ttu-id="9efed-192">静的なデータ (Visual Basic では `Shared`) は既定でスレッド セーフにします。</span><span class="sxs-lookup"><span data-stu-id="9efed-192">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
-   <span data-ttu-id="9efed-193">インスタンス データは既定でスレッド セーフにしないようにします。</span><span class="sxs-lookup"><span data-stu-id="9efed-193">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="9efed-194">スレッド セーフなコードを作成するロックを追加すると、パフォーマンスが低下し、ロックの競合が増加し、デッドロックが発生する可能性が生じます。</span><span class="sxs-lookup"><span data-stu-id="9efed-194">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="9efed-195">一般的なアプリケーション モデルでは、一度にユーザー コードを実行するスレッドは 1 つだけにして、スレッド セーフを実現する必要を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="9efed-195">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="9efed-196">この理由から、.NET Framework のクラス ライブラリは既定ではスレッド セーフではないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="9efed-196">For this reason, the .NET Framework class libraries are not thread safe by default.</span></span>  
  
-   <span data-ttu-id="9efed-197">静的状態を変更する静的メソッドは提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="9efed-197">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="9efed-198">一般的なサーバーのシナリオでは、静的状態は要求間で共有されます。つまり、複数のスレッドがそのコードを同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="9efed-198">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="9efed-199">これにより、スレッド処理のバグが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="9efed-199">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="9efed-200">要求間で共有されないインスタンスにデータをカプセル化するデザイン パターンの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="9efed-200">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="9efed-201">加えて、静的なデータを同期する場合は、状態を変更する呼び出しが静的メソッド間にあると、デッドロックや冗長な同期が生じる可能性があり、パフォーマンスに悪影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="9efed-201">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9efed-202">関連項目</span><span class="sxs-lookup"><span data-stu-id="9efed-202">See Also</span></span>  
 [<span data-ttu-id="9efed-203">スレッド化</span><span class="sxs-lookup"><span data-stu-id="9efed-203">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="9efed-204">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="9efed-204">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)
