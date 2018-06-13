---
title: PLINQ の非利便性
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73ec2d2fb73ee95b39a15307d136c35542578c41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591717"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="44f11-102">PLINQ の非利便性</span><span class="sxs-lookup"><span data-stu-id="44f11-102">Potential Pitfalls with PLINQ</span></span>
<span data-ttu-id="44f11-103">PLINQ を使用すると、多くの場合、連続した LINQ to Objects クエリのパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="44f11-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="44f11-104">ただし、クエリの実行を並列化すると、複雑性が増すため、シーケンシャルなコードにおいて一般的でない問題、またはめったにない問題を引き起こす場合があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="44f11-105">このトピックでは、PLINQ クエリを記述するときに回避すべき点について示します。</span><span class="sxs-lookup"><span data-stu-id="44f11-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a><span data-ttu-id="44f11-106">並列処理が常に高速であると思い込まない</span><span class="sxs-lookup"><span data-stu-id="44f11-106">Do Not Assume That Parallel Is Always Faster</span></span>  
 <span data-ttu-id="44f11-107">並列化することで、PLINQ クエリの実行速度が同等の LINQ to Objects より遅くなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="44f11-108">基本的な経験則では、ソース要素が少なく、高速ユーザー デリゲートを使用するクエリの速度が大幅に向上することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="44f11-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="44f11-109">ただし、パフォーマンスには多くの要因が関係するため、実際の結果を測定してから、PLINQ を使用するかどうかを決定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="44f11-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="44f11-110">詳細については、「[Understanding Speedup in PLINQ (PLINQ での高速化について)](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44f11-110">For more information, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="44f11-111">共有メモリの位置への書き込みを回避する</span><span class="sxs-lookup"><span data-stu-id="44f11-111">Avoid Writing to Shared Memory Locations</span></span>  
 <span data-ttu-id="44f11-112">逐次コードでは、静的変数またはクラス フィールドから読み取ることや、これらの場所に書き込むことはよくあります。</span><span class="sxs-lookup"><span data-stu-id="44f11-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="44f11-113">ただし、複数のスレッドからこのような変数に同時にアクセスしているときは、著しい競合状態になる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="44f11-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="44f11-114">ロックを使用して変数へのアクセスを同期できる場合でも、同期のコストでパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="44f11-115">このため、PLINQ クエリにおける共有状態へのアクセスは、できるだけ回避するか、少なくとも制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="44f11-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>  
  
## <a name="avoid-over-parallelization"></a><span data-ttu-id="44f11-116">過剰な並列化を回避する</span><span class="sxs-lookup"><span data-stu-id="44f11-116">Avoid Over-Parallelization</span></span>  
 <span data-ttu-id="44f11-117">`AsParallel` を使用することで、ソース コレクションのパーティション分割とワーカー スレッドの同期によるオーバーヘッド コストが発生します。</span><span class="sxs-lookup"><span data-stu-id="44f11-117">By using the `AsParallel` operator, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="44f11-118">並列化の利点は、コンピューター上のプロセッサ数によってさらに制限されます。</span><span class="sxs-lookup"><span data-stu-id="44f11-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="44f11-119">1 つのプロセッサで複数の計算主体のスレッドを実行しても、高速化は実現しません。</span><span class="sxs-lookup"><span data-stu-id="44f11-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="44f11-120">そのため、クエリを過剰に並列処理しないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-120">Therefore, you must be careful not to over-parallelize a query.</span></span>  
  
 <span data-ttu-id="44f11-121">過剰な並列化が発生する可能性が特に高い一般的な状況は、次のスニペットで示すように、入れ子になったクエリの場合です。</span><span class="sxs-lookup"><span data-stu-id="44f11-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 <span data-ttu-id="44f11-122">この場合、次の条件のうち 1 つ以上該当しない限り、外側のデータ ソース (customers) のみを並列化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="44f11-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>  
  
-   <span data-ttu-id="44f11-123">内部データ ソース (cust.Orders) が非常に長い。</span><span class="sxs-lookup"><span data-stu-id="44f11-123">The inner data source (cust.Orders) is known to be very long.</span></span>  
  
-   <span data-ttu-id="44f11-124">各順序で高負荷の計算を実行している </span><span class="sxs-lookup"><span data-stu-id="44f11-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="44f11-125">(この例に示す操作の負荷は大きくありません)。</span><span class="sxs-lookup"><span data-stu-id="44f11-125">(The operation shown in the example is not expensive.)</span></span>  
  
-   <span data-ttu-id="44f11-126">対象システムに、`cust.Orders` でクエリを並列化することで生成されるスレッドの数を十分に処理できるプロセッサが存在している。</span><span class="sxs-lookup"><span data-stu-id="44f11-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>  
  
 <span data-ttu-id="44f11-127">どの場合も、最適なクエリの形式を決定する最善の方法は、テストおよび測定することです。</span><span class="sxs-lookup"><span data-stu-id="44f11-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="44f11-128">詳細については、「[方法: PLINQ クエリのパフォーマンスを測定する](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44f11-128">For more information, see [How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).</span></span>  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="44f11-129">スレッド セーフでないメソッドの呼び出しを回避する</span><span class="sxs-lookup"><span data-stu-id="44f11-129">Avoid Calls to Non-Thread-Safe Methods</span></span>  
 <span data-ttu-id="44f11-130">PLINQ クエリからスレッド セーフでないインスタンス メソッドに書き込むと、プログラムで検出されない可能性のあるデータ破損が起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="44f11-131">例外が発生する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="44f11-131">It can also lead to exceptions.</span></span> <span data-ttu-id="44f11-132">次の例では、複数のスレッドが、クラスでサポートされていない `Filestream.Write` メソッドの同時呼び出しを試みます。</span><span class="sxs-lookup"><span data-stu-id="44f11-132">In the following example, multiple threads would be attempting to call the `Filestream.Write` method simultaneously, which is not supported by the class.</span></span>  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="44f11-133">スレッド セーフなメソッドの呼び出しを制限する</span><span class="sxs-lookup"><span data-stu-id="44f11-133">Limit Calls to Thread-Safe Methods</span></span>  
 <span data-ttu-id="44f11-134">.NET Framework のほとんどの静的メソッドはスレッド セーフであり、複数のスレッドから同時に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="44f11-134">Most static methods in the .NET Framework are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="44f11-135">ただし、このような場合でも、関連する同期によっては、クエリの処理速度が大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44f11-136">これは、クエリに <xref:System.Console.WriteLine%2A> の呼び出しをいくつか挿入することで自分でテストできます。</span><span class="sxs-lookup"><span data-stu-id="44f11-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="44f11-137">このメソッドは、ドキュメントの例でデモのために使用されていますが、PLINQ クエリでは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="44f11-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>  
  
## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="44f11-138">不要な並べ替え操作を回避する</span><span class="sxs-lookup"><span data-stu-id="44f11-138">Avoid Unnecessary Ordering Operations</span></span>  
 <span data-ttu-id="44f11-139">PLINQ を使用して 1 つのクエリを並列で実行すると、ソース シーケンスがパーティションに分割され、複数のスレッド上で同時に操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="44f11-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="44f11-140">既定では、パーティションが処理される順序と生成される結果は予測できません (`OrderBy` などの演算子を除く)。</span><span class="sxs-lookup"><span data-stu-id="44f11-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="44f11-141">PLINQ に、ソース シーケンスの順序を維持するように指示することもできますが、この操作はパフォーマンスの低下を招きます。</span><span class="sxs-lookup"><span data-stu-id="44f11-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="44f11-142">推奨される手順は、できる限り、順序の維持に依存しないようにクエリを構成することです。</span><span class="sxs-lookup"><span data-stu-id="44f11-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="44f11-143">詳細については、「[Order Preservation in PLINQ (PLINQ における順序維持)](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44f11-143">For more information, see [Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).</span></span>  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="44f11-144">できる限り ForEach より ForAll を優先する</span><span class="sxs-lookup"><span data-stu-id="44f11-144">Prefer ForAll to ForEach When It Is Possible</span></span>  
 <span data-ttu-id="44f11-145">PLINQ では複数のスレッドで 1 つのクエリを実行しますが、`foreach` ループ (Visual Basic の場合は `For Each`) の結果を処理する場合、クエリ結果は 1 つのスレッドにマージされてから列挙子によって連続してアクセスされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="44f11-146">これが避けられない場合もありますが、できる限り `ForAll` メソッドを使用して各スレッドで固有の結果を出力できるようにします。たとえば、<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> などのスレッド セーフなコレクションに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="44f11-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="44f11-147">つまり、同じ問題が <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> にも適用されます。つまり、`source.AsParallel().Where().ForAll(...)` が以下のものよりも強く求められます。</span><span class="sxs-lookup"><span data-stu-id="44f11-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to</span></span>  
  
 <span data-ttu-id="44f11-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`。</span><span class="sxs-lookup"><span data-stu-id="44f11-148">`Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>  
  
## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="44f11-149">スレッド アフィニティの問題に注意する</span><span class="sxs-lookup"><span data-stu-id="44f11-149">Be Aware of Thread Affinity Issues</span></span>  
 <span data-ttu-id="44f11-150">シングル スレッド アパートメント (STA) コンポーネント向けの COM 相互運用性、Windows フォーム、Windows Presentation Foundation (WPF) などの一部のテクノロジでは、特定のスレッド上で実行するコードを必要とするスレッド アフィニティが制限される場合があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="44f11-151">たとえば、Windows フォームと WPF では、コントロールへのアクセスは、そのコントロールが作成されたスレッド上でしか行うことができません。</span><span class="sxs-lookup"><span data-stu-id="44f11-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="44f11-152">PLINQ クエリで Windows フォーム コントロールの共有状態にアクセスしようとすると、デバッガーを実行中である場合は例外が発生します </span><span class="sxs-lookup"><span data-stu-id="44f11-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="44f11-153">(この設定はオフにできます)。ただし、クエリが UI スレッドで処理される場合、コードは 1 つのスレッドでのみ実行されるので、クエリ結果を列挙する `foreach` ループからコントロールにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="44f11-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="44f11-154">ForEach、For および ForAll のイテレーションが必ず並列実行されているとは限らない</span><span class="sxs-lookup"><span data-stu-id="44f11-154">Do Not Assume that Iterations of ForEach, For and ForAll Always Execute in Parallel</span></span>  
 <span data-ttu-id="44f11-155"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>、または <xref:System.Linq.ParallelEnumerable.ForAll%2A> の各ループにおける個々の反復処理が必ずしも並列実行されるとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="44f11-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="44f11-156">そのため、イテレーションの並列実行の正確性、または特定の順序でのイテレーションの実行の正確性に依存するコードを記述しないでください。</span><span class="sxs-lookup"><span data-stu-id="44f11-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>  
  
 <span data-ttu-id="44f11-157">たとえば、次のコードはデッドロックが起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-157">For example, this code is likely to deadlock:</span></span>  
  
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
  
 <span data-ttu-id="44f11-158">この例では、1 つのイテレーションでイベントを設定し、その他のすべてのイテレーションでイベントを待機します。</span><span class="sxs-lookup"><span data-stu-id="44f11-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="44f11-159">待機のイテレーションは、イベント設定のイテレーションが完了するまで完了できません。</span><span class="sxs-lookup"><span data-stu-id="44f11-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="44f11-160">ただし、待機のイテレーションによって、並列ループの実行に使用されるすべてのスレッドがブロックされ、イベント設定のイテレーションがまったく実行されなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="44f11-161">これにより、イベント設定のイテレーションが実行されず、待機のイテレーションが開始されないままの状態になるデッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="44f11-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>  
  
 <span data-ttu-id="44f11-162">具体的には、処理を適切に進めるには、並列ループの特定のイテレーションでそのループの別のイテレーションを待機するのは避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="44f11-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="44f11-163">並列ループで、イテレーションが逆の順序で順次スケジュールされた場合、デッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="44f11-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f11-164">参照</span><span class="sxs-lookup"><span data-stu-id="44f11-164">See Also</span></span>  
 [<span data-ttu-id="44f11-165">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="44f11-165">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
