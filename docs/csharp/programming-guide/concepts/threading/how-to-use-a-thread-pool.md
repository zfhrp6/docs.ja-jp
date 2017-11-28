---
title: "方法: スレッド プールを使用する (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 210a9235-83a6-420b-af52-2d6a58e5133f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ad5ffb224821c67d227297f8a5a4a1476d77b0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thread-pool-c"></a><span data-ttu-id="1c99c-102">方法: スレッド プールを使用する (C#)</span><span class="sxs-lookup"><span data-stu-id="1c99c-102">How to: Use a Thread Pool (C#)</span></span>
<span data-ttu-id="1c99c-103">"*スレッド プール*" はマルチスレッドの 1 つの形式であり、タスクはキューに追加されて、スレッドが作成されると自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="1c99c-103">*Thread pooling* is a form of multithreading in which tasks are added to a queue and automatically started when threads are created.</span></span> <span data-ttu-id="1c99c-104">詳しくは、「[スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1c99c-104">For more information, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).</span></span>  
  
 <span data-ttu-id="1c99c-105">次の例では、.NET Framework のスレッド プールを使って、20 から 40 の間の 10 個の数字に対する `Fibonacci` の結果を計算しています。</span><span class="sxs-lookup"><span data-stu-id="1c99c-105">The following example uses the .NET Framework thread pool to calculate the `Fibonacci` result for ten numbers between 20 and 40.</span></span> <span data-ttu-id="1c99c-106">各 `Fibonacci` の結果は `Fibonacci` クラスによって表され、このクラスには計算を実行する `ThreadPoolCallback` という名前のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="1c99c-106">Each `Fibonacci` result is represented by the `Fibonacci` class, which provides a method named `ThreadPoolCallback` that performs the calculation.</span></span> <span data-ttu-id="1c99c-107">`Fibonacci` の各値を表すオブジェクトが作成され、`ThreadPoolCallback` メソッドが <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> に渡されます。このメソッドは、プール内の使用可能なスレッドを割り当てて、渡されたメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1c99c-107">An object that represents each `Fibonacci` value is created, and the `ThreadPoolCallback` method is passed to <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, which assigns an available thread in the pool to execute the method.</span></span>  
  
 <span data-ttu-id="1c99c-108">`Fibonacci` の各オブジェクトは計算のために準ランダムな値を提供され、各スレッドはプロセッサ時間を競合するため、10 個の結果すべてが計算されるまでにかかる時間を事前に知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="1c99c-108">Because each `Fibonacci` object is given a semi-random value to compute, and because each thread will be competing for processor time, you cannot know in advance how long it will take for all ten results to be calculated.</span></span> <span data-ttu-id="1c99c-109">そのため、各 `Fibonacci` オブジェクトには構築の間に <xref:System.Threading.ManualResetEvent> クラスのインスタンスを渡されます。</span><span class="sxs-lookup"><span data-stu-id="1c99c-109">That is why each `Fibonacci` object is passed an instance of the <xref:System.Threading.ManualResetEvent> class during construction.</span></span> <span data-ttu-id="1c99c-110">各オブジェクトは、計算が完了すると提供されたイベント オブジェクトに通知します。これにより、プライマリ スレッドは、10 個の `Fibonacci` オブジェクトすべてが結果を計算するまで、<xref:System.Threading.WaitHandle.WaitAll%2A> で実行をブロックできます。</span><span class="sxs-lookup"><span data-stu-id="1c99c-110">Each object signals the provided event object when its calculation is complete, which allows the primary thread to block execution with <xref:System.Threading.WaitHandle.WaitAll%2A> until all ten `Fibonacci` objects have calculated a result.</span></span> <span data-ttu-id="1c99c-111">その後、`Main` メソッドは各 `Fibonacci` の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="1c99c-111">The `Main` method then displays each `Fibonacci` result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c99c-112">例</span><span class="sxs-lookup"><span data-stu-id="1c99c-112">Example</span></span>  
  
```csharp  
using System;  
using System.Threading;  
  
public class Fibonacci  
{  
    private int _n;  
    private int _fibOfN;  
    private ManualResetEvent _doneEvent;  
  
    public int N { get { return _n; } }  
    public int FibOfN { get { return _fibOfN; } }  
  
    // Constructor.  
    public Fibonacci(int n, ManualResetEvent doneEvent)  
    {  
        _n = n;  
        _doneEvent = doneEvent;  
    }  
  
    // Wrapper method for use with thread pool.  
    public void ThreadPoolCallback(Object threadContext)  
    {  
        int threadIndex = (int)threadContext;  
        Console.WriteLine("thread {0} started...", threadIndex);  
        _fibOfN = Calculate(_n);  
        Console.WriteLine("thread {0} result calculated...", threadIndex);  
        _doneEvent.Set();  
    }  
  
    // Recursive method that calculates the Nth Fibonacci number.  
    public int Calculate(int n)  
    {  
        if (n <= 1)  
        {  
            return n;  
        }  
  
        return Calculate(n - 1) + Calculate(n - 2);  
    }  
}  
  
public class ThreadPoolExample  
{  
    static void Main()  
    {  
        const int FibonacciCalculations = 10;  
  
        // One event is used for each Fibonacci object.  
        ManualResetEvent[] doneEvents = new ManualResetEvent[FibonacciCalculations];  
        Fibonacci[] fibArray = new Fibonacci[FibonacciCalculations];  
        Random r = new Random();  
  
        // Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations);  
        for (int i = 0; i < FibonacciCalculations; i++)  
        {  
            doneEvents[i] = new ManualResetEvent(false);  
            Fibonacci f = new Fibonacci(r.Next(20, 40), doneEvents[i]);  
            fibArray[i] = f;  
            ThreadPool.QueueUserWorkItem(f.ThreadPoolCallback, i);  
        }  
  
        // Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents);  
        Console.WriteLine("All calculations are complete.");  
  
        // Display the results.  
        for (int i= 0; i<FibonacciCalculations; i++)  
        {  
            Fibonacci f = fibArray[i];  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1c99c-113">出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1c99c-113">Following is an example of the output.</span></span>  
  
```  
launching 10 tasks...  
thread 0 started...  
thread 1 started...  
thread 1 result calculated...  
thread 2 started...  
thread 2 result calculated...  
thread 3 started...  
thread 3 result calculated...  
thread 4 started...  
thread 0 result calculated...  
thread 5 started...  
thread 5 result calculated...  
thread 6 started...  
thread 4 result calculated...  
thread 7 started...  
thread 6 result calculated...  
thread 8 started...  
thread 8 result calculated...  
thread 9 started...  
thread 9 result calculated...  
thread 7 result calculated...  
All calculations are complete.  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(25) = 75025  
Fibonacci(22) = 17711  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(29) = 514229  
Fibonacci(38) = 39088169  
Fibonacci(21) = 10946  
Fibonacci(27) = 196418  
```  
  
## <a name="see-also"></a><span data-ttu-id="1c99c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c99c-114">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="1c99c-115">スレッド プール (C#)</span><span class="sxs-lookup"><span data-stu-id="1c99c-115">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="1c99c-116">スレッド処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="1c99c-116">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="1c99c-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1c99c-117">Security</span></span>](../../../../standard/security/index.md)
