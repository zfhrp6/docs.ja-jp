---
title: 完了後の残りの非同期タスクのキャンセル (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 22a29dec90dcbbd24ff1a6081fd7bf1d56d6ac0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327425"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="13a5b-102">完了後の残りの非同期タスクのキャンセル (C#)</span><span class="sxs-lookup"><span data-stu-id="13a5b-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="13a5b-103"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> メソッドを <xref:System.Threading.CancellationToken> と共に使用すると、1 つのタスクが完了したときに残りのすべてのタスクを取り消しできます。</span><span class="sxs-lookup"><span data-stu-id="13a5b-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="13a5b-104">`WhenAny` メソッドは、タスクのコレクションである引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="13a5b-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="13a5b-105">このメソッドは、すべてのタスクを開始し、単一のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="13a5b-106">単一のタスクは、コレクションのいずれかのタスクが完了すると完了します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="13a5b-107">この例では、キャンセル トークンを `WhenAny` と共に使用して、タスクのコレクションから最初のタスクを終了まで保持し、残りのタスクを取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="13a5b-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="13a5b-108">各タスクは、Web サイトのコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="13a5b-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="13a5b-109">この例は最初のダウンロードが完了したコンテンツの長さを表示し、他のダウンロードを取り消します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13a5b-110">この例を実行するには、コンピューターに Visual Studio 2012 以降および .NET Framework 4.5 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="13a5b-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="13a5b-111">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="13a5b-111">Downloading the Example</span></span>  
 <span data-ttu-id="13a5b-112">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="13a5b-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="13a5b-113">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="13a5b-114">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="13a5b-115">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="13a5b-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="13a5b-116">**ソリューション エクスプローラー**で、**CancelAfterOneTask** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="13a5b-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="13a5b-117">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="13a5b-118">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="13a5b-119">プログラムを複数回実行し、最初に終了するダウンロードが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="13a5b-120">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="13a5b-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="13a5b-121">例のビルド</span><span class="sxs-lookup"><span data-stu-id="13a5b-121">Building the Example</span></span>  
 <span data-ttu-id="13a5b-122">このトピックの例では、「[非同期タスクまたはタスクの一覧のキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)」で開発したプロジェクトに追加して、タスクのリストをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="13a5b-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="13a5b-123">この例では、**[キャンセル]** ボタンは明示的に使用していませんが、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="13a5b-124">この例を自分で 1 つずつビルドするには、"例をダウンロードする" セクションの手順に従います。ただし、**[スタートアップ プロジェクト]** として **CancelAListOfTasks** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="13a5b-125">そのプロジェクトに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="13a5b-126">**CancelAListOfTasks** プロジェクトの MainWindow.xaml.cs ファイルで、各 Web サイトの処理ステップを `AccessTheWebAsync` のループから次の非同期メソッドに移動して、遷移を開始します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
/ ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="13a5b-127">この例では、`AccessTheWebAsync` で、<xref:System.Linq.Enumerable.ToArray%2A> メソッドのクエリと `WhenAny` メソッドを使用して、タスクの配列を作成して開始します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="13a5b-128">配列への `WhenAny` のアプリケーションは、待機したときに、タスクの配列で完了に到達する最初のタスクを評価する 1 つのタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="13a5b-129">`AccessTheWebAsync` で次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="13a5b-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="13a5b-130">アスタリスクはコード ファイルの変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="13a5b-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="13a5b-131">ループをコメント アウトするか、削除します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="13a5b-132">実行されると、一般的なタスクのコレクションを生成するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="13a5b-133">`ProcessURLAsync` に対する各呼び出しは、<xref:System.Threading.Tasks.Task%601> が整数である `TResult` を返します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  <span data-ttu-id="13a5b-134">`ToArray` を呼び出してクエリを実行し、タスクを開始します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="13a5b-135">次の手順で `WhenAny` メソッドのアプリケーションは、`ToArray` を使用せずにクエリを実行してタスクを開始しますが、他のメソッドはそうでない場合があります。</span><span class="sxs-lookup"><span data-stu-id="13a5b-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="13a5b-136">最も安全な方法は、クエリの実行を明示的に強制することです。</span><span class="sxs-lookup"><span data-stu-id="13a5b-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="13a5b-137">タスクのコレクションで `WhenAny` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="13a5b-138">`WhenAny` は `Task(Of Task(Of Integer))` または `Task<Task<int>>` を返します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="13a5b-139">つまり、`WhenAny` は、待機すると、単一の `Task(Of Integer)` または `Task<int>` に評価するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="13a5b-140">その単一のタスクが、コレクションで最初に終了するタスクです。</span><span class="sxs-lookup"><span data-stu-id="13a5b-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="13a5b-141">最初に終了したタスクは `firstFinishedTask` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="13a5b-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="13a5b-142">`firstFinishedTask` の型は、<xref:System.Threading.Tasks.Task%601> が整数である `TResult` です。それは `ProcessURLAsync` の戻り値の型であるためです。</span><span class="sxs-lookup"><span data-stu-id="13a5b-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  <span data-ttu-id="13a5b-143">この例では、最初に終了したタスクにのみ焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="13a5b-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="13a5b-144">したがって、<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> を使用して、残りのタスクを取り消します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  <span data-ttu-id="13a5b-145">最後に、`firstFinishedTask` を待機して、ダウンロードされたコンテンツの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
    ```  
  
 <span data-ttu-id="13a5b-146">プログラムを複数回実行し、最初に終了するダウンロードが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="13a5b-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="13a5b-147">コード例全体</span><span class="sxs-lookup"><span data-stu-id="13a5b-147">Complete Example</span></span>  
 <span data-ttu-id="13a5b-148">次のコードは、この例で使用した MainWindow.xaml.cs ファイルの全体です。</span><span class="sxs-lookup"><span data-stu-id="13a5b-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="13a5b-149">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="13a5b-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="13a5b-150"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13a5b-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="13a5b-151">このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="13a5b-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.   
            //    // Argument ct carries the message if the Cancel button is chosen.   
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.   
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes   
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.   
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="13a5b-152">参照</span><span class="sxs-lookup"><span data-stu-id="13a5b-152">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="13a5b-153">非同期アプリケーションの微調整 (C#)</span><span class="sxs-lookup"><span data-stu-id="13a5b-153">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="13a5b-154">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="13a5b-154">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="13a5b-155">非同期のサンプル: アプリケーションの微調整</span><span class="sxs-lookup"><span data-stu-id="13a5b-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
