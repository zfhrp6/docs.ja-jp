---
title: '方法: Task.WhenAll (Visual Basic) を使用して Asyncwalkthrough を拡張'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 12d195caa11cd33b4e450e5a57699da4037ed4a2
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696352"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="962bb-102">方法: Task.WhenAll (Visual Basic) を使用して Asyncwalkthrough を拡張</span><span class="sxs-lookup"><span data-stu-id="962bb-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="962bb-103">非同期ソリューションのパフォーマンスを向上できる[チュートリアル: を使用して Async および Await (Visual Basic) で Web にアクセスする](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)を使用して、<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="962bb-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="962bb-104">このメソッドは、タスクのコレクションとして表される、複数の非同期操作を非同期に待機します。</span><span class="sxs-lookup"><span data-stu-id="962bb-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="962bb-105">このチュートリアルでは、Web サイトが異なる速度でダウンロードされることに気付きます。</span><span class="sxs-lookup"><span data-stu-id="962bb-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="962bb-106">Web サイトの 1 つが非常に低速な場合があります。これは残りのすべてのダウンロードを遅延させます。</span><span class="sxs-lookup"><span data-stu-id="962bb-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="962bb-107">このチュートリアルで構築した非同期ソリューションを実行すると、プログラムを待たない場合には簡単に終了することができますが、よりよい方法は、すべてのダウンロードを同時に開始して、遅延したダウンロードを待たずに早いダウンロードが継続できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="962bb-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="962bb-108">タスクのコレクションに `Task.WhenAll` メソッドを適用します。</span><span class="sxs-lookup"><span data-stu-id="962bb-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="962bb-109">`WhenAll` を適用すると、コレクション内のすべてのタスクが完了するまで完了しない 1 つのタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="962bb-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="962bb-110">タスクは並列で実行されるように見えますが、追加のスレッドは作成されません。</span><span class="sxs-lookup"><span data-stu-id="962bb-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="962bb-111">タスクは任意の順序で完了します。</span><span class="sxs-lookup"><span data-stu-id="962bb-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="962bb-112">次の手順で開発された非同期アプリケーションの拡張機能を説明する[チュートリアル: を使用して Async および Await (Visual Basic) で Web へのアクセス](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。</span><span class="sxs-lookup"><span data-stu-id="962bb-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="962bb-113">チュートリアルを完了するか、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)からコードをダウンロードして、アプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="962bb-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="962bb-114">例を実行するには、Visual Studio 2012 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="962bb-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="962bb-115">GetURLContentsAsync ソリューションに Task.WhenAll を追加するには</span><span class="sxs-lookup"><span data-stu-id="962bb-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="962bb-116">追加、`ProcessURLAsync`メソッドで開発された最初のアプリケーションを[チュートリアル: を使用して Async および Await (Visual Basic) で Web へのアクセス](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。</span><span class="sxs-lookup"><span data-stu-id="962bb-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="962bb-117">コードをダウンロードしている場合[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)AsyncWalkthrough プロジェクトを開き、追加`ProcessURLAsync`MainWindow.xaml.vb ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="962bb-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="962bb-118">チュートリアルを実行してコードを開発する場合は、`ProcessURLAsync` メソッドを含むアプリケーションに `GetURLContentsAsync` を追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="962bb-119">このアプリケーションの MainWindow.xaml.vb ファイルは、「完全なコードからチュートリアル例」セクション最初の例です。</span><span class="sxs-lookup"><span data-stu-id="962bb-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="962bb-120">`ProcessURLAsync` メソッドは、元のチュートリアルの `SumPageSizesAsync` の `For Each` ループの本体にあるアクションを統合します。</span><span class="sxs-lookup"><span data-stu-id="962bb-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="962bb-121">このメソッドは、指定した Web サイトのコンテンツをバイト配列として非同期的にダウンロードし、バイト配列の長さを表示して返します。</span><span class="sxs-lookup"><span data-stu-id="962bb-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="962bb-122">次のコードに示すように、`SumPageSizesAsync` の `For Each` ループをコメント アウトするか削除します。</span><span class="sxs-lookup"><span data-stu-id="962bb-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  <span data-ttu-id="962bb-123">タスクのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="962bb-123">Create a collection of tasks.</span></span> <span data-ttu-id="962bb-124">次のコードは、<xref:System.Linq.Enumerable.ToArray%2A> メソッドによって実行されるときに、各 Web サイトのコンテンツをダウンロードするタスクのコレクションを作成する[クエリ](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)を定義します。</span><span class="sxs-lookup"><span data-stu-id="962bb-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="962bb-125">タスクは、クエリが評価されるときに開始されます。</span><span class="sxs-lookup"><span data-stu-id="962bb-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="962bb-126">`SumPageSizesAsync` の宣言の後の `urlList` メソッドに、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="962bb-127">`Task.WhenAll` をタスクのコレクション `downloadTasks` に適用します。</span><span class="sxs-lookup"><span data-stu-id="962bb-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="962bb-128">`Task.WhenAll` は、タスクのコレクションのすべてのタスクが完了すると完了する、単一のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="962bb-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="962bb-129">次の例では、`Await` 式は、`WhenAll` によって返される単一のタスクが完了するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="962bb-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="962bb-130">式は、各整数がダウンロードされたサイトの長さである、整数の配列に評価します。</span><span class="sxs-lookup"><span data-stu-id="962bb-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="962bb-131">`SumPageSizesAsync` の、前の手順で追加したコードの直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="962bb-132">最後に <xref:System.Linq.Enumerable.Sum%2A> メソッドを使って、すべての Web サイトの長さの合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="962bb-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="962bb-133">`SumPageSizesAsync` に次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="962bb-134">HttpClient.GetByteArrayAsync ソリューションに Task.WhenAll を追加するには</span><span class="sxs-lookup"><span data-stu-id="962bb-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="962bb-135">次のバージョンの追加`ProcessURLAsync`で開発された 2 つ目のアプリケーションに[チュートリアル: を使用して Async および Await (Visual Basic) で Web へのアクセス](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。</span><span class="sxs-lookup"><span data-stu-id="962bb-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="962bb-136">コードをダウンロードしている場合[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)AsyncWalkthrough_HttpClient プロジェクトを開き、追加`ProcessURLAsync`MainWindow.xaml.vb ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="962bb-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="962bb-137">チュートリアルを実行してコードを開発する場合は、`ProcessURLAsync` メソッドを使うアプリケーションに `HttpClient.GetByteArrayAsync` を追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="962bb-138">このアプリケーションの MainWindow.xaml.vb ファイルは、「完全なコードからチュートリアル例」セクションに 2 番目の例を示します。</span><span class="sxs-lookup"><span data-stu-id="962bb-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="962bb-139">`ProcessURLAsync` メソッドは、元のチュートリアルの `SumPageSizesAsync` の `For Each` ループの本体にあるアクションを統合します。</span><span class="sxs-lookup"><span data-stu-id="962bb-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="962bb-140">このメソッドは、指定した Web サイトのコンテンツをバイト配列として非同期的にダウンロードし、バイト配列の長さを表示して返します。</span><span class="sxs-lookup"><span data-stu-id="962bb-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="962bb-141">前の手順の `ProcessURLAsync` メソッドとの唯一の違いは、<xref:System.Net.Http.HttpClient> インスタンス `client` の使用です。</span><span class="sxs-lookup"><span data-stu-id="962bb-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="962bb-142">次のコードに示すように、`SumPageSizesAsync` の `For Each` ループをコメント アウトするか削除します。</span><span class="sxs-lookup"><span data-stu-id="962bb-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3.  <span data-ttu-id="962bb-143"><xref:System.Linq.Enumerable.ToArray%2A> メソッドによって実行されるときに、各 Web サイトのコンテンツをダウンロードするタスクのコレクションを作成する[クエリ](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)を定義します。</span><span class="sxs-lookup"><span data-stu-id="962bb-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="962bb-144">タスクは、クエリが評価されるときに開始されます。</span><span class="sxs-lookup"><span data-stu-id="962bb-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="962bb-145">`SumPageSizesAsync` および `client` の宣言の後の `urlList` メソッドに、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="962bb-146">次に、`Task.WhenAll` をタスクのコレクション `downloadTasks` に適用します。</span><span class="sxs-lookup"><span data-stu-id="962bb-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="962bb-147">`Task.WhenAll` は、タスクのコレクションのすべてのタスクが完了すると完了する、単一のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="962bb-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="962bb-148">次の例では、`Await` 式は、`WhenAll` によって返される単一のタスクが完了するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="962bb-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="962bb-149">完了すると、`Await` 式は、各整数がダウンロードされたサイトの長さである、整数の配列に評価します。</span><span class="sxs-lookup"><span data-stu-id="962bb-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="962bb-150">`SumPageSizesAsync` の、前の手順で追加したコードの直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="962bb-151">最後に <xref:System.Linq.Enumerable.Sum%2A> メソッドを使って、すべての Web サイトの長さの合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="962bb-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="962bb-152">`SumPageSizesAsync` に次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="962bb-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="962bb-153">Task.WhenAll ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="962bb-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="962bb-154">各ソリューションで、F5 キーを押してプログラムを実行し、**[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="962bb-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="962bb-155">出力に含まれる async ソリューションからの出力のようになります[チュートリアル: を使用して Async および Await (Visual Basic) で Web へのアクセス](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)です。</span><span class="sxs-lookup"><span data-stu-id="962bb-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="962bb-156">ただし、Web サイトは毎回、異なる順序で表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="962bb-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="962bb-157">例</span><span class="sxs-lookup"><span data-stu-id="962bb-157">Example</span></span>  
 <span data-ttu-id="962bb-158">次のコードは、`GetURLContentsAsync` メソッドを使用して Web からコンテンツをダウンロードするプロジェクトの拡張機能を示します。</span><span class="sxs-lookup"><span data-stu-id="962bb-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
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
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a><span data-ttu-id="962bb-159">例</span><span class="sxs-lookup"><span data-stu-id="962bb-159">Example</span></span>  
 <span data-ttu-id="962bb-160">次のコードは、`HttpClient.GetByteArrayAsync` メソッドを使用して Web からコンテンツをダウンロードするプロジェクトの拡張機能を示します。</span><span class="sxs-lookup"><span data-stu-id="962bb-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="962bb-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="962bb-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="962bb-162">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="962bb-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
