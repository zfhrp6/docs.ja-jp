---
title: "await (C# リファレンス)"
ms.date: 2017-05-22
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- await_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 38b41e2cde3c0c22c1c5bd609f1ab8fcd2685355
ms.openlocfilehash: 7255d170c8b27ba29817b6355c0cf6a9c593a09f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/01/2017

---
# <a name="await-c-reference"></a><span data-ttu-id="8f69f-102">await (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8f69f-102">await (C# Reference)</span></span>
<span data-ttu-id="8f69f-103">`await` 演算子は非同期メソッドのタスクに適用され、中断ポイントを挿入することで、メソッドの実行を、待機中のタスクが完了するまで中断します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-103">The `await` operator is applied to a task in an asynchronous method to insert a suspension point in the execution of the method until the awaited task completes.</span></span> <span data-ttu-id="8f69f-104">このタスクは、進行中の作業を表します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-104">The task represents ongoing work.</span></span>  
  
<span data-ttu-id="8f69f-105">`await` は、[async](../../../csharp/language-reference/keywords/async.md) キーワードによって変更された非同期メソッドでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-105">`await` can only be used in an asynchronous method modified by the [async](../../../csharp/language-reference/keywords/async.md) keyword.</span></span> <span data-ttu-id="8f69f-106">このようなメソッド (`async` 修飾子を使用して定義され、通常 1 つ以上の `await` 式を含むメソッド) が、"*非同期メソッド*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-106">Such a method, defined by using the `async` modifier and usually containing one or more `await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f69f-107">`async` キーワードおよび `await` キーワードは、C# 5 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="8f69f-107">The `async` and `await` keywords were introduced in C# 5.</span></span> <span data-ttu-id="8f69f-108">非同期プログラミングの概要については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8f69f-108">For an introduction to async programming, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
<span data-ttu-id="8f69f-109">`await` 演算子を適用するタスクは、通常、[タスク ベースの非同期パターン](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)を実装するメソッド呼び出しによって返されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-109">The task to which the `await` operator is applied typically is returned by a call to a method that implements the [Task-Based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span> <span data-ttu-id="8f69f-110">たとえば、<xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、および `System.Threading.Tasks.ValueType<TResult>` オブジェクトを返すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="8f69f-110">They include methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, and `System.Threading.Tasks.ValueType<TResult>` objects.</span></span>  

  
 <span data-ttu-id="8f69f-111">次の例では、<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=fullName> メソッドは `Task<byte[]>` を返します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-111">In the following example, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=fullName> method returns a `Task<byte[]>`.</span></span> <span data-ttu-id="8f69f-112">これにより、タスクが完了したときに実際のバイト配列が生成されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-112">The task is a promise to produce the actual byte array when the task is complete.</span></span> <span data-ttu-id="8f69f-113">`await` 演算子は、<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> メソッドの処理が完了するまで実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-113">The `await` operator suspends execution until the work of the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> method is complete.</span></span> <span data-ttu-id="8f69f-114">その間、コントロールは `GetPageSizeAsync` の呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-114">In the meantime, control is returned to the caller of `GetPageSizeAsync`.</span></span> <span data-ttu-id="8f69f-115">タスクの実行が終了すると、`await` 式はバイト配列に評価されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-115">When the task finishes execution, the `await` expression evaluates to a byte array.</span></span>  

