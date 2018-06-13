---
title: 非同期の戻り値の型 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 0c6c02efd282f8581f3dc85905149acf7b3ea6ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644083"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="797d4-102">非同期の戻り値の型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="797d4-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="797d4-103">非同期メソッドには、<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task>、および void の 3 とおりの戻り値の型があります。</span><span class="sxs-lookup"><span data-stu-id="797d4-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="797d4-104">Visual Basic では、void の戻り値の型は [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) プロシージャとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="797d4-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="797d4-105">非同期メソッドの詳細については、次を参照してください。 [Async および Await (Visual Basic) を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="797d4-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="797d4-106">それぞれの戻り値の型は、次のセクションの 1 つで確認でき、トピックの最後で 3 種類のすべてを使用する例を参照できます。</span><span class="sxs-lookup"><span data-stu-id="797d4-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="797d4-107">この例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="797d4-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_TaskTReturnType"></a><span data-ttu-id="797d4-108">Task(T) 型</span><span class="sxs-lookup"><span data-stu-id="797d4-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="797d4-109"><xref:System.Threading.Tasks.Task%601>戻り値の型を含む非同期メソッドは、使用、[返す](../../../../visual-basic/language-reference/statements/return-statement.md)ステートメントのオペランドが型を持つ`TResult`します。</span><span class="sxs-lookup"><span data-stu-id="797d4-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="797d4-110">次の例では、`TaskOfT_MethodAsync` 非同期メソッドには整数を返す return ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="797d4-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="797d4-111">そのため、メソッド宣言では、戻り値の型を `Task(Of Integer)` と指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="797d4-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 <span data-ttu-id="797d4-112">`TaskOfT_MethodAsync` が await 式の中から呼び出されると、await 式は `leisureHours` から返されるタスクに格納されている整数値 (`TaskOfT_MethodAsync` の値) を取得します。</span><span class="sxs-lookup"><span data-stu-id="797d4-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="797d4-113">詳細については、await 式を参照してください[Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="797d4-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="797d4-114">次のコードは、`TaskOfT_MethodAsync` メソッドを呼び出して待機します。</span><span class="sxs-lookup"><span data-stu-id="797d4-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="797d4-115">結果は `result1` 変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="797d4-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="797d4-116">次のコードに示すように、`TaskOfT_MethodAsync` の呼び出しと、`Await` の適用を分離すると、この仕組みをよく理解できます。</span><span class="sxs-lookup"><span data-stu-id="797d4-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="797d4-117">メソッドの宣言から予想されるように、直ちに待機しない `TaskOfT_MethodAsync` メソッドの呼び出しは、`Task(Of Integer)` を返します。</span><span class="sxs-lookup"><span data-stu-id="797d4-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="797d4-118">タスクは、この例の `integerTask` 変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="797d4-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="797d4-119">`integerTask` は <xref:System.Threading.Tasks.Task%601> であるため、<xref:System.Threading.Tasks.Task%601.Result> 型の `TResult` プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="797d4-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="797d4-120">この場合、TResult が整数型を表します。</span><span class="sxs-lookup"><span data-stu-id="797d4-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="797d4-121">`Await` が `integerTask` に適用されると、`integerTask` の <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティの内容が await 式の評価となります。</span><span class="sxs-lookup"><span data-stu-id="797d4-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="797d4-122">この値は `result2` 変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="797d4-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="797d4-123"><xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは Blocking プロパティです。</span><span class="sxs-lookup"><span data-stu-id="797d4-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="797d4-124">タスクが終了する前にアクセスしようとすると、現在アクティブなスレッドは、タスクが完了して値が使用可能になるまで、ブロックされます。</span><span class="sxs-lookup"><span data-stu-id="797d4-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="797d4-125">多くの場合、プロパティに直接アクセスする代わりに、`Await` を使用して値にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="797d4-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="797d4-126">次のコードの表示ステートメントは、`result1` 変数、`result2` 変数、および `Result` プロパティの値が同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="797d4-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="797d4-127">`Result` プロパティは Blocking プロパティであり、タスクが待機される前にアクセスしないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="797d4-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a><span data-ttu-id="797d4-128">Task 型</span><span class="sxs-lookup"><span data-stu-id="797d4-128">Task Return Type</span></span>  
 <span data-ttu-id="797d4-129">return ステートメントを含まない非同期メソッド、またはオペランドを返さない return ステートメントを含む非同期メソッドは、通常は <xref:System.Threading.Tasks.Task> 戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="797d4-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="797d4-130">このようなメソッドになります[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)プロシージャが作成されている場合に同期的に実行します。</span><span class="sxs-lookup"><span data-stu-id="797d4-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="797d4-131">非同期メソッドに戻り値の型 `Task` を使用した場合、呼び出し元のメソッドは `Await` 演算子を使って、呼び出された async のメソッドが終了するまで、呼び出し元の完了を中断します。</span><span class="sxs-lookup"><span data-stu-id="797d4-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="797d4-132">次の例では、非同期メソッド `Task_MethodAsync` には、return ステートメントが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="797d4-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="797d4-133">したがって、`Task` を待機させるメソッドに、戻り値の型 `Task_MethodAsync` を指定します。</span><span class="sxs-lookup"><span data-stu-id="797d4-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="797d4-134">`Task` 型の定義は、戻り値を格納する `Result` プロパティを含みません。</span><span class="sxs-lookup"><span data-stu-id="797d4-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 <span data-ttu-id="797d4-135">`Task_MethodAsync` は、同期 `Sub` または void を返すメソッドを呼び出す場合と同様に、await 式でなく、await ステートメントを使って呼び出され、待機されます。</span><span class="sxs-lookup"><span data-stu-id="797d4-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="797d4-136">アプリケーション、`Await`演算子はここで値を生成しません。</span><span class="sxs-lookup"><span data-stu-id="797d4-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="797d4-137">次のコードは、`Task_MethodAsync` メソッドを呼び出して待機します。</span><span class="sxs-lookup"><span data-stu-id="797d4-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="797d4-138">以前と同様に<xref:System.Threading.Tasks.Task%601>例への呼び出しを分離することができます`Task_MethodAsync`のアプリケーションから、`Await`演算子は、次のコードを示します。</span><span class="sxs-lookup"><span data-stu-id="797d4-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="797d4-139">ただし `Task` は `Result` プロパティを持たないこと、また await 演算子が `Task` に適用されるときに値は生成されないことに注意します。</span><span class="sxs-lookup"><span data-stu-id="797d4-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="797d4-140">次のコードは `Task_MethodAsync` の呼び出しを `Task_MethodAsync` が返すタスクの待機から分離します。</span><span class="sxs-lookup"><span data-stu-id="797d4-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="797d4-141">Void 型</span><span class="sxs-lookup"><span data-stu-id="797d4-141">Void Return Type</span></span>  
 <span data-ttu-id="797d4-142">主な用途`Sub`手順は、イベント ハンドラーの戻り値の型を (その他の言語に void 戻り値の型と呼ばれる) が存在しません。</span><span class="sxs-lookup"><span data-stu-id="797d4-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="797d4-143">void である戻り値は、void を返すメソッドを上書きするためにも使われます。または「ファイア アンド フォーゲット (撃ち放し)」と分類されるアクティビティを実行するメソッドに対して使われます。</span><span class="sxs-lookup"><span data-stu-id="797d4-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="797d4-144">ただし、void を返す非同期メソッドを待機することはできないため、できる限り `Task` を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="797d4-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="797d4-145">このようなメソッドの呼び出し元は、呼び出した非同期メソッドが完了するのを待たずに、完了まで継続できる必要があります。また呼び出し元は、非同期メソッドが生成する値または例外とは無関係である必要があります。</span><span class="sxs-lookup"><span data-stu-id="797d4-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="797d4-146">void を返す非同期メソッドの呼び出し元は、メソッドがスローする例外をキャッチすることはできません。そのようなハンドルされない例外によって、アプリケーションが失敗する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="797d4-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="797d4-147"><xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返す非同期メソッドで例外が発生すると、例外は返されたタスクに格納され、タスクが待機するときに再スローされます。</span><span class="sxs-lookup"><span data-stu-id="797d4-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="797d4-148">したがって、例外を生成する場合がある非同期メソッドは <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> の戻り値の型を持つこと、またメソッドの呼び出しが待機することを確認します。</span><span class="sxs-lookup"><span data-stu-id="797d4-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="797d4-149">非同期のメソッドで例外をキャッチする方法の詳細については、「[Try...Catch...Finally Statement (Try...Catch...Finally ステートメント)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="797d4-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="797d4-150">次のコードは非同期のイベント ハンドラーを定義します。</span><span class="sxs-lookup"><span data-stu-id="797d4-150">The following code defines an async event handler.</span></span>  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
##  <a name="BKMK_Example"></a><span data-ttu-id="797d4-151">コード例全体</span><span class="sxs-lookup"><span data-stu-id="797d4-151">Complete Example</span></span>  
 <span data-ttu-id="797d4-152">次の Windows Presentation Foundation (WPF) プロジェクトには、このトピックのコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="797d4-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="797d4-153">このプロジェクトを実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="797d4-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="797d4-154">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="797d4-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="797d4-155">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="797d4-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="797d4-156">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="797d4-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="797d4-157">**インストール**、**テンプレート**カテゴリで、選択**Visual Basic**を選択し**Windows**です。</span><span class="sxs-lookup"><span data-stu-id="797d4-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="797d4-158">プロジェクトの種類の一覧から **[WPF アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="797d4-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="797d4-159">プロジェクトの名前として「`AsyncReturnTypes`」と入力し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="797d4-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="797d4-160">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="797d4-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="797d4-161">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="797d4-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="797d4-162">タブが表示されない場合は、**ソリューション エクスプローラー**で MainWindow.xaml のショートカット メニューを開き、**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="797d4-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="797d4-163">MainWindow.xaml の **[XAML]** ウィンドウで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="797d4-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="797d4-164">テキスト ボックスとボタンを含むシンプルなウィンドウが、MainWindow.xaml の **[デザイン]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="797d4-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="797d4-165">**ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="797d4-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="797d4-166">MainWindow.xaml.vb のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="797d4-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. <span data-ttu-id="797d4-167">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="797d4-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="797d4-168">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="797d4-168">The following output should appear.</span></span>  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="797d4-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="797d4-169">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [<span data-ttu-id="797d4-170">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="797d4-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="797d4-171">非同期プログラムにおける制御フロー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="797d4-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [<span data-ttu-id="797d4-172">Async</span><span class="sxs-lookup"><span data-stu-id="797d4-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="797d4-173">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="797d4-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
