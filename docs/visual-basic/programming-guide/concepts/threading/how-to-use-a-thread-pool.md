---
title: "方法: スレッド プール (Visual Basic) を使用する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a86eabe40c91d96fc236c0a0de3ff668b855b9ab
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-a-thread-pool-visual-basic"></a><span data-ttu-id="5154b-102">方法: スレッド プール (Visual Basic) を使用します。</span><span class="sxs-lookup"><span data-stu-id="5154b-102">How to: Use a Thread Pool (Visual Basic)</span></span>
<span data-ttu-id="5154b-103">*スレッド プール*の形式は、どのタスクがキューに追加され、スレッドを作成するときに自動的に開始のマルチ スレッド処理します。</span><span class="sxs-lookup"><span data-stu-id="5154b-103">*Thread pooling* is a form of multithreading in which tasks are added to a queue and automatically started when threads are created.</span></span> <span data-ttu-id="5154b-104">詳細については、次を参照してください。 [(Visual Basic) スレッド プール](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)します。</span><span class="sxs-lookup"><span data-stu-id="5154b-104">For more information, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).</span></span>  
  
 <span data-ttu-id="5154b-105">次の例で、.NET Framework スレッド プールを使用して、計算、 `Fibonacci` 20 ~ 40 の間の 10 個の数字の結果。</span><span class="sxs-lookup"><span data-stu-id="5154b-105">The following example uses the .NET Framework thread pool to calculate the `Fibonacci` result for ten numbers between 20 and 40.</span></span> <span data-ttu-id="5154b-106">各`Fibonacci`で結果を表す、`Fibonacci`という名前のメソッドを提供するクラス`ThreadPoolCallback`計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="5154b-106">Each `Fibonacci` result is represented by the `Fibonacci` class, which provides a method named `ThreadPoolCallback` that performs the calculation.</span></span> <span data-ttu-id="5154b-107">それぞれを表すオブジェクト`Fibonacci`値を作成すると、および`ThreadPoolCallback`をメソッドに渡されます<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>、メソッドの実行にプールで利用可能なスレッドが割り当てられます</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>。</span><span class="sxs-lookup"><span data-stu-id="5154b-107">An object that represents each `Fibonacci` value is created, and the `ThreadPoolCallback` method is passed to <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, which assigns an available thread in the pool to execute the method.</span></span>  
  
 <span data-ttu-id="5154b-108">各`Fibonacci`オブジェクトにを計算するための半ランダムな値が指定され、ため、各スレッドは、プロセッサ時間の競合は、事前に時間が&10; 個すべての結果を計算するを知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="5154b-108">Because each `Fibonacci` object is given a semi-random value to compute, and because each thread will be competing for processor time, you cannot know in advance how long it will take for all ten results to be calculated.</span></span> <span data-ttu-id="5154b-109">そういう各`Fibonacci`オブジェクトには、インスタンスが渡される、<xref:System.Threading.ManualResetEvent>の構築時にクラス</xref:System.Threading.ManualResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="5154b-109">That is why each `Fibonacci` object is passed an instance of the <xref:System.Threading.ManualResetEvent> class during construction.</span></span> <span data-ttu-id="5154b-110">各オブジェクトが指定されたイベント オブジェクトに通知の計算が終了すると、これにより、プライマリ スレッドで実行をブロックする<xref:System.Threading.WaitHandle.WaitAll%2A>10 まで`Fibonacci`オブジェクトが、結果を計算します</xref:System.Threading.WaitHandle.WaitAll%2A>。</span><span class="sxs-lookup"><span data-stu-id="5154b-110">Each object signals the provided event object when its calculation is complete, which allows the primary thread to block execution with <xref:System.Threading.WaitHandle.WaitAll%2A> until all ten `Fibonacci` objects have calculated a result.</span></span> <span data-ttu-id="5154b-111">`Main`メソッドは、それぞれ表示`Fibonacci`結果。</span><span class="sxs-lookup"><span data-stu-id="5154b-111">The `Main` method then displays each `Fibonacci` result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5154b-112">例</span><span class="sxs-lookup"><span data-stu-id="5154b-112">Example</span></span>  
  
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
  
 <span data-ttu-id="5154b-113">出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5154b-113">Following is an example of the output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5154b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5154b-114">See Also</span></span>  
 <span data-ttu-id="5154b-115"><xref:System.Threading.Mutex></xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="5154b-115"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="5154b-116"><xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A></span><span class="sxs-lookup"><span data-stu-id="5154b-116"><xref:System.Threading.WaitHandle.WaitAll%2A></span></span>   
 <span data-ttu-id="5154b-117"><xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent></span><span class="sxs-lookup"><span data-stu-id="5154b-117"><xref:System.Threading.ManualResetEvent></span></span>   
 <span data-ttu-id="5154b-118"><xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A></span><span class="sxs-lookup"><span data-stu-id="5154b-118"><xref:System.Threading.EventWaitHandle.Set%2A></span></span>   
 <span data-ttu-id="5154b-119"><xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool></span><span class="sxs-lookup"><span data-stu-id="5154b-119"><xref:System.Threading.ThreadPool></span></span>   
 <span data-ttu-id="5154b-120"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="5154b-120"><xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span></span>   
 <span data-ttu-id="5154b-121"><xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent></span><span class="sxs-lookup"><span data-stu-id="5154b-121"><xref:System.Threading.ManualResetEvent></span></span>   
<span data-ttu-id="5154b-122"> [スレッド プール (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span><span class="sxs-lookup"><span data-stu-id="5154b-122"> [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span></span>  
<span data-ttu-id="5154b-123"> [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="5154b-123"> [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
 @System.Threading.Monitor   
<span data-ttu-id="5154b-124"> [セキュリティ](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)</span><span class="sxs-lookup"><span data-stu-id="5154b-124"> [Security](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)</span></span>
