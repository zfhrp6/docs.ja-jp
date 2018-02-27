---
title: "非同期タスクまたはタスクの一覧のキャンセル (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3003c7b4a10890ddf7faa098ed672ef40b591b30
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="5615d-102">非同期タスクまたはタスクの一覧のキャンセル (C#)</span><span class="sxs-lookup"><span data-stu-id="5615d-102">Cancel an Async Task or a List of Tasks (C#)</span></span>
<span data-ttu-id="5615d-103">非同期のアプリケーションが終了するまで待機しない場合、それを取り消すために使用できるボタンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5615d-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="5615d-104">このトピックの例に従うと、1 つの Web サイトのコンテンツまたは Web サイトのリストをダウンロードするアプリケーションにキャンセル ボタンを追加できます。</span><span class="sxs-lookup"><span data-stu-id="5615d-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="5615d-105">例では、「[非同期アプリケーションの微調整 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)」で説明している UI を使用しています。</span><span class="sxs-lookup"><span data-stu-id="5615d-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5615d-106">この例を実行するには、コンピューターに Visual Studio 2012 以降および .NET Framework 4.5 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5615d-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a><span data-ttu-id="5615d-107">タスクのキャンセル</span><span class="sxs-lookup"><span data-stu-id="5615d-107">Cancel a Task</span></span>  
 <span data-ttu-id="5615d-108">最初の例では、**キャンセル** ボタンを単一のダウンロード タスクと関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5615d-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="5615d-109">アプリケーションがコンテンツをダウンロード中にボタンをクリックすると、ダウンロードは取り消されます。</span><span class="sxs-lookup"><span data-stu-id="5615d-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="5615d-110">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="5615d-110">Downloading the Example</span></span>  
 <span data-ttu-id="5615d-111">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5615d-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="5615d-112">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="5615d-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5615d-113">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="5615d-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="5615d-114">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5615d-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="5615d-115">**ソリューション エクスプローラー**で、**CancelATask** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5615d-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="5615d-116">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5615d-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="5615d-117">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5615d-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="5615d-118">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="5615d-118">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="5615d-119">例のビルド</span><span class="sxs-lookup"><span data-stu-id="5615d-119">Building the Example</span></span>  
 <span data-ttu-id="5615d-120">次の変更は、Web サイトをダウンロードするアプリケーションに**キャンセル** ボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="5615d-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="5615d-121">この例のダウンロードまたはビルドをしない場合は、このトピックの最後にある「コード例全体」のセクションで最終製品をレビューできます。</span><span class="sxs-lookup"><span data-stu-id="5615d-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="5615d-122">アスタリスクはコードの変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="5615d-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="5615d-123">この例を自分でビルドするには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** として、**[CancelATask]** の代わりに **[StarterCode]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5615d-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="5615d-124">次の変更点をプロジェクトの MainWindow.xaml.cs ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="5615d-124">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>  
  
1.  <span data-ttu-id="5615d-125">アクセスするすべてのメソッドのスコープである `CancellationTokenSource` 変数、`cts` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="5615d-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="5615d-126">次のような**キャンセル** ボタンのイベント ハンドラーのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5615d-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="5615d-127">ユーザーが取り消しを要求すると、イベント ハンドラーは <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> メソッドを使って `cts` に通知します。</span><span class="sxs-lookup"><span data-stu-id="5615d-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```csharp  
    // ***Add an event handler for the Cancel button.  
    private void cancelButton_Click(object sender, RoutedEventArgs e)  
    {  
        if (cts != null)  
        {  
            cts.Cancel();  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="5615d-128">**開始**ボタン `startButton_Click` のためのイベント ハンドラーに次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="5615d-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="5615d-129">`CancellationTokenSource`、`cts` をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="5615d-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   <span data-ttu-id="5615d-130">指定された Web サイトのコンテンツをダウンロードする `AccessTheWebAsync` の呼び出しでは、引数として <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> の `cts` プロパティを送ります。</span><span class="sxs-lookup"><span data-stu-id="5615d-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="5615d-131">取り消しが要求されると、`Token` プロパティがメッセージを伝達します。</span><span class="sxs-lookup"><span data-stu-id="5615d-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="5615d-132">ユーザーがダウンロード操作の取り消しを選択するとメッセージを表示する catch ブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="5615d-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="5615d-133">次のコードは変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="5615d-133">The following code shows the changes.</span></span>  
  
        ```csharp  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
        // *** If cancellation is requested, an OperationCanceledException results.  
        catch (OperationCanceledException)  
        {  
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
        }  
        catch (Exception)  
        {  
            resultsTextBox.Text += "\r\nDownload failed.\r\n";  
        }  
        ```  
  
4.  <span data-ttu-id="5615d-134">`AccessTheWebAsync` では、Web サイトのコンテンツをダウンロードするために <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 型の `GetAsync` メソッドの <xref:System.Net.Http.HttpClient> オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5615d-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="5615d-135">2 番目の引数として、`ct` の <xref:System.Threading.CancellationToken> パラメーターである `AccessTheWebAsync` を渡します。</span><span class="sxs-lookup"><span data-stu-id="5615d-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="5615d-136">ユーザーが**キャンセル** ボタンをクリックすると、トークンがメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="5615d-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="5615d-137">次のコードは、`AccessTheWebAsync` の変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="5615d-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  <span data-ttu-id="5615d-138">プログラムの取り消しをしない場合、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="5615d-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="5615d-139">プログラムがコンテンツのダウンロードを終了する前に**キャンセル** ボタンをクリックすると、プログラムは次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="5615d-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a><span data-ttu-id="5615d-140">タスクの一覧を取り消す</span><span class="sxs-lookup"><span data-stu-id="5615d-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="5615d-141">前の例を拡張すると、同じ `CancellationTokenSource` のインスタンスを各タスクに関連付けることによって、多数のタスクを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="5615d-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="5615d-142">**キャンセル** ボタンをクリックすると、完了していないすべてのタスクを取り消します。</span><span class="sxs-lookup"><span data-stu-id="5615d-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="5615d-143">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="5615d-143">Downloading the Example</span></span>  
 <span data-ttu-id="5615d-144">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5615d-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="5615d-145">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="5615d-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5615d-146">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="5615d-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="5615d-147">**[プロジェクトを開く]** ダイアログ ボックスで、圧縮解除したサンプル コードを含むフォルダーを開き、AsyncFineTuningCS のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="5615d-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="5615d-148">**ソリューション エクスプローラー**で、**CancelAListOfTasks** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5615d-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="5615d-149">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5615d-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="5615d-150">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="5615d-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="5615d-151">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.cs ファイルをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="5615d-151">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="5615d-152">例のビルド</span><span class="sxs-lookup"><span data-stu-id="5615d-152">Building the Example</span></span>  
 <span data-ttu-id="5615d-153">この例を自分で拡張するには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** として **CancelATask** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5615d-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="5615d-154">次の変更点をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5615d-154">Add the following changes to that project.</span></span> <span data-ttu-id="5615d-155">アスタリスクはプログラムの変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="5615d-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="5615d-156">Web アドレスのリストを作成するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="5615d-156">Add a method to create a list of web addresses.</span></span>  
  
    ```csharp  
    // ***Add a method that creates a list of web addresses.  
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
    ```  
  
2.  <span data-ttu-id="5615d-157">`AccessTheWebAsync` のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5615d-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  <span data-ttu-id="5615d-158">次のループを `AccessTheWebAsync` に追加して、リストの各 Web アドレスを処理します。</span><span class="sxs-lookup"><span data-stu-id="5615d-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```csharp  
    // ***Add a loop to process the list of web addresses.  
    foreach (var url in urlList)  
    {  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // Argument ct carries the message if the Cancel button is chosen.   
        // ***Note that the Cancel button can cancel all remaining downloads.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  <span data-ttu-id="5615d-159">`AccessTheWebAsync` は長さを表示するため、メソッドは何も返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5615d-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="5615d-160">return ステートメントを削除し、メソッドの戻り値の型を <xref:System.Threading.Tasks.Task> ではなく <xref:System.Threading.Tasks.Task%601> に変更します。</span><span class="sxs-lookup"><span data-stu-id="5615d-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     <span data-ttu-id="5615d-161">式の代わりにステートメントを使って、`startButton_Click` からメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5615d-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  <span data-ttu-id="5615d-162">プログラムの取り消しをしない場合、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="5615d-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     <span data-ttu-id="5615d-163">ダウンロードが完了する前に**キャンセル** ボタンをクリックすると、出力には取り消しの前に完了したダウンロードの長さが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5615d-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a><span data-ttu-id="5615d-164">コード例全体</span><span class="sxs-lookup"><span data-stu-id="5615d-164">Complete Examples</span></span>  
 <span data-ttu-id="5615d-165">次のセクションには、前の例の各コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5615d-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="5615d-166"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5615d-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="5615d-167">このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="5615d-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="5615d-168">タスクを取り消す例</span><span class="sxs-lookup"><span data-stu-id="5615d-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="5615d-169">次のコードは、単一のタスクを取り消す例での MainWindow.xaml.cs ファイルの全体です。</span><span class="sxs-lookup"><span data-stu-id="5615d-169">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>  
  
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
  
// Add the following using directive for System.Threading.  
  
using System.Threading;  
namespace CancelATask  
{  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // ***Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Send a token to carry the message if cancellation is requested.  
                int contentLength = await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
            // *** If cancellation is requested, an OperationCanceledException results.  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.\r\n";  
            }  
  
            // ***Set the CancellationTokenSource to null when the download is complete.  
            cts = null;   
        }  
  
        // ***Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // ***Provide a parameter for the CancellationToken.  
        async Task<int> AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            // The result of the method is the length of the downloaded website.  
            return urlContents.Length;  
        }  
    }  
  
    // Output for a successful download:  
  
    // Ready to download.  
  
    // Length of the downloaded string: 158125.  
  
    // Or, if you cancel:  
  
    // Ready to download.  
  
    // Download canceled.  
}  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="5615d-170">タスクの一覧を取り消す例</span><span class="sxs-lookup"><span data-stu-id="5615d-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="5615d-171">次のコードは、タスクの一覧を取り消す例での MainWindow.xaml.cs ファイルの全体です。</span><span class="sxs-lookup"><span data-stu-id="5615d-171">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>  
  
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
  
// Add the following using directive for System.Threading.  
using System.Threading;  
  
namespace CancelAListOfTasks  
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
                // ***Small change in the display lines.  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        // ***Change the return type to Task because the method has no return statement.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // ***Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Add a loop to process the list of web addresses.  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // ***Note that the Cancel button can cancel all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
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
  
    // Output if you do not choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Length of the downloaded string: 158124.  
  
    //Length of the downloaded string: 204890.  
  
    //Length of the downloaded string: 175488.  
  
    //Length of the downloaded string: 145790.  
  
    //Downloads complete.  
  
    // Sample output if you choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Downloads canceled.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5615d-172">参照</span><span class="sxs-lookup"><span data-stu-id="5615d-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="5615d-173">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="5615d-173">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="5615d-174">非同期アプリケーションの微調整 (C#)</span><span class="sxs-lookup"><span data-stu-id="5615d-174">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="5615d-175">非同期のサンプル: アプリケーションの微調整</span><span class="sxs-lookup"><span data-stu-id="5615d-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
