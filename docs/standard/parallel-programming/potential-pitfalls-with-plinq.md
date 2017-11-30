---
title: "PLINQ の非利便性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="a0742-102">PLINQ の非利便性</span><span class="sxs-lookup"><span data-stu-id="a0742-102">Potential Pitfalls with PLINQ</span></span>
<span data-ttu-id="a0742-103">多くの場合、PLINQ は、順次の LINQ to Objects クエリ経由で大幅なパフォーマンス向上を提供できます。</span><span class="sxs-lookup"><span data-stu-id="a0742-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="a0742-104">ただし、クエリの実行を並列化には、問題が発生するの順次のコードに、一般的ではないまたはめったにない可能性がある複雑さが導入されています。</span><span class="sxs-lookup"><span data-stu-id="a0742-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="a0742-105">このトピックでは、PLINQ クエリを記述するときを防ぐためのいくつかの事項を示します。</span><span class="sxs-lookup"><span data-stu-id="a0742-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="a0742-106">並列処理が常に高速であると思い込まない</span><span class="sxs-lookup"><span data-stu-id="a0742-106">Do Not Assume That Parallel Is Always Faster</span></span>  
 <span data-ttu-id="a0742-107">並列処理こともありますが、PLINQ クエリを同等のオブジェクトに、LINQ より時間がかかります実行発生します。</span><span class="sxs-lookup"><span data-stu-id="a0742-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="a0742-108">基本的な経験則は、いくつかのソース要素とユーザーの簡易デリゲートを持つクエリがないことにより高速化する可能性がはるかです。</span><span class="sxs-lookup"><span data-stu-id="a0742-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="a0742-109">ただし、パフォーマンスには、多くの要因が関係する、ため PLINQ を使用するかどうかを決定する前に、実際の結果を測定することお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a0742-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="a0742-110">詳細については、「[Understanding Speedup in PLINQ (PLINQ での高速化について)](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0742-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="a0742-111">共有メモリの位置への書き込みを回避する</span><span class="sxs-lookup"><span data-stu-id="a0742-111">Avoid Writing to Shared Memory Locations</span></span>  
 <span data-ttu-id="a0742-112">逐次コードでは、静的変数またはクラス フィールドから読み取ることや、これらの場所に書き込むことはよくあります。</span><span class="sxs-lookup"><span data-stu-id="a0742-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="a0742-113">ただし、複数のスレッドからこのような変数に同時にアクセスしているときは、著しい競合状態になる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="a0742-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="a0742-114">ロックを使用して変数へのアクセスを同期できる場合でも、同期のコストでパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="a0742-115">したがって、することを避けるため、または少なくとも制限可能な限り PLINQ クエリ内の共有状態へのアクセスをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a0742-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>  
  
## <a name="avoid-over-parallelization"></a><span data-ttu-id="a0742-116">過剰な並列化を回避する</span><span class="sxs-lookup"><span data-stu-id="a0742-116">Avoid Over-Parallelization</span></span>  
 <span data-ttu-id="a0742-117">使用して、`AsParallel`ソース コレクションを分割して、ワーカー スレッドの同期のオーバーヘッド コストが発生する演算子です。</span><span class="sxs-lookup"><span data-stu-id="a0742-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="a0742-118">並列化の利点は、コンピューター上のプロセッサ数によってさらに制限されます。</span><span class="sxs-lookup"><span data-stu-id="a0742-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="a0742-119">1 つのプロセッサで複数の計算主体のスレッドを実行しても、高速化は実現しません。</span><span class="sxs-lookup"><span data-stu-id="a0742-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="a0742-120">したがって、過剰なクエリの並列化しないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-120">Therefore, you must be careful not to over-parallelize a query.</span></span>  
  
 <span data-ttu-id="a0742-121">最も一般的なシナリオでは、次のスニペットに示すように、入れ子になったクエリではどの過剰な並列化が発生することができます。</span><span class="sxs-lookup"><span data-stu-id="a0742-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 <span data-ttu-id="a0742-122">ここを次の条件の 1 つ以上を適用しない限り、外部データ ソース (顧客) だけを並列化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a0742-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>  
  
-   <span data-ttu-id="a0742-123">内部データ ソース (cust です。注文) は非常に長い呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a0742-123">The inner data source (cust.Orders) is known to be very long.</span></span>  
  
-   <span data-ttu-id="a0742-124">各順序で高負荷の計算を実行している </span><span class="sxs-lookup"><span data-stu-id="a0742-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="a0742-125">(この例に示す操作の負荷は大きくありません)。</span><span class="sxs-lookup"><span data-stu-id="a0742-125">(The operation shown in the example is not expensive.)</span></span>  
  
-   <span data-ttu-id="a0742-126">対象システムに、`cust.Orders` でクエリを並列化することで生成されるスレッドの数を十分に処理できるプロセッサが存在している。</span><span class="sxs-lookup"><span data-stu-id="a0742-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>  
  
 <span data-ttu-id="a0742-127">どの場合も、最適なクエリの形式を決定する最善の方法は、テストおよび測定することです。</span><span class="sxs-lookup"><span data-stu-id="a0742-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="a0742-128">詳細については、次を参照してください。[する方法: PLINQ クエリのパフォーマンスを測定](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0742-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="a0742-129">スレッド セーフでないメソッドの呼び出しを回避する</span><span class="sxs-lookup"><span data-stu-id="a0742-129">Avoid Calls to Non-Thread-Safe Methods</span></span>  
 <span data-ttu-id="a0742-130">クエリは、PLINQ から非スレッド セーフなインスタンス メソッドへの書き込みがあり、プログラムで検出されない可能性がありますいないデータが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="a0742-131">例外が発生する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="a0742-131">It can also lead to exceptions.</span></span> <span data-ttu-id="a0742-132">次の例では、複数のスレッドとする呼び出しを試みると、`Filestream.Write`メソッド、クラスによってサポートされていない、同時にします。</span><span class="sxs-lookup"><span data-stu-id="a0742-132">In the following example, multiple threads would be attempting to call the `Filestream.Write` method simultaneously, which is not supported by the class.</span></span>  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="a0742-133">スレッド セーフなメソッドの呼び出しを制限する</span><span class="sxs-lookup"><span data-stu-id="a0742-133">Limit Calls to Thread-Safe Methods</span></span>  
 <span data-ttu-id="a0742-134">.NET Framework のほとんどの静的メソッドはスレッド セーフであり、複数のスレッドから同時に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a0742-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="a0742-135">ただし、このような場合でも、関連する同期によっては、クエリの処理速度が大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0742-136">テストできますこの自分でいくつかの呼び出しを挿入することで<xref:System.Console.WriteLine%2A>クエリにします。</span><span class="sxs-lookup"><span data-stu-id="a0742-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="a0742-137">このメソッドは、デモンストレーションのためのドキュメントの例で使用されますが、PLINQ クエリで使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a0742-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>  
  
## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="a0742-138">不要な並べ替え操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="a0742-138">Avoid Unnecessary Ordering Operations</span></span>  
 <span data-ttu-id="a0742-139">PLINQ では、並列クエリを実行したときに、ソース シーケンスを処理できる同時に複数のスレッドでのパーティションに分割します。</span><span class="sxs-lookup"><span data-stu-id="a0742-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="a0742-140">既定では、パーティションが処理され、結果が配信されるの順序は予測可能な (などの演算子を除く`OrderBy`)。</span><span class="sxs-lookup"><span data-stu-id="a0742-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="a0742-141">任意のソース シーケンスの順序を保持するために PLINQ に指示できますが、パフォーマンスに悪影響を及ぼしますこれです。</span><span class="sxs-lookup"><span data-stu-id="a0742-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="a0742-142">ベスト プラクティス、可能な限りはクエリを構築する順序の維持に依存しないようにします。</span><span class="sxs-lookup"><span data-stu-id="a0742-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="a0742-143">詳細については、「[Order Preservation in PLINQ (PLINQ における順序維持)](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0742-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="a0742-144">ForAll (_n) 可能であれば ForEach と</span><span class="sxs-lookup"><span data-stu-id="a0742-144">Prefer ForAll to ForEach When It Is Possible</span></span>  
 <span data-ttu-id="a0742-145">PLINQ クエリを実行、複数のスレッドの結果を処理する場合は、`foreach`ループ (`For Each` Visual Basic で)、クエリの結果を 1 つのスレッドに反映され、列挙子が順番にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="a0742-146">場合によっては、これは回避できません。ただし、可能な限り、使用、`ForAll`など、スレッド セーフ コレクションへの書き込みなど、独自の結果を出力するには、各スレッドを有効にするメソッド<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="a0742-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="a0742-147">同じ問題の適用対象<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>言い換えれば、`source.AsParallel().Where().ForAll(...)`を強く推奨される必要があります</span><span class="sxs-lookup"><span data-stu-id="a0742-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>  
  
 <span data-ttu-id="a0742-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`。</span><span class="sxs-lookup"><span data-stu-id="a0742-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>  
  
## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="a0742-149">スレッド アフィニティの問題に注意する</span><span class="sxs-lookup"><span data-stu-id="a0742-149">Be Aware of Thread Affinity Issues</span></span>  
 <span data-ttu-id="a0742-150">シングル スレッド アパートメント (STA) コンポーネント向けの COM 相互運用性、Windows フォーム、Windows Presentation Foundation (WPF) などの一部のテクノロジでは、特定のスレッド上で実行するコードを必要とするスレッド アフィニティが制限される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="a0742-151">たとえば、Windows フォームと WPF では、コントロールへのアクセスは、そのコントロールが作成されたスレッド上でしか行うことができません。</span><span class="sxs-lookup"><span data-stu-id="a0742-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="a0742-152">PLINQ クエリの Windows フォーム コントロールの共有状態にアクセスしようとする場合は、デバッガーで実行している場合に、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="a0742-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="a0742-153">(この設定はオフにすることができます)。ただし場合、UI スレッドで、クエリを使用すると、し、アクセスできますからコントロール、 `foreach` 1 つのスレッドでそのコードが実行されるため、クエリを列挙するループになります。</span><span class="sxs-lookup"><span data-stu-id="a0742-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="a0742-154">ForEach、For および ForAll のイテレーションが必ず並列実行されているとは限らない</span><span class="sxs-lookup"><span data-stu-id="a0742-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>  
 <span data-ttu-id="a0742-155">その個々 の繰り返しに留意することが重要な<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>または<xref:System.Linq.ParallelEnumerable.ForAll%2A>月のループが並列で実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a0742-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="a0742-156">そのため、イテレーションの並列実行の正確性、または特定の順序でのイテレーションの実行の正確性に依存するコードを記述しないでください。</span><span class="sxs-lookup"><span data-stu-id="a0742-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>  
  
 <span data-ttu-id="a0742-157">たとえば、次のコードはデッドロックが起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-157">For example, this code is likely to deadlock:</span></span>  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
                                                     If j = Environment.ProcessorCount Then  
  
                                                         Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Set()  
  
                                                     Else  
  
                                                         Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Wait()  
                                                     End If  
    End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
            {  
                if (j == Environment.ProcessorCount)  
                {  
                    Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Set();  
                }  
                else  
                {  
                    Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Wait();  
                }  
            }); //deadlocks  
```  
  
 <span data-ttu-id="a0742-158">この例では、1 つのイテレーションでイベントを設定し、その他のすべてのイテレーションでイベントを待機します。</span><span class="sxs-lookup"><span data-stu-id="a0742-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="a0742-159">待機のイテレーションは、イベント設定のイテレーションが完了するまで完了できません。</span><span class="sxs-lookup"><span data-stu-id="a0742-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="a0742-160">ただし、待機のイテレーションによって、並列ループの実行に使用されるすべてのスレッドがブロックされ、イベント設定のイテレーションがまったく実行されなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="a0742-161">これにより、イベント設定のイテレーションが実行されず、待機のイテレーションが開始されないままの状態になるデッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="a0742-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>  
  
 <span data-ttu-id="a0742-162">具体的には、処理を適切に進めるには、並列ループの特定のイテレーションでそのループの別のイテレーションを待機するのは避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0742-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="a0742-163">並列ループで、イテレーションが逆の順序で順次スケジュールされた場合、デッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="a0742-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0742-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0742-164">See Also</span></span>  
 [<span data-ttu-id="a0742-165">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a0742-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
