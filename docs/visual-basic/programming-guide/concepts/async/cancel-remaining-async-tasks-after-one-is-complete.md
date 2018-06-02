---
title: 完了 (Visual Basic の場合) は、1 つ後の残りの非同期タスクのキャンセルします。
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: baf18ed4c2a4693f0765358d9f9a56842991cf29
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728340"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="98321-102">完了 (Visual Basic の場合) は、1 つ後の残りの非同期タスクのキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="98321-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="98321-103"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> メソッドを <xref:System.Threading.CancellationToken> と共に使用すると、1 つのタスクが完了したときに残りのすべてのタスクを取り消しできます。</span><span class="sxs-lookup"><span data-stu-id="98321-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="98321-104">`WhenAny` メソッドは、タスクのコレクションである引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="98321-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="98321-105">このメソッドは、すべてのタスクを開始し、単一のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="98321-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="98321-106">単一のタスクは、コレクションのいずれかのタスクが完了すると完了します。</span><span class="sxs-lookup"><span data-stu-id="98321-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="98321-107">この例では、キャンセル トークンを `WhenAny` と共に使用して、タスクのコレクションから最初のタスクを終了まで保持し、残りのタスクを取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="98321-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="98321-108">各タスクは、Web サイトのコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="98321-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="98321-109">この例は最初のダウンロードが完了したコンテンツの長さを表示し、他のダウンロードを取り消します。</span><span class="sxs-lookup"><span data-stu-id="98321-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98321-110">この例を実行するには、コンピューターに Visual Studio 2012 以降および .NET Framework 4.5 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="98321-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="98321-111">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="98321-111">Downloading the Example</span></span>  
 <span data-ttu-id="98321-112">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="98321-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="98321-113">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="98321-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="98321-114">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="98321-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="98321-115">**プロジェクトを開く** ダイアログ ボックスでは、圧縮解除したサンプル コードが含まれるフォルダーを開き、AsyncFineTuningVB のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="98321-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="98321-116">**ソリューション エクスプローラー**で、**CancelAfterOneTask** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98321-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="98321-117">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="98321-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="98321-118">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="98321-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="98321-119">プログラムを複数回実行し、最初に終了するダウンロードが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="98321-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="98321-120">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.vb ファイルを確認できます。</span><span class="sxs-lookup"><span data-stu-id="98321-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="98321-121">例のビルド</span><span class="sxs-lookup"><span data-stu-id="98321-121">Building the Example</span></span>  
 <span data-ttu-id="98321-122">このトピックの例で開発したプロジェクトに追加[非同期タスクまたはタスクの一覧を取り消す](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0)タスクの一覧をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="98321-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="98321-123">この例では、**[キャンセル]** ボタンは明示的に使用していませんが、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="98321-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="98321-124">この例を自分で 1 つずつビルドするには、"例をダウンロードする" セクションの手順に従います。ただし、**[スタートアップ プロジェクト]** として **CancelAListOfTasks** を選択します。</span><span class="sxs-lookup"><span data-stu-id="98321-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="98321-125">そのプロジェクトに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="98321-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="98321-126">MainWindow.xaml.vb ファイル、 **CancelAListOfTasks**プロジェクトでのループから各 web サイトの処理手順を移動することによって、移行を開始`AccessTheWebAsync`次のメソッドを非同期にします。</span><span class="sxs-lookup"><span data-stu-id="98321-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```vb  
' ***Bundle the processing steps for a website into one async method.  
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
    ' GetAsync returns a Task(Of HttpResponseMessage).   
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
    ' Retrieve the website contents from the HttpResponseMessage.  
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
    Return urlContents.Length  
