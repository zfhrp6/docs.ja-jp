---
title: Async (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e11bb7eb29cefa627543e8ad0a9b061d5ad1e95c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="async-visual-basic"></a><span data-ttu-id="89415-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89415-102">Async (Visual Basic)</span></span>
<span data-ttu-id="89415-103">`Async`修飾子には、ことを示します、メソッドまたは[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)を変更することは非同期です。</span><span class="sxs-lookup"><span data-stu-id="89415-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="89415-104">このようなメソッドをいいます*非同期メソッド*です。</span><span class="sxs-lookup"><span data-stu-id="89415-104">Such methods are referred to as *async methods*.</span></span>  
  
 <span data-ttu-id="89415-105">非同期メソッドは、呼び出し元のスレッドをブロックすることなく、実行に時間のかかる可能性のある処理を行うことができる、便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="89415-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="89415-106">非同期メソッドの呼び出し元は、非同期メソッドの完了を待たずに作業を再開できます。</span><span class="sxs-lookup"><span data-stu-id="89415-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89415-107">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="89415-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="89415-108">非同期のプログラミングの概要については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="89415-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="89415-109">次の例は、非同期メソッドの構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="89415-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="89415-110">規則により、非同期メソッドの名前の末尾は "Async" になります。</span><span class="sxs-lookup"><span data-stu-id="89415-110">By convention, async method names end in "Async."</span></span>  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 <span data-ttu-id="89415-111">通常で修飾されているメソッド、`Async`キーワードは、少なくとも 1 つを含む[Await](../../../visual-basic/language-reference/modifiers/async.md)式またはステートメント。</span><span class="sxs-lookup"><span data-stu-id="89415-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="89415-112">メソッドは、最初の `Await` に到達するまで同期的に実行されますが、この時点で、待機していたタスクが完了するまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="89415-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="89415-113">その間、コントロールはメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="89415-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="89415-114">メソッドに `Await` 式またはステートメントが含まれていない場合、メソッドは中断されず、同期メソッドのように実行されます。</span><span class="sxs-lookup"><span data-stu-id="89415-114">If the method doesn’t contain an `Await` expression or statement, the method isn’t suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="89415-115">`Await` が含まれていない非同期メソッドが存在する場合は、その状態がエラーを示す可能性があるため、コンパイラによって警告が通知されます。</span><span class="sxs-lookup"><span data-stu-id="89415-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="89415-116">詳細については、次を参照してください。、[コンパイラ エラー](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md)です。</span><span class="sxs-lookup"><span data-stu-id="89415-116">For more information, see the [compiler error](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).</span></span>  
  
 <span data-ttu-id="89415-117">`Async` キーワードは、予約されていないキーワードです。</span><span class="sxs-lookup"><span data-stu-id="89415-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="89415-118">メソッドまたはラムダ式を修飾する場合にキーワードとなります。</span><span class="sxs-lookup"><span data-stu-id="89415-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="89415-119">それ以外の場合は、識別子として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="89415-119">In all other contexts, it is interpreted as an identifier.</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="89415-120">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="89415-120">Return Types</span></span>  
 <span data-ttu-id="89415-121">非同期のメソッドは、 [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)プロシージャ、または[関数](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)を戻り値の型を持つプロシージャ<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>です。</span><span class="sxs-lookup"><span data-stu-id="89415-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="89415-122">メソッドは、いずれかを宣言できません[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーター。</span><span class="sxs-lookup"><span data-stu-id="89415-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="89415-123">指定した`Task(Of TResult)`非同期メソッドの戻り値の型の場合、[返す](../../../visual-basic/language-reference/statements/return-statement.md)メソッドのステートメントに TResult 型のオペランド。</span><span class="sxs-lookup"><span data-stu-id="89415-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="89415-124">メソッドの完了時に意味のある値を返さない場合は、`Task` を使用します。</span><span class="sxs-lookup"><span data-stu-id="89415-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="89415-125">これにより、メソッドの呼び出しでは `Task` が返されますが、`Task` の完了時に、`Await` を待機している `Task` ステートメントは結果値を生成しません。</span><span class="sxs-lookup"><span data-stu-id="89415-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>  
  
 <span data-ttu-id="89415-126">非同期サブルーチンは主として、`Sub` プロシージャが必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="89415-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="89415-127">非同期サブルーチンの呼び出し元は、このサブルーチンを待機できず、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="89415-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="89415-128">使用例を含む詳細については、「[非同期の戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89415-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89415-129">例</span><span class="sxs-lookup"><span data-stu-id="89415-129">Example</span></span>  
 <span data-ttu-id="89415-130">次の例は、非同期のイベント ハンドラー、非同期ラムダ式、および非同期メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="89415-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="89415-131">これらの要素を使用する完全な例を参照してください。[チュートリアル: を使用して Async および Await を Web にアクセスする](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。</span><span class="sxs-lookup"><span data-stu-id="89415-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="89415-132">チュートリアル コードは、[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkId=255191)のページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="89415-132">You can download the walkthrough code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="89415-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="89415-133">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="89415-134">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="89415-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="89415-135">Async および Await を使用した非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="89415-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="89415-136">チュートリアル: Async と Await を使用した Web へのアクセス</span><span class="sxs-lookup"><span data-stu-id="89415-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
