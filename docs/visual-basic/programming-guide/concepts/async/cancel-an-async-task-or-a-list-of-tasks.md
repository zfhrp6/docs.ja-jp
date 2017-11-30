---
title: "非同期タスクまたはタスク (Visual Basic) の一覧をキャンセルします。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 916577107bd65559aed71dc9bb2921969a117e90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="7bf11-102">非同期タスクまたはタスク (Visual Basic) の一覧をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="7bf11-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="7bf11-103">非同期のアプリケーションが終了するまで待機しない場合、それを取り消すために使用できるボタンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="7bf11-104">このトピックの例に従うと、1 つの Web サイトのコンテンツまたは Web サイトのリストをダウンロードするアプリケーションにキャンセル ボタンを追加できます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="7bf11-105">例では、UI を使用している[非同期アプリケーションの微調整 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)について説明します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bf11-106">この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bf11-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="7bf11-107"><a name="BKMK_CancelaTask"></a>タスクのキャンセル</span><span class="sxs-lookup"><span data-stu-id="7bf11-107"><a name="BKMK_CancelaTask"></a> Cancel a Task</span></span>  
 <span data-ttu-id="7bf11-108">最初の例では、**キャンセル** ボタンを単一のダウンロード タスクと関連付けます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="7bf11-109">アプリケーションがコンテンツをダウンロード中にボタンをクリックすると、ダウンロードは取り消されます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="7bf11-110">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7bf11-110">Downloading the Example</span></span>  
 <span data-ttu-id="7bf11-111">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7bf11-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="7bf11-112">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7bf11-113">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="7bf11-114">**プロジェクトを開く** ダイアログ ボックスでは、圧縮解除したサンプル コードが含まれるフォルダーを開き、AsyncFineTuningVB のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="7bf11-115">**ソリューション エクスプローラー**で、**CancelATask** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bf11-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="7bf11-116">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="7bf11-117">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="7bf11-118">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.vb ファイルを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="7bf11-119">例のビルド</span><span class="sxs-lookup"><span data-stu-id="7bf11-119">Building the Example</span></span>  
 <span data-ttu-id="7bf11-120">次の変更は、Web サイトをダウンロードするアプリケーションに**キャンセル** ボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="7bf11-121">この例のダウンロードまたはビルドをしない場合は、このトピックの最後にある「コード例全体」のセクションで最終製品をレビューできます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="7bf11-122">アスタリスクはコードの変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="7bf11-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="7bf11-123">この例を自分でビルドするには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** として、**[CancelATask]** の代わりに **[StarterCode]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="7bf11-124">そのプロジェクトの MainWindow.xaml.vb ファイルに次の変更を追加します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="7bf11-125">アクセスするすべてのメソッドのスコープである `CancellationTokenSource` 変数、`cts` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="7bf11-126">次のような**キャンセル** ボタンのイベント ハンドラーのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="7bf11-127">ユーザーが取り消しを要求すると、イベント ハンドラーは <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> メソッドを使って `cts` に通知します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="7bf11-128">**開始**ボタン `startButton_Click` のためのイベント ハンドラーに次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="7bf11-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="7bf11-129">`CancellationTokenSource`、`cts` をインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="7bf11-130">指定された Web サイトのコンテンツをダウンロードする `AccessTheWebAsync` の呼び出しでは、引数として <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> の `cts` プロパティを送ります。</span><span class="sxs-lookup"><span data-stu-id="7bf11-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="7bf11-131">取り消しが要求されると、`Token` プロパティがメッセージを伝達します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="7bf11-132">ユーザーがダウンロード操作の取り消しを選択するとメッセージを表示する catch ブロックを追加します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="7bf11-133">次のコードは変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="7bf11-133">The following code shows the changes.</span></span>  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  <span data-ttu-id="7bf11-134">`AccessTheWebAsync` では、Web サイトのコンテンツをダウンロードするために <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> 型の `GetAsync` メソッドの <xref:System.Net.Http.HttpClient> オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="7bf11-135">2 番目の引数として、`ct` の <xref:System.Threading.CancellationToken> パラメーターである `AccessTheWebAsync` を渡します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="7bf11-136">ユーザーが**キャンセル** ボタンをクリックすると、トークンがメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="7bf11-137">次のコードは、`AccessTheWebAsync` の変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="7bf11-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="7bf11-138">プログラムの取り消しをしない場合、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="7bf11-139">プログラムがコンテンツのダウンロードを終了する前に**キャンセル** ボタンをクリックすると、プログラムは次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <span data-ttu-id="7bf11-140"><a name="BKMK_CancelaListofTasks"></a>タスクの一覧を取り消す</span><span class="sxs-lookup"><span data-stu-id="7bf11-140"><a name="BKMK_CancelaListofTasks"></a> Cancel a List of Tasks</span></span>  
 <span data-ttu-id="7bf11-141">前の例を拡張すると、同じ `CancellationTokenSource` のインスタンスを各タスクに関連付けることによって、多数のタスクを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="7bf11-142">**キャンセル** ボタンをクリックすると、完了していないすべてのタスクを取り消します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="7bf11-143">例をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7bf11-143">Downloading the Example</span></span>  
 <span data-ttu-id="7bf11-144">完全な Windows Presentation Foundation (WPF) プロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。ダウンロード後、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7bf11-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="7bf11-145">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7bf11-146">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="7bf11-147">**プロジェクトを開く** ダイアログ ボックスでは、圧縮解除したサンプル コードが含まれるフォルダーを開き、AsyncFineTuningVB のソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="7bf11-148">**ソリューション エクスプローラー**で、**CancelAListOfTasks** プロジェクトのショートカット メニューを開き、**[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7bf11-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="7bf11-149">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="7bf11-150">Ctrl + F5 キーを押して、デバッグを行わずにプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="7bf11-151">プロジェクトをダウンロードしない場合は、このトピックの最後の MainWindow.xaml.vb ファイルを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="7bf11-152">例のビルド</span><span class="sxs-lookup"><span data-stu-id="7bf11-152">Building the Example</span></span>  
 <span data-ttu-id="7bf11-153">この例を自分で拡張するには、「例をダウンロードする」のセクションの詳細な手順の指示に従いますが、**[スタートアップ プロジェクト]** として **CancelATask** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="7bf11-154">次の変更点をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-154">Add the following changes to that project.</span></span> <span data-ttu-id="7bf11-155">アスタリスクはプログラムの変更点を示しています。</span><span class="sxs-lookup"><span data-stu-id="7bf11-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="7bf11-156">Web アドレスのリストを作成するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
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
    ```  
  
2.  <span data-ttu-id="7bf11-157">`AccessTheWebAsync` のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="7bf11-158">次のループを `AccessTheWebAsync` に追加して、リストの各 Web アドレスを処理します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  <span data-ttu-id="7bf11-159">`AccessTheWebAsync` は長さを表示するため、メソッドは何も返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7bf11-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="7bf11-160">return ステートメントを削除し、メソッドの戻り値の型を <xref:System.Threading.Tasks.Task> ではなく <xref:System.Threading.Tasks.Task%601> に変更します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="7bf11-161">式の代わりにステートメントを使って、`startButton_Click` からメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="7bf11-162">プログラムの取り消しをしない場合、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="7bf11-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
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
  
     <span data-ttu-id="7bf11-163">ダウンロードが完了する前に**キャンセル** ボタンをクリックすると、出力には取り消しの前に完了したダウンロードの長さが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7bf11-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <span data-ttu-id="7bf11-164"><a name="BKMK_CompleteExamples"></a>コード例全体</span><span class="sxs-lookup"><span data-stu-id="7bf11-164"><a name="BKMK_CompleteExamples"></a> Complete Examples</span></span>  
 <span data-ttu-id="7bf11-165">次のセクションには、前の例の各コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7bf11-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="7bf11-166"><xref:System.Net.Http> の参照を追加する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7bf11-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="7bf11-167">このプロジェクトは「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="7bf11-167">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="7bf11-168">タスクを取り消す例</span><span class="sxs-lookup"><span data-stu-id="7bf11-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="7bf11-169">次のコードは、完全な MainWindow.xaml.vb ファイルを 1 つのタスクを取り消す例です。</span><span class="sxs-lookup"><span data-stu-id="7bf11-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="7bf11-170">タスクの一覧を取り消す例</span><span class="sxs-lookup"><span data-stu-id="7bf11-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="7bf11-171">次のコードは、タスクのリストを取り消す例の完全な MainWindow.xaml.vb ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7bf11-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
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
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bf11-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bf11-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="7bf11-173">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bf11-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="7bf11-174">非同期アプリケーションの微調整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bf11-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="7bf11-175">非同期のサンプル: アプリケーションの微調整</span><span class="sxs-lookup"><span data-stu-id="7bf11-175">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)
