---
title: "Await 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
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
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="22c18-102">Await 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22c18-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="22c18-103">`Await` 演算子は、非同期のメソッドまたはラムダ式のオペランドに適用されて、待機中のタスクが完了するまでメソッドの実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="22c18-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="22c18-104">このタスクは、進行中の作業を表します。</span><span class="sxs-lookup"><span data-stu-id="22c18-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="22c18-105">メソッドに`Await`は使用が必要、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子です。</span><span class="sxs-lookup"><span data-stu-id="22c18-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="22c18-106">このような定義されたメソッドを使用して、`Async`修飾子、および通常含まれる&1; つまたは複数`Await`式と呼ばれます、 *async メソッド*します。</span><span class="sxs-lookup"><span data-stu-id="22c18-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22c18-107">`Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="22c18-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="22c18-108">非同期のプログラミングの概要については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="22c18-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="22c18-109">適用するタスクでは通常、`Await`演算子を実装するメソッドの呼び出しからの戻り値は、[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=204847)、つまり、 <xref:System.Threading.Tasks.Task>、または<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="22c18-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="22c18-110">次のコードで、<xref:System.Net.Http.HttpClient>メソッド<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>返します`getContentsTask`、 `Task(Of Byte())`</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient> 。</span><span class="sxs-lookup"><span data-stu-id="22c18-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="22c18-111">タスクにより、操作が完了したときに実際のバイト配列が生成されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="22c18-112">`Await` 演算子が `getContentsTask` に適用されているため、`SumPageSizesAsync` が完了するまで `getContentsTask` の実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="22c18-113">その間、コントロールは `SumPageSizesAsync` の呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="22c18-114">`getContentsTask` が終了すると、`Await` 式がバイト配列に評価されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
<span data-ttu-id="22c18-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="22c18-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="22c18-116">完全な例を参照してください。[チュートリアル: を使用して Async と Await による Web にアクセスする](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。</span><span class="sxs-lookup"><span data-stu-id="22c18-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="22c18-117">サンプルをダウンロードすることも[デベロッパー サンプル コード集](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)Microsoft web サイトです。</span><span class="sxs-lookup"><span data-stu-id="22c18-117">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="22c18-118">この例は AsyncWalkthrough_HttpClient プロジェクトにあります。</span><span class="sxs-lookup"><span data-stu-id="22c18-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="22c18-119">`Await` を返すメソッド呼び出しの結果に `Task(Of TResult)` が適用されている場合、`Await` 式の型は TResult になります。</span><span class="sxs-lookup"><span data-stu-id="22c18-119">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="22c18-120">`Await` を返すメソッド呼び出しの結果に `Task` が適用されている場合、`Await` 式は値を返しません。</span><span class="sxs-lookup"><span data-stu-id="22c18-120">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="22c18-121">この違いを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="22c18-121">The following example illustrates the difference.</span></span>  
  
<span data-ttu-id="22c18-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="22c18-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="22c18-123">`Await` 式またはステートメントは、自身が実行されているスレッドをブロックするのではなく、</span><span class="sxs-lookup"><span data-stu-id="22c18-123">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="22c18-124">非同期メソッドの残りの部分が待機中のタスクの継続として `Await` 式の後に登録されるようにします。</span><span class="sxs-lookup"><span data-stu-id="22c18-124">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="22c18-125">これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-125">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="22c18-126">タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-126">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="22c18-127">`Await` 式は、`Async` 修飾子で修飾されたすぐ外側のメソッドまたはラムダ式の本体でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="22c18-127">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="22c18-128">用語*Await*そのコンテキストでのみキーワードとして機能します。</span><span class="sxs-lookup"><span data-stu-id="22c18-128">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="22c18-129">他の場所では、識別子として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="22c18-129">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="22c18-130">非同期のメソッドまたはラムダ式に含まれる、`Await`式は、クエリ式で発生することはできません、`catch`または`finally`のブロック、[しようとしています.キャッチしてください.最後に](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)のループ コントロール変数式、ステートメント、`For`または`For Each`、ループの本体で、または、 [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md)ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="22c18-130">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="22c18-131">例外</span><span class="sxs-lookup"><span data-stu-id="22c18-131">Exceptions</span></span>  
 <span data-ttu-id="22c18-132">大半の非同期メソッドを返す、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="22c18-132">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="22c18-133">返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="22c18-133">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="22c18-134">`Await` 演算子は、これらのプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="22c18-134">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="22c18-135">タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`Await` 演算子はその例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="22c18-135">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="22c18-136">取り消されたタスクを返す非同期メソッドを待機する場合、`Await`演算子<xref:System.OperationCanceledException>.</xref:System.OperationCanceledException>を再スロー</span><span class="sxs-lookup"><span data-stu-id="22c18-136">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="22c18-137">障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。</span><span class="sxs-lookup"><span data-stu-id="22c18-137">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="22c18-138">タスクが<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>。</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>への呼び出しの結果になる可能性があります、</span><span class="sxs-lookup"><span data-stu-id="22c18-138">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="22c18-139">このようなタスクを待機すると、await 操作によって&1; つの例外のみが再スローされます。</span><span class="sxs-lookup"><span data-stu-id="22c18-139">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="22c18-140">ただし、どの例外が再スローされるかを予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="22c18-140">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="22c18-141">非同期のメソッドのエラー処理の例については、次を参照してください[しようとしています.。キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="22c18-141">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22c18-142">例</span><span class="sxs-lookup"><span data-stu-id="22c18-142">Example</span></span>  
 <span data-ttu-id="22c18-143">次に示す Windows フォームの例では、`Await` という非同期メソッドで `WaitAsynchronouslyAsync` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="22c18-143">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="22c18-144">このメソッドの動作と `WaitSynchronously` の動作の違いを確認します。</span><span class="sxs-lookup"><span data-stu-id="22c18-144">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="22c18-145">なし、`Await`演算子、 `WaitSynchronously` 、使用されているにもかかわらず、同期的に実行、`Async`修飾子を呼び出すと、その定義を<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>本体にです</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="22c18-145">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> in its body.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22c18-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="22c18-146">See Also</span></span>  
 <span data-ttu-id="22c18-147">[非同期プログラミングを Async と Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="22c18-147">[Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="22c18-148"> [チュートリアル: Async を使用して、Web にアクセスして Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="22c18-148"> [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="22c18-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span><span class="sxs-lookup"><span data-stu-id="22c18-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span></span>