End Function  
```  
  
 <span data-ttu-id="98321-127">この例では、`AccessTheWebAsync` で、<xref:System.Linq.Enumerable.ToArray%2A> メソッドのクエリと `WhenAny` メソッドを使用して、タスクの配列を作成して開始します。</span><span class="sxs-lookup"><span data-stu-id="98321-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="98321-128">配列への `WhenAny` のアプリケーションは、待機したときに、タスクの配列で完了に到達する最初のタスクを評価する 1 つのタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="98321-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="98321-129">`AccessTheWebAsync` で次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="98321-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="98321-130">アスタリスクはコード ファイルの変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="98321-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="98321-131">ループをコメント アウトするか、削除します。</span><span class="sxs-lookup"><span data-stu-id="98321-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="98321-132">実行されると、一般的なタスクのコレクションを生成するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="98321-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="98321-133">`ProcessURLAsync` に対する各呼び出しは、<xref:System.Threading.Tasks.Task%601> が整数である `TResult` を返します。</span><span class="sxs-lookup"><span data-stu-id="98321-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  <span data-ttu-id="98321-134">`ToArray` を呼び出してクエリを実行し、タスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="98321-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="98321-135">次の手順で `WhenAny` メソッドのアプリケーションは、`ToArray` を使用せずにクエリを実行してタスクを開始しますが、他のメソッドはそうでない場合があります。</span><span class="sxs-lookup"><span data-stu-id="98321-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="98321-136">最も安全な方法は、クエリの実行を明示的に強制することです。</span><span class="sxs-lookup"><span data-stu-id="98321-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="98321-137">タスクのコレクションで `WhenAny` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="98321-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="98321-138">`WhenAny` は `Task(Of Task(Of Integer))` または `Task<Task<int>>` を返します。</span><span class="sxs-lookup"><span data-stu-id="98321-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="98321-139">つまり、`WhenAny` は、待機すると、単一の `Task(Of Integer)` または `Task<int>` に評価するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="98321-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="98321-140">その単一のタスクが、コレクションで最初に終了するタスクです。</span><span class="sxs-lookup"><span data-stu-id="98321-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="98321-141">最初に終了したタスクは `firstFinishedTask` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="98321-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="98321-142">`firstFinishedTask` の型は、<xref:System.Threading.Tasks.Task%601> が整数である `TResult` です。それは `ProcessURLAsync` の戻り値の型であるためです。</span><span class="sxs-lookup"><span data-stu-id="98321-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="98321-143">この例では、最初に終了したタスクにのみ焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="98321-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="98321-144">したがって、<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> を使用して、残りのタスクを取り消します。</span><span class="sxs-lookup"><span data-stu-id="98321-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="98321-145">最後に、`firstFinishedTask` を待機して、ダウンロードされたコンテンツの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="98321-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="98321-146">プログラムを複数回実行し、最初に終了するダウンロードが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="98321-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="98321-147">コード例全体</span><span class="sxs-lookup"><span data-stu-id="98321-147">Complete Example</span></span>  
 <span data-ttu-id="98321-148">次のコードは、この例での MainWindow.xaml.vb または MainWindow.xaml.cs ファイルの全体です。</span><span class="sxs-lookup"><span data-stu-id="98321-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="98321-149">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="98321-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="98321-150"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="98321-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="98321-151">このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="98321-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Download complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        '' Comment out or delete the loop.  
        ''For Each url In urlList  
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).   
        ''    ' Argument ct carries the message if the Cancel button is chosen.   
        ''    ' Note that the Cancel button can cancel all remaining downloads.  
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ''    ' Retrieve the website contents from the HttpResponseMessage.  
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ''    resultsTextBox.Text &=  
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        ''Next  
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToArray to execute the query and start the download tasks.   
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' ***Call WhenAny and then await the result. The task that finishes   
        ' first is assigned to firstFinishedTask.  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
        ' ***Cancel the rest of the downloads. You just want the first one.  
        cts.Cancel()  
  
        ' ***Await the first completed task and display the results  
        ' Run the program several times to demonstrate that different  
        ' websites can finish first.  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    End Function  
  
    ' ***Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="98321-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="98321-152">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="98321-153">非同期アプリケーションの微調整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98321-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="98321-154">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98321-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="98321-155">非同期のサンプル: アプリケーションの微調整</span><span class="sxs-lookup"><span data-stu-id="98321-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