<span data-ttu-id="8f69f-116">[!code-cs[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f69f-116">[!code-cs[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="8f69f-117">完全な例については、「[チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8f69f-117">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="8f69f-118">Microsoft Web サイトの[開発者コード サンプル](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409)からサンプルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-118">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="8f69f-119">この例は AsyncWalkthrough_HttpClient プロジェクトにあります。</span><span class="sxs-lookup"><span data-stu-id="8f69f-119">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
<span data-ttu-id="8f69f-120">前の例で示したように、`Task<TResult>` を返すメソッド呼び出しの結果に `await` を適用する場合、`await` 式の型は `TResult` です。</span><span class="sxs-lookup"><span data-stu-id="8f69f-120">As shown in the previous example, if `await` is applied to the result of a method call that returns a `Task<TResult>`, then the type of the `await` expression is `TResult`.</span></span> <span data-ttu-id="8f69f-121">`Task` を返すメソッド呼び出しの結果に `await` が適用されている場合、`await` 式の型は `void` になります。</span><span class="sxs-lookup"><span data-stu-id="8f69f-121">If `await` is applied to the result of a method call that returns a `Task`, then the type of the `await` expression is `void`.</span></span> <span data-ttu-id="8f69f-122">この違いを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-122">The following example illustrates the difference.</span></span>  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
<span data-ttu-id="8f69f-123">`await` 式は、自身が実行されているスレッドをブロックするのではなく、</span><span class="sxs-lookup"><span data-stu-id="8f69f-123">An `await` expression does not block the thread on which it is executing.</span></span> <span data-ttu-id="8f69f-124">非同期メソッドの残りの部分が待機中のタスクの継続として登録されるようにします。</span><span class="sxs-lookup"><span data-stu-id="8f69f-124">Instead, it causes the compiler to sign up the rest of the async method as a continuation on the awaited task.</span></span> <span data-ttu-id="8f69f-125">これによって、コントロールは非同期のメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-125">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="8f69f-126">タスクが完了すると、継続が呼び出され、中断したところから非同期メソッドの実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-126">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
<span data-ttu-id="8f69f-127">`await` 式は、`async` 修飾子でマークする必要がある外側のメソッド、ラムダ式、または匿名メソッドの本体でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-127">An `await` expression can occur only in the body of its enclosing method, lambda expression, or anonymous method, which must be marked with an `async` modifier.</span></span> <span data-ttu-id="8f69f-128">*await* という用語がキーワードとして機能するのはこのコンテキストだけです。</span><span class="sxs-lookup"><span data-stu-id="8f69f-128">The term *await* serves as a keyword only in that context.</span></span> <span data-ttu-id="8f69f-129">他の場所では、識別子として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-129">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="8f69f-130">メソッド、ラムダ式、または匿名メソッド内では、`await` 式は、同期関数、クエリ式、[lock ステートメント](../../../csharp/language-reference/keywords/lock-statement.md)のブロック、または [unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストの本体では使用できません。</span><span class="sxs-lookup"><span data-stu-id="8f69f-130">Within the method, lambda expression, or anonymous method, an `await` expression cannot occur in the body of a synchronous function, in a query expression, in the block of a [lock statement](../../../csharp/language-reference/keywords/lock-statement.md), or in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="8f69f-131">例外</span><span class="sxs-lookup"><span data-stu-id="8f69f-131">Exceptions</span></span>  
<span data-ttu-id="8f69f-132">大半の非同期メソッドは、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-132">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="8f69f-133">返されるタスクのプロパティには、タスクが完了しているかどうか、非同期メソッドで例外または取り消しが発生したかどうか、最終結果など、その状態および履歴に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-133">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="8f69f-134">`await` 演算子は、`GetAwaiter` メソッドによって返されたオブジェクトでメソッドを呼び出して、こうしたプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8f69f-134">The `await` operator accesses those properties by calling methods on the object returned by the `GetAwaiter` method.</span></span>  
  
<span data-ttu-id="8f69f-135">タスクを返す非同期メソッドを待機しているときにそのメソッドで例外が発生した場合、`await` 演算子はその例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="8f69f-135">If you await a task-returning async method that causes an exception, the `await` operator rethrows the exception.</span></span>  
  
<span data-ttu-id="8f69f-136">タスクを返す非同期メソッドを待機しているときにそのメソッドが取り消された場合、`await` 演算子は <xref:System.OperationCanceledException> を再スローします。</span><span class="sxs-lookup"><span data-stu-id="8f69f-136">If you await a task-returning async method that's canceled, the `await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
<span data-ttu-id="8f69f-137">障害の発生した状態にある単一のタスクで、複数の例外が反映される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8f69f-137">A single task that is in a faulted state can reflect multiple exceptions.</span></span> <span data-ttu-id="8f69f-138">たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> の呼び出しの結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8f69f-138">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="8f69f-139">このようなタスクを待機すると、await 操作によって 1 つの例外のみが再スローされます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-139">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="8f69f-140">ただし、どの例外が再スローされるかを予測することはできません。</span><span class="sxs-lookup"><span data-stu-id="8f69f-140">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
<span data-ttu-id="8f69f-141">非同期メソッドのエラー処理の例については、「[try-catch](../../../csharp/language-reference/keywords/try-catch.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8f69f-141">For examples of error handling in async methods, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f69f-142">例</span><span class="sxs-lookup"><span data-stu-id="8f69f-142">Example</span></span>  
<span data-ttu-id="8f69f-143">次の例では、URL がコマンド ラインの引数として渡されたページの合計文字数を返します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-143">The following example returns the total number of characters in the pages whose URLs are passed to it as command line arguments.</span></span> <span data-ttu-id="8f69f-144">この例は、`async` キーワードでマークされた `GetPageLengthsAsync` メソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="8f69f-144">The example calls the `GetPageLengthsAsync` method, which is marked with the `async` keyword.</span></span> <span data-ttu-id="8f69f-145">その後、`GetPageLengthsAsync` メソッドは `await` キーワードを使用して、<xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=fullName> メソッドへの呼び出しを待ちます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-145">The `GetPageLengthsAsync` method in turn uses the `await` keyword to await calls to the <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=fullName> method.</span></span>  

<span data-ttu-id="8f69f-146">[!code-cs[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8f69f-146">[!code-cs[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]</span></span>  

<span data-ttu-id="8f69f-147">アプリケーション エントリ ポイントでの `async` および `await` の使用はサポートされていないため、`async` 属性は `Main` メソッドに適用できません。また、`GetPageLengthsAsync` メソッド呼び出しを待つこともできません。</span><span class="sxs-lookup"><span data-stu-id="8f69f-147">Because the use of `async` and `await` in an application entry point is not supported, we cannot apply the `async` attribute to the `Main` method, nor can we await the `GetPageLengthsAsync` method call.</span></span> <span data-ttu-id="8f69f-148">非同期操作が完了するのを `Main` メソッドが確実に待つようにするには、<xref:System.Threading.Tasks.Task%601.Result?displayProperty=fullName> プロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f69f-148">We can ensure that the `Main` method waits for the async operation to complete by retrieving the value of the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=fullName> property.</span></span> <span data-ttu-id="8f69f-149">値を返さないタスクについては、<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8f69f-149">For tasks that do not return a value, you can call the <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=fullName> method.</span></span> 

## <a name="see-also"></a><span data-ttu-id="8f69f-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f69f-150">See also</span></span>  
<span data-ttu-id="8f69f-151">[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="8f69f-151">[Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="8f69f-152">[チュートリアル: Async と Await を使用した Web へのアクセス](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="8f69f-152">[Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
[<span data-ttu-id="8f69f-153">async</span><span class="sxs-lookup"><span data-stu-id="8f69f-153">async</span></span>](../../../csharp/language-reference/keywords/async.md)

