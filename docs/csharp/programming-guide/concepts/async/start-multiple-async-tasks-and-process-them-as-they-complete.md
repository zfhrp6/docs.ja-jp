---
title: 完了時での複数の非同期タスクとプロセスの実行 (C#)
ms.date: 07/20/2015
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 29dc629abae13bb7ba3a9b0cb87300e6d1cbe2d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="1a27a-102">完了時での複数の非同期タスクとプロセスの実行 (C#)</span><span class="sxs-lookup"><span data-stu-id="1a27a-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>
<span data-ttu-id="1a27a-103"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> を使用すると、複数のタスクを、開始された順番に処理するのでなく、同時に開始して完了するごとに 1 つずつ処理できます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="1a27a-104">クエリを使用して、タスクのコレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="1a27a-105">各タスクは、指定された Web サイトのコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1a27a-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="1a27a-106">while ループの各反復で、待機されている `WhenAny` への呼び出しは、最初にダウンロードを終了するタスクのコレクションにあるタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="1a27a-107">タスクはコレクションから削除され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="1a27a-108">ループは、コレクションのタスクがなくなるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a27a-109">この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a27a-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="1a27a-110">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="1a27a-110">Downloading the Example</span></span>  
 <span data-ttu-id="1a27a-111">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1a27a-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="1a27a-112">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1a27a-113">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1a27a-114">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="1a27a-115">**ソリューション エクスプローラー**で、**ProcessTasksAsTheyFinish** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1a27a-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="1a27a-116">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1a27a-117">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="1a27a-118">ダウンロードの長さが常に同じ順序では表示されないことを確認するために、プロジェクトを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="1a27a-119">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-119">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="1a27a-120">例のビルド</span><span class="sxs-lookup"><span data-stu-id="1a27a-120">Building the Example</span></span>  
 <span data-ttu-id="1a27a-121">この例では、「[完了後の残りの非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76)」で開発したコードを追加し、同じ UI を使用します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) and uses the same UI.</span></span>  
  
 <span data-ttu-id="1a27a-122">この例を自分でビルドするには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** では **CancelAfterOneTask** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="1a27a-123">そのプロジェクトの `AccessTheWebAsync` メソッドに、このトピックでの変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="1a27a-124">変更部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="1a27a-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="1a27a-125">**CancelAfterOneTask** プロジェクトには、実行時にタスクのコレクションを作成するクエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a27a-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="1a27a-126">次のコードの `ProcessURLAsync` への各呼び出しは、<xref:System.Threading.Tasks.Task%601> が整数である `TResult` を返します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 <span data-ttu-id="1a27a-127">プロジェクトの MainWindow.xaml.cs ファイルで、`AccessTheWebAsync` メソッドに次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="1a27a-127">In the MainWindow.xaml.cs file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="1a27a-128"><xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> の代わりに <xref:System.Linq.Enumerable.ToArray%2A> を適用して、クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   <span data-ttu-id="1a27a-129">コレクションの各タスクで次の手順を実行する while ループを追加します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="1a27a-130">`WhenAny` への呼び出しを待機し、ダウンロードを終了する、コレクションの最初のタスクを識別します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  <span data-ttu-id="1a27a-131">コレクションからそのタスクを削除します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-131">Removes that task from the collection.</span></span>  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  <span data-ttu-id="1a27a-132">`firstFinishedTask` への呼び出しから返される、`ProcessURLAsync` を待機します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="1a27a-133">`firstFinishedTask` 変数は <xref:System.Threading.Tasks.Task%601> が整数である `TReturn` です。</span><span class="sxs-lookup"><span data-stu-id="1a27a-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="1a27a-134">次の例に示すように、タスクは既に完了していますが、ダウンロードした Web サイトの長さの取得を待機します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 <span data-ttu-id="1a27a-135">ダウンロードの長さが常に同じ順序では表示されないことを確認するために、プロジェクトを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="1a27a-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1a27a-136">ループで `WhenAny` を使って、例に示すように、いくつかのタスクを格納する問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="1a27a-137">ただし、多数のタスクが処理する場合、他のアプローチがより効率的です。</span><span class="sxs-lookup"><span data-stu-id="1a27a-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="1a27a-138">詳細と例については、「[Processing Tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/)」 (完了したタスクを処理する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a27a-138">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="1a27a-139">コード例全体</span><span class="sxs-lookup"><span data-stu-id="1a27a-139">Complete Example</span></span>  
 <span data-ttu-id="1a27a-140">次のコードは、この例での MainWindow.xaml.cs ファイルのテキスト全体です。</span><span class="sxs-lookup"><span data-stu-id="1a27a-140">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="1a27a-141">アスタリスクはこの例のために追加された要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="1a27a-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="1a27a-142"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1a27a-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="1a27a-143">このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1a27a-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
namespace ProcessTasksAsTheyFinish  
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
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;  
        }  
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a27a-144">参照</span><span class="sxs-lookup"><span data-stu-id="1a27a-144">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="1a27a-145">非同期アプリケーションの微調整 (C#)</span><span class="sxs-lookup"><span data-stu-id="1a27a-145">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="1a27a-146">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="1a27a-146">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="1a27a-147">非同期のサンプル: アプリケーションの微調整</span><span class="sxs-lookup"><span data-stu-id="1a27a-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
