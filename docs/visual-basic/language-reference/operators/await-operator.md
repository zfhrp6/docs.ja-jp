---
title: Await 演算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d639d1398c0f783fcfa40ee9ff278922fd6fc7b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="1207b-102">Await 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1207b-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="1207b-103">`Await` 演算子は、非同期のメソッドまたはラムダ式のオペランドに適用されて、待機中のタスクが完了するまでメソッドの実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="1207b-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="1207b-104">このタスクは、進行中の作業を表します。</span><span class="sxs-lookup"><span data-stu-id="1207b-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="1207b-105">メソッドに`Await`が使用する必要があります、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="1207b-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="1207b-106">このようなメソッド (`Async` 修飾子を使用して定義され、通常 1 つ以上の `Await` 式を含むメソッド) を "*非同期メソッド*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="1207b-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1207b-107">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="1207b-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="1207b-108">非同期のプログラミングの概要については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="1207b-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="1207b-109">適用するタスクでは通常、`Await`演算子を実装するメソッドへの呼び出しからの戻り値、[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=204847),、つまり、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>です。</span><span class="sxs-lookup"><span data-stu-id="1207b-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="1207b-110">次のコードでは、<xref:System.Net.Http.HttpClient> メソッドの <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> が `getContentsTask` (`Task(Of Byte())`) を返します。</span><span class="sxs-lookup"><span data-stu-id="1207b-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="1207b-111">これにより、操作が完了したときに実際のバイト配列が生成されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="1207b-112">`Await` 演算子が `getContentsTask` に適用されているため、`SumPageSizesAsync` が完了するまで `getContentsTask` の実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="1207b-113">その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="1207b-114">`getContentsTask` が終了すると、`Await` 式がバイト配列に評価されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="1207b-115">完全な例については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1207b-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="1207b-116">Microsoft Web サイトの[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)からサンプルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1207b-116">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="1207b-117">この例は AsyncWalkthrough_HttpClient プロジェクトにあります。</span><span class="sxs-lookup"><span data-stu-id="1207b-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="1207b-118">`Await` を返すメソッド呼び出しの結果に `Task(Of TResult)` が適用されている場合、`Await` 式の型は TResult になります。</span><span class="sxs-lookup"><span data-stu-id="1207b-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="1207b-119">`Await` を返すメソッド呼び出しの結果に `Task` が適用されている場合、`Await` 式は値を返しません。</span><span class="sxs-lookup"><span data-stu-id="1207b-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="1207b-120">この違いを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="1207b-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="1207b-121">`Await` 式またはステートメントは、自身が実行されているスレッドをブロックするのではなく、</span><span class="sxs-lookup"><span data-stu-id="1207b-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="1207b-122">非同期メソッドの残りの部分が待機中のタスクの継続として `Await` 式の後に登録されるようにします。</span><span class="sxs-lookup"><span data-stu-id="1207b-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="1207b-123">これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="1207b-124">タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="1207b-125">`Await` 式は、`Async` 修飾子で修飾されたすぐ外側のメソッドまたはラムダ式の本体でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1207b-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="1207b-126">用語*Await*そのコンテキストでのみがキーワードとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1207b-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="1207b-127">他の場所では、識別子として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="1207b-128">Async メソッドまたはラムダ式内で、`Await`クエリ式内で式は発生しません、`catch`または`finally`のブロック、[を再試行してください.キャッチしてください.最後に](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)ステートメントでは、ループ コントロール変数の式で、`For`または`For Each`、ループの本体で、または、 [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1207b-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="1207b-129">例外</span><span class="sxs-lookup"><span data-stu-id="1207b-129">Exceptions</span></span>  
 <span data-ttu-id="1207b-130">大半の非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="1207b-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1207b-131">返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1207b-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="1207b-132">`Await` 演算子は、これらのプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1207b-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="1207b-133">タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`Await` 演算子はその例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="1207b-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="1207b-134">タスクを返す非同期メソッドを待機しているときにそのメソッドがキャンセルされた場合、`Await` 演算子は <xref:System.OperationCanceledException> を再スローします。</span><span class="sxs-lookup"><span data-stu-id="1207b-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="1207b-135">障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。</span><span class="sxs-lookup"><span data-stu-id="1207b-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="1207b-136">たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> の呼び出しの結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="1207b-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1207b-137">このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。</span><span class="sxs-lookup"><span data-stu-id="1207b-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="1207b-138">ただし、どの例外が再スローされるかを予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="1207b-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="1207b-139">非同期メソッドのエラー処理の例については、次を参照してください[を再試行してください.。キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="1207b-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1207b-140">例</span><span class="sxs-lookup"><span data-stu-id="1207b-140">Example</span></span>  
 <span data-ttu-id="1207b-141">次に示す Windows フォームの例では、`Await` という非同期メソッドで `WaitAsynchronouslyAsync` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="1207b-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="1207b-142">このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。</span><span class="sxs-lookup"><span data-stu-id="1207b-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="1207b-143">`Await` には `WaitSynchronously` 演算子がないため、定義で `Async` 修飾子が使用されていて、本体で <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> が呼び出されているにもかかわらず、同期的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="1207b-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="1207b-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="1207b-144">See Also</span></span>  
 [<span data-ttu-id="1207b-145">Async および Await を使用した非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="1207b-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="1207b-146">チュートリアル: Async と Await を使用した Web へのアクセス</span><span class="sxs-lookup"><span data-stu-id="1207b-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="1207b-147">Async</span><span class="sxs-lookup"><span data-stu-id="1207b-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
