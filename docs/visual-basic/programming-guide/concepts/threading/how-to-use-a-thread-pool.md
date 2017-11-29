---
title: "方法: スレッド プール (Visual Basic) を使用します。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42a4120900203eb7eb5ad8463fba4491636882b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thread-pool-visual-basic"></a><span data-ttu-id="3dd60-102">方法: スレッド プール (Visual Basic) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3dd60-102">How to: Use a Thread Pool (Visual Basic)</span></span>
<span data-ttu-id="3dd60-103">"*スレッド プール*" はマルチスレッドの 1 つの形式であり、タスクはキューに追加されて、スレッドが作成されると自動的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="3dd60-103">*Thread pooling* is a form of multithreading in which tasks are added to a queue and automatically started when threads are created.</span></span> <span data-ttu-id="3dd60-104">詳細については、次を参照してください。 [(Visual Basic) スレッドのプール](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)です。</span><span class="sxs-lookup"><span data-stu-id="3dd60-104">For more information, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).</span></span>  
  
 <span data-ttu-id="3dd60-105">次の例では、.NET Framework のスレッド プールを使って、20 から 40 の間の 10 個の数字に対する `Fibonacci` の結果を計算しています。</span><span class="sxs-lookup"><span data-stu-id="3dd60-105">The following example uses the .NET Framework thread pool to calculate the `Fibonacci` result for ten numbers between 20 and 40.</span></span> <span data-ttu-id="3dd60-106">各 `Fibonacci` の結果は `Fibonacci` クラスによって表され、このクラスには計算を実行する `ThreadPoolCallback` という名前のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="3dd60-106">Each `Fibonacci` result is represented by the `Fibonacci` class, which provides a method named `ThreadPoolCallback` that performs the calculation.</span></span> <span data-ttu-id="3dd60-107">`Fibonacci` の各値を表すオブジェクトが作成され、`ThreadPoolCallback` メソッドが <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> に渡されます。このメソッドは、プール内の使用可能なスレッドを割り当てて、渡されたメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="3dd60-107">An object that represents each `Fibonacci` value is created, and the `ThreadPoolCallback` method is passed to <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, which assigns an available thread in the pool to execute the method.</span></span>  
  
 <span data-ttu-id="3dd60-108">`Fibonacci` の各オブジェクトは計算のために準ランダムな値を提供され、各スレッドはプロセッサ時間を競合するため、10 個の結果すべてが計算されるまでにかかる時間を事前に知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="3dd60-108">Because each `Fibonacci` object is given a semi-random value to compute, and because each thread will be competing for processor time, you cannot know in advance how long it will take for all ten results to be calculated.</span></span> <span data-ttu-id="3dd60-109">そのため、各 `Fibonacci` オブジェクトには構築の間に <xref:System.Threading.ManualResetEvent> クラスのインスタンスを渡されます。</span><span class="sxs-lookup"><span data-stu-id="3dd60-109">That is why each `Fibonacci` object is passed an instance of the <xref:System.Threading.ManualResetEvent> class during construction.</span></span> <span data-ttu-id="3dd60-110">各オブジェクトは、計算が完了すると提供されたイベント オブジェクトに通知します。これにより、プライマリ スレッドは、10 個の `Fibonacci` オブジェクトすべてが結果を計算するまで、<xref:System.Threading.WaitHandle.WaitAll%2A> で実行をブロックできます。</span><span class="sxs-lookup"><span data-stu-id="3dd60-110">Each object signals the provided event object when its calculation is complete, which allows the primary thread to block execution with <xref:System.Threading.WaitHandle.WaitAll%2A> until all ten `Fibonacci` objects have calculated a result.</span></span> <span data-ttu-id="3dd60-111">その後、`Main` メソッドは各 `Fibonacci` の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="3dd60-111">The `Main` method then displays each `Fibonacci` result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dd60-112">例</span><span class="sxs-lookup"><span data-stu-id="3dd60-112">Example</span></span>  
  
```vb  
Imports System.Threading  
  
Module Module1  
  
    Public Class Fibonacci  
        Private _n As Integer  
        Private _fibOfN  
        Private _doneEvent As ManualResetEvent  
  
        Public ReadOnly Property N() As Integer  
            Get  
                Return _n  
            End Get  
        End Property  
  
        Public ReadOnly Property FibOfN() As Integer  
            Get  
                Return _fibOfN  
            End Get  
        End Property  
  
        Sub New(ByVal n As Integer, ByVal doneEvent As ManualResetEvent)  
            _n = n  
            _doneEvent = doneEvent  
        End Sub  
  
        ' Wrapper method for use with the thread pool.  
        Public Sub ThreadPoolCallBack(ByVal threadContext As Object)  
            Dim threadIndex As Integer = CType(threadContext, Integer)  
            Console.WriteLine("thread {0} started...", threadIndex)  
            _fibOfN = Calculate(_n)  
            Console.WriteLine("thread {0} result calculated...", threadIndex)  
            _doneEvent.Set()  
        End Sub  
  
        Public Function Calculate(ByVal n As Integer) As Integer  
            If n <= 1 Then  
                Return n  
            End If  
            Return Calculate(n - 1) + Calculate(n - 2)  
        End Function  
  
    End Class  
  
    <MTAThread()>   
    Sub Main()  
        Const FibonacciCalculations As Integer = 9 ' 0 to 9  
  
        ' One event is used for each Fibonacci object  
        Dim doneEvents(FibonacciCalculations) As ManualResetEvent  
        Dim fibArray(FibonacciCalculations) As Fibonacci  
        Dim r As New Random()  
  
        ' Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations)  
  
        For i As Integer = 0 To FibonacciCalculations  
            doneEvents(i) = New ManualResetEvent(False)  
            Dim f = New Fibonacci(r.Next(20, 40), doneEvents(i))  
            fibArray(i) = f  
            ThreadPool.QueueUserWorkItem(AddressOf f.ThreadPoolCallBack, i)  
        Next  
  
        ' Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents)  
        Console.WriteLine("All calculations are complete.")  
  
        ' Display the results.  
        For i As Integer = 0 To FibonacciCalculations  
            Dim f As Fibonacci = fibArray(i)  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN)  
        Next  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="3dd60-113">出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3dd60-113">Following is an example of the output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3dd60-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dd60-114">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="3dd60-115">スレッド プール (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dd60-115">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="3dd60-116">スレッド処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dd60-116">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="3dd60-117">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3dd60-117">Security</span></span>](../../../../standard/security/index.md)
