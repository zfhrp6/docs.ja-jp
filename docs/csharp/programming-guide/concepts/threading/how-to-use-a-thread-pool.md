---
title: "方法: スレッド プールを使用する (C#)"
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
ms.assetid: 210a9235-83a6-420b-af52-2d6a58e5133f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f90262cdfa6e4d6c8c37c553e999d51fee736d6a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-a-thread-pool-c"></a>方法: スレッド プールを使用する (C#)
"*スレッド プール*" はマルチスレッドの 1 つの形式であり、タスクはキューに追加されて、スレッドが作成されると自動的に開始されます。 詳しくは、「[スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)」をご覧ください。  
  
 次の例では、.NET Framework のスレッド プールを使って、20 から 40 の間の 10 個の数字に対する `Fibonacci` の結果を計算しています。 各 `Fibonacci` の結果は `Fibonacci` クラスによって表され、このクラスには計算を実行する `ThreadPoolCallback` という名前のメソッドがあります。 `Fibonacci` の各値を表すオブジェクトが作成され、`ThreadPoolCallback` メソッドが <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> に渡されます。このメソッドは、プール内の使用可能なスレッドを割り当てて、渡されたメソッドを実行します。  
  
 `Fibonacci` の各オブジェクトは計算のために準ランダムな値を提供され、各スレッドはプロセッサ時間を競合するため、10 個の結果すべてが計算されるまでにかかる時間を事前に知ることはできません。 そのため、各 `Fibonacci` オブジェクトには構築の間に <xref:System.Threading.ManualResetEvent> クラスのインスタンスを渡されます。 各オブジェクトは、計算が完了すると提供されたイベント オブジェクトに通知します。これにより、プライマリ スレッドは、10 個の `Fibonacci` オブジェクトすべてが結果を計算するまで、<xref:System.Threading.WaitHandle.WaitAll%2A> で実行をブロックできます。 その後、`Main` メソッドは各 `Fibonacci` の結果を表示します。  
  
## <a name="example"></a>例  
  
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
  
 出力の例を次に示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Mutex>   
 <xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.EventWaitHandle.Set%2A>   
 <xref:System.Threading.ThreadPool>   
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading.ManualResetEvent>   
 [スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)   
 [スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)   
 @System.Threading.Monitor   
 [セキュリティ](../../../../standard/security/index.md)

