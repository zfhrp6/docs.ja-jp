---
title: "複数の同期タスクし、プロセスの完了 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fbf4611ecd64abfd016963dff887d82aad333b7
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="53951-102">複数の同期タスクし、プロセスの完了 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53951-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="53951-103">使用して<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>、同時に複数のタスクを開始し、起動している順序で処理するのではなく、完了すると、1 つずつを処理することができます</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="53951-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="53951-104">クエリを使用して、タスクのコレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="53951-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="53951-105">各タスクは、指定された Web サイトのコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="53951-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="53951-106">while ループの各反復で、待機されている `WhenAny` への呼び出しは、最初にダウンロードを終了するタスクのコレクションにあるタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="53951-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="53951-107">タスクはコレクションから削除され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="53951-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="53951-108">ループは、コレクションのタスクがなくなるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="53951-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53951-109">例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="53951-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="53951-110">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="53951-110">Downloading the Example</span></span>  
 <span data-ttu-id="53951-111">完全な Windows Presentation Foundation (WPF) プロジェクトをダウンロードすることができます[Async サンプル: 細かいアプリケーションの調整](http://go.microsoft.com/fwlink/?LinkId=255046)し次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="53951-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="53951-112">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="53951-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="53951-113">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="53951-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="53951-114">**プロジェクトを開く** ダイアログ ボックスでは、圧縮解除したサンプル コードが含まれるフォルダーを開き、AsyncFineTuningVB のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="53951-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="53951-115">**ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **ProcessTasksAsTheyFinish**プロジェクトを開いて、**スタートアップ プロジェクトとして設定**します。</span><span class="sxs-lookup"><span data-stu-id="53951-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="53951-116">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="53951-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="53951-117">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="53951-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="53951-118">ダウンロードの長さが常に同じ順序では表示されないことを確認するために、プロジェクトを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="53951-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="53951-119">プロジェクトをダウンロードできない場合は、このトピックの最後の MainWindow.xaml.vb ファイルを確認できます。</span><span class="sxs-lookup"><span data-stu-id="53951-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="53951-120">例のビルド</span><span class="sxs-lookup"><span data-stu-id="53951-120">Building the Example</span></span>  
 <span data-ttu-id="53951-121">この例で開発されたコードを追加[1 つの完了 (Visual Basic) の後に残りの非同期タスクのキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)し、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="53951-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="53951-122">例をビルドする、自分のステップ バイ ステップ「例をダウンロードする」セクション指示従いますが、選択**CancelAfterOneTask**として、**スタートアップ プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="53951-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="53951-123">そのプロジェクトの `AccessTheWebAsync` メソッドに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="53951-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="53951-124">変更部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="53951-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="53951-125">**CancelAfterOneTask**プロジェクトに既にクエリが含まれている、実行すると、タスクのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="53951-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="53951-126">各呼び出し`ProcessURLAsync`次のコードを返します、 <xref:System.Threading.Tasks.Task%601>、`TResult`整数です。</xref:System.Threading.Tasks.Task%601> 。</span><span class="sxs-lookup"><span data-stu-id="53951-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="53951-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="53951-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="53951-128">プロジェクトの MainWindow.xaml.vb ファイルで次の変更を`AccessTheWebAsync`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="53951-128">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="53951-129"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> <xref:System.Linq.Enumerable.ToArray%2A>。</xref:System.Linq.Enumerable.ToArray%2A>の代わりに</xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>適用することで、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="53951-129">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
<span data-ttu-id="53951-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="53951-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
-   <span data-ttu-id="53951-131">コレクションの各タスクで次の手順を実行する while ループを追加します。</span><span class="sxs-lookup"><span data-stu-id="53951-131">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="53951-132">`WhenAny` への呼び出しを待機し、ダウンロードを終了する、コレクションの最初のタスクを識別します。</span><span class="sxs-lookup"><span data-stu-id="53951-132">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
<span data-ttu-id="53951-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="53951-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
    2.  <span data-ttu-id="53951-134">コレクションからそのタスクを削除します。</span><span class="sxs-lookup"><span data-stu-id="53951-134">Removes that task from the collection.</span></span>  
  
<span data-ttu-id="53951-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="53951-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
    3.  <span data-ttu-id="53951-136">`firstFinishedTask` への呼び出しから返される、`ProcessURLAsync` を待機します。</span><span class="sxs-lookup"><span data-stu-id="53951-136">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="53951-137">`firstFinishedTask`変数は、 <xref:System.Threading.Tasks.Task%601>、`TReturn`整数です</xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="53951-137">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="53951-138">次の例に示すように、タスクは既に完了していますが、ダウンロードした Web サイトの長さの取得を待機します。</span><span class="sxs-lookup"><span data-stu-id="53951-138">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="53951-139">ダウンロードの長さが常に同じ順序では表示されないことを確認するために、プロジェクトを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="53951-139">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="53951-140">ループで `WhenAny` を使って、例に示すように、いくつかのタスクを格納する問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="53951-140">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="53951-141">ただし、多数のタスクが処理する場合、他のアプローチがより効率的です。</span><span class="sxs-lookup"><span data-stu-id="53951-141">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="53951-142">詳細と例については、次を参照してください。[としてそれらの完全な処理タスク](http://go.microsoft.com/fwlink/?LinkId=260810)します。</span><span class="sxs-lookup"><span data-stu-id="53951-142">For more information and examples, see [Processing Tasks as they complete](http://go.microsoft.com/fwlink/?LinkId=260810).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="53951-143">コード例全体</span><span class="sxs-lookup"><span data-stu-id="53951-143">Complete Example</span></span>  
 <span data-ttu-id="53951-144">次のコードは、たとえば、MainWindow.xaml.vb ファイルの完全なテキストです。</span><span class="sxs-lookup"><span data-stu-id="53951-144">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="53951-145">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="53951-145">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="53951-146"><xref:System.Net.Http>。</xref:System.Net.Http>への参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="53951-146">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="53951-147">プロジェクトをダウンロードする[Async サンプル: 細かいアプリケーションの調整](http://go.microsoft.com/fwlink/?LinkId=255046)します。</span><span class="sxs-lookup"><span data-stu-id="53951-147">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.   
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="53951-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="53951-148">See Also</span></span>  
 <span data-ttu-id="53951-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="53951-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="53951-150"> [非同期アプリケーション (Visual Basic) の微調整](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="53951-150"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="53951-151"> [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="53951-151"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="53951-152"> [アプリケーションの微調整の非同期のサンプル:](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="53951-152"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
