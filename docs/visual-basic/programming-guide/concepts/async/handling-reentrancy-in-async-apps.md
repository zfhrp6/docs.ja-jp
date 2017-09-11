---
title: "(Visual Basic) の非同期アプリにおける再入の処理 |Microsoft ドキュメント"
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
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 8c35f0b393f38ea32f456a60ebd520065d16c6eb
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="30602-102">(Visual Basic) の非同期アプリにおける再入の処理</span><span class="sxs-lookup"><span data-stu-id="30602-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="30602-103">非同期コードをアプリに含める場合は、再入を考慮し、場合によっては回避することをお勧めします。これは、完了前に非同期操作の再入力を参照します。</span><span class="sxs-lookup"><span data-stu-id="30602-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="30602-104">再入の可能性を特定して処理しないと、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="30602-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="30602-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="30602-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="30602-106">再入を認識</span><span class="sxs-lookup"><span data-stu-id="30602-106">Recognizing Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="30602-107">再入の処理</span><span class="sxs-lookup"><span data-stu-id="30602-107">Handling Reentrancy</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   <span data-ttu-id="30602-108">[[スタート] ボタンを無効にします。](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)</span><span class="sxs-lookup"><span data-stu-id="30602-108">[Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)</span></span>  
  
    -   [<span data-ttu-id="30602-109">キャンセルし、操作を再開</span><span class="sxs-lookup"><span data-stu-id="30602-109">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="30602-110">複数の操作を実行し、キューの出力</span><span class="sxs-lookup"><span data-stu-id="30602-110">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="30602-111">確認して、アプリケーションの例を実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-111">Reviewing and Running the Example App</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="30602-112">例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="30602-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="30602-113"><a name="BKMK_RecognizingReentrancy"></a>再入を認識</span><span class="sxs-lookup"><span data-stu-id="30602-113"><a name="BKMK_RecognizingReentrancy"></a> Recognizing Reentrancy</span></span>  
 <span data-ttu-id="30602-114">このトピックの例では、ユーザーが選択、**開始**を一連の web サイトをダウンロードして、ダウンロードされるバイト数の合計を計算する非同期のアプリを開始 ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="30602-115">同期バージョンの例では、ユーザーが何回ボタンをクリックしても同じように応答します。2 回目以降はアプリが実行を完了するまで、UI スレッドはこれらのイベントを無視するからです。</span><span class="sxs-lookup"><span data-stu-id="30602-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="30602-116">ただし、非同期アプリでは、UI スレッドは応答し続けるので、完了前に非同期操作を再入力することがあります。</span><span class="sxs-lookup"><span data-stu-id="30602-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="30602-117">次の例は、予想される、ユーザーが選択したかどうかの出力、**開始**一度だけ ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="30602-118">ダウンロードされた Web サイトの一覧には、各サイトのサイズがバイト単位で表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="30602-119">合計バイト数は最後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="30602-120">ただし、ユーザーがボタンを複数回クリックすると、イベント ハンドラーは繰り返し呼び出され、ダウンロード プロセスはそのたびに再入力されます。</span><span class="sxs-lookup"><span data-stu-id="30602-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="30602-121">その結果、複数の非同期操作が同時に実行され、出力は結果をインターリーブするので、合計バイト数がややこしくなります。</span><span class="sxs-lookup"><span data-stu-id="30602-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="30602-122">このトピックの最後にスクロールすると、この出力を生成するコードをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="30602-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="30602-123">ローカル コンピューターに、ソリューションをダウンロードし、WebsiteDownload プロジェクトを実行してコードを試してみるか、コードは、このトピックの最後に使用すると詳細と手順については、独自のプロジェクトを作成する、次を参照してください。[確認して、アプリケーションの例を実行する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)です。</span><span class="sxs-lookup"><span data-stu-id="30602-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <span data-ttu-id="30602-124"><a name="BKMK_HandlingReentrancy"></a>再入の処理</span><span class="sxs-lookup"><span data-stu-id="30602-124"><a name="BKMK_HandlingReentrancy"></a> Handling Reentrancy</span></span>  
 <span data-ttu-id="30602-125">再入の処理は、アプリで何を行うかに応じてさまざまな方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="30602-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="30602-126">このトピックでは、次の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="30602-126">This topic presents the following examples:</span></span>  
  
-   <span data-ttu-id="30602-127">[[スタート] ボタンを無効にします。](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)</span><span class="sxs-lookup"><span data-stu-id="30602-127">[Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)</span></span>  
  
     <span data-ttu-id="30602-128">無効にする、**開始**ユーザーが中断できないように、操作の実行中にボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="30602-129">キャンセルし、操作を再開</span><span class="sxs-lookup"><span data-stu-id="30602-129">Cancel and Restart the Operation</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="30602-130">ユーザーが選択したときに実行されているすべての操作をキャンセル、**開始**を再度クリックし、続行できるように、最後に要求された操作。</span><span class="sxs-lookup"><span data-stu-id="30602-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="30602-131">複数の操作を実行し、キューの出力</span><span class="sxs-lookup"><span data-stu-id="30602-131">Run Multiple Operations and Queue the Output</span></span>](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="30602-132">要求されたすべての処理を非同期的に実行できるようにします。ただし、各処理の結果が順番にまとめて表示されるように出力を調整します。</span><span class="sxs-lookup"><span data-stu-id="30602-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <span data-ttu-id="30602-133"><a name="BKMK_DisableTheStartButton"></a>[スタート] ボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="30602-133"><a name="BKMK_DisableTheStartButton"></a> Disable the Start Button</span></span>  
 <span data-ttu-id="30602-134">ブロックすることができます、**開始**ボタンの上部にあるボタンを無効にすると、操作の実行中に、`StartButton_Click`イベント ハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="30602-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="30602-135">処理が完了しユーザーが再度アプリを実行できるようになったら、`Finally` ブロック内からこのボタンを再度有効にできます。</span><span class="sxs-lookup"><span data-stu-id="30602-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="30602-136">次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="30602-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="30602-137">変更内容を追加するには、このトピックの最後のコードにかから完成したアプリをダウンロードする[Async のサンプル: .NET デスクトップ アプリにおける再入](http://go.microsoft.com/fwlink/?LinkId=266571)します。</span><span class="sxs-lookup"><span data-stu-id="30602-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="30602-138">プロジェクト名は DisableStartButton です。</span><span class="sxs-lookup"><span data-stu-id="30602-138">The project name is DisableStartButton.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="30602-139">変更の結果、`AccessTheWebAsync` が Web サイトをダウンロードしている間は、ボタンが応答しないので、プロセスを再入力できません。</span><span class="sxs-lookup"><span data-stu-id="30602-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <span data-ttu-id="30602-140"><a name="BKMK_CancelAndRestart"></a>キャンセルし、操作を再開</span><span class="sxs-lookup"><span data-stu-id="30602-140"><a name="BKMK_CancelAndRestart"></a> Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="30602-141">無効にせず、**開始** ボタンをすることができます、ボタンをアクティブにしておくが、ここでも、そのボタンを選択した場合、処理を取り消しが既に実行されていると、最後に開始された処理を続行します。</span><span class="sxs-lookup"><span data-stu-id="30602-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="30602-142">キャンセルの詳細については、次を参照してください。[微調整 Your Async アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="30602-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="30602-143">このシナリオをセットアップするには、基本的なコードで提供されている次の変更を加えて[確認して、アプリケーションの例を実行する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)です。</span><span class="sxs-lookup"><span data-stu-id="30602-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="30602-144">ダウンロードすることも、完了したアプリから[Async のサンプル: .NET デスクトップ アプリにおける再入](http://go.microsoft.com/fwlink/?LinkId=266571)します。</span><span class="sxs-lookup"><span data-stu-id="30602-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span> <span data-ttu-id="30602-145">このプロジェクトの名前は CancelAndRestart です。</span><span class="sxs-lookup"><span data-stu-id="30602-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="30602-146">宣言、<xref:System.Threading.CancellationTokenSource>変数`cts`、すべてのメソッドのスコープである</xref:System.Threading.CancellationTokenSource>。</span><span class="sxs-lookup"><span data-stu-id="30602-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="30602-147">`StartButton_Click` で、処理が既に実行されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="30602-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="30602-148">場合の値`cts`は`Nothing`操作は既にアクティブです。</span><span class="sxs-lookup"><span data-stu-id="30602-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="30602-149">値がない場合`Nothing`、既に実行されている操作が取り消されました。</span><span class="sxs-lookup"><span data-stu-id="30602-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="30602-150">`cts` に、現在のプロセスを表す別の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="30602-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="30602-151">末尾に`StartButton_Click`、現在のプロセスが完了したら、そのための値を設定`cts`に`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="30602-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="30602-152">次のコードは、`StartButton_Click` のすべての変更を示しています。</span><span class="sxs-lookup"><span data-stu-id="30602-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="30602-153">追加部分はアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="30602-153">The additions are marked with asterisks.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 <span data-ttu-id="30602-154">`AccessTheWebAsync` で、次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="30602-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="30602-155">`StartButton_Click` からキャンセル トークンを受け取るためのパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="30602-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="30602-156">使用して、<xref:System.Net.Http.HttpClient.GetAsync%2A>ために、web サイトをダウンロードする方法`GetAsync`を受け入れる、<xref:System.Threading.CancellationToken>引数</xref:System.Threading.CancellationToken></xref:System.Net.Http.HttpClient.GetAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="30602-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="30602-157">`DisplayResults` を呼び出してダウンロードした各 Web サイトの結果を表示する前に、`ct` で、現在の処理が取り消されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="30602-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="30602-158">次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="30602-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="30602-159">選択した場合、**開始**を複数回クリックしてこのアプリの実行中には、次の出力のような結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="30602-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="30602-160">部分的なリストを削除するには、`StartButton_Click` コードの先頭行のコメントを解除して、ユーザーが操作を再開するたびに、テキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="30602-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <span data-ttu-id="30602-161"><a name="BKMK_RunMultipleOperations"></a>複数の操作を実行し、キューの出力</span><span class="sxs-lookup"><span data-stu-id="30602-161"><a name="BKMK_RunMultipleOperations"></a> Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="30602-162">この&3; 番目の例は、アプリケーション、ユーザーが選択されるたびに非同期操作の開始点で最も複雑な**開始** ボタン、およびすべての操作が完了するまで実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="30602-163">要求されたすべての操作によって Web サイトがリストから非同期的にダウンロードされますが、操作からの出力は順次表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="30602-164">つまり、実際のダウンロード アクティビティはインターリーブされますに出力として[を認識する再入](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)が示すように、各グループの結果のリストは個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="30602-165">操作共有グローバル<xref:System.Threading.Tasks.Task>、 `pendingWork`、これは、表示プロセスのゲートキーパーとして機能します</xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="30602-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="30602-166">内のコードに変更内容を貼り付けることによってこの例を実行する[アプリケーションを構築する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、」の手順に従うこともできます[アプリをダウンロードする](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)サンプルをダウンロードし、QueueResults プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-166">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="30602-167">次の出力は、ユーザーが選択したかどうか、結果を示します、**開始**一度だけ ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="30602-168">文字ラベル A は、初めてから結果であることを示します、**開始**ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="30602-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="30602-169">数字は、ダウンロード対象の一覧における URL の順序を示しています。</span><span class="sxs-lookup"><span data-stu-id="30602-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="30602-170">ユーザーが選択した場合、**開始**ボタンを&3; 回、アプリには、次の行のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="30602-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="30602-171">先頭にシャープ記号 (#) が付いている情報行は、アプリケーションの進行状況を追跡します。</span><span class="sxs-lookup"><span data-stu-id="30602-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="30602-172">グループ B とグループ C は、グループ A が終了する前に開始します。ただし、各グループの出力は個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="30602-173">グループ A のすべての出力は表示グループ B のすべての出力とすべての出力グループ C. に続く&1; つは、アプリケーションは必ずの順序でグループを表示され、グループごとに、Url は、Url の一覧に表示される順序で常に個別の web サイトに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="30602-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="30602-174">ただし、ダウンロードが実際に行われる順序は予測できません。</span><span class="sxs-lookup"><span data-stu-id="30602-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="30602-175">複数のグループが開始されたら、そのグループが生成するダウンロード タスクはすべてのアクティブです。</span><span class="sxs-lookup"><span data-stu-id="30602-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="30602-176">B-1 の前に A-1 がダウンロードされる、また、A-2 の前に A-1 がダウンロードされると仮定することはできません。</span><span class="sxs-lookup"><span data-stu-id="30602-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="30602-177">グローバル定義</span><span class="sxs-lookup"><span data-stu-id="30602-177">Global Definitions</span></span>  
 <span data-ttu-id="30602-178">サンプル コードには、すべてのメソッドから参照できる次の&2; つのグローバル宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="30602-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="30602-179">`Task` 変数、`pendingWork` は、表示プロセスを監視し、あるグループが別のグループの表示操作を中断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="30602-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="30602-180">文字変数 `group` は、異なるグループからの出力にラベルを付け、予想された順序で結果が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="30602-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="30602-181">Click イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="30602-181">The Click Event Handler</span></span>  
 <span data-ttu-id="30602-182">イベント ハンドラー `StartButton_Click`、インクリメントします、ユーザーが選択するたびに、**開始** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="30602-183">ハンドラーは `AccessTheWebAsync` を呼び出して、ダウンロード操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="30602-184">AccessTheWebAsync メソッド</span><span class="sxs-lookup"><span data-stu-id="30602-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="30602-185">この例では、`AccessTheWebAsync` を&2; つのメソッドに分割します。</span><span class="sxs-lookup"><span data-stu-id="30602-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="30602-186">最初のメソッド、`AccessTheWebAsync` は、グループのすべてのダウンロード タスクを開始し、`pendingWork` を設定して表示プロセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="30602-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="30602-187">メソッドは、言語統合クエリ (LINQ クエリ) を使用し、<xref:System.Linq.Enumerable.ToArray%2A>を同時にすべてのダウンロード タスクを開始します</xref:System.Linq.Enumerable.ToArray%2A>。</span><span class="sxs-lookup"><span data-stu-id="30602-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="30602-188">その後、`AccessTheWebAsync` は、`FinishOneGroupAsync` を呼び出して各ダウンロードが完了するまで待機し、その長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="30602-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="30602-189">`FinishOneGroupAsync` は、`pendingWork` の `AccessTheWebAsync` に割り当てられたタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="30602-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="30602-190">この値は、タスクが完了する前に、別の操作によって操作が中断されないようにします。</span><span class="sxs-lookup"><span data-stu-id="30602-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="30602-191">FinishOneGroupAsync メソッド</span><span class="sxs-lookup"><span data-stu-id="30602-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="30602-192">このメソッドは、グループのダウンロード タスクを循環参照し、それぞれを待機してから、ダウンロードされた Web サイトの長さを表示して、その長さを合計に追加します。</span><span class="sxs-lookup"><span data-stu-id="30602-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="30602-193">最初のステートメントで`FinishOneGroupAsync`を使用して`pendingWork`するメソッドを入力する妨げにならないで操作を実行、表示プロセスにではないかを既に待機しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="30602-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="30602-194">これらの操作が進行中の場合、入力操作は順番を待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="30602-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="30602-195">内のコードに変更内容を貼り付けることによってこの例を実行する[アプリケーションを構築する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、」の手順に従うこともできます[アプリをダウンロードする](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)サンプルをダウンロードし、QueueResults プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-195">You can run this example by pasting the changes into the code in [Building the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="30602-196">目的のポイント</span><span class="sxs-lookup"><span data-stu-id="30602-196">Points of Interest</span></span>  
 <span data-ttu-id="30602-197">出力で先頭にシャープ記号 (#) が付いている情報行は、この例の動作を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="30602-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="30602-198">出力のパターンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="30602-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="30602-199">前のグループが出力を表示していても、グループを開始できます。その際、前のグループの出力の表示は中断されません。</span><span class="sxs-lookup"><span data-stu-id="30602-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="30602-200">`pendingWork`タスクは、`Nothing`の開始時`FinishOneGroupAsync`グループ A についてのみが最初に開始します。</span><span class="sxs-lookup"><span data-stu-id="30602-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="30602-201">`FinishOneGroupAsync` に達したとき、グループ A はまだ await 式を完了していません。</span><span class="sxs-lookup"><span data-stu-id="30602-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="30602-202">したがって、コントロールは `AccessTheWebAsync` に戻っておらず、`pendingWork` への最初の割り当ては発生していません。</span><span class="sxs-lookup"><span data-stu-id="30602-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="30602-203">次の&2; 行は、出力に必ず同時に表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="30602-204">`StartButton_Click` のグループ操作が開始してから、グループのタスクが `pendingWork` に割り当てられるまでの間、コードが中断されることは決してありません。</span><span class="sxs-lookup"><span data-stu-id="30602-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="30602-205">グループが `StartButton_Click` に移行したら、`FinishOneGroupAsync` に移行するまでは、await 式は完了しません。</span><span class="sxs-lookup"><span data-stu-id="30602-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="30602-206">したがって、コード セグメントの途中で、他の操作がコントロールを得ることはありません。</span><span class="sxs-lookup"><span data-stu-id="30602-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <span data-ttu-id="30602-207"><a name="BKMD_SettingUpTheExample"></a>確認して、アプリケーションの例を実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-207"><a name="BKMD_SettingUpTheExample"></a> Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="30602-208">サンプル アプリをさらに詳しく理解するには、そのアプリをダウンロードし、ご自身でビルドしてみてください。また、このトピックの最後にあるコードをレビューすることもできます。アプリを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="30602-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30602-209">Windows Presentation Foundation (WPF) デスクトップ アプリとして例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="30602-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <span data-ttu-id="30602-210"><a name="BKMK_DownloadingTheApp"></a>アプリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="30602-210"><a name="BKMK_DownloadingTheApp"></a> Downloading the App</span></span>  
  
1.  <span data-ttu-id="30602-211">圧縮ファイルをダウンロード[Async のサンプル: .NET デスクトップ アプリにおける再入](http://go.microsoft.com/fwlink/?LinkId=266571)します。</span><span class="sxs-lookup"><span data-stu-id="30602-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](http://go.microsoft.com/fwlink/?LinkId=266571).</span></span>  
  
2.  <span data-ttu-id="30602-212">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="30602-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="30602-213">メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="30602-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="30602-214">圧縮解除したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="30602-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="30602-215">**ソリューション エクスプ ローラー**、実行、および順に選択するプロジェクトのショートカット メニューを開いて**スタートアップ プロジェクトに設定として設定**します。</span><span class="sxs-lookup"><span data-stu-id="30602-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="30602-216">Ctrl キーを押しながら F5 キーを押してプロジェクトをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="30602-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <span data-ttu-id="30602-217"><a name="BKMK_BuildingTheApp"></a>アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="30602-217"><a name="BKMK_BuildingTheApp"></a> Building the App</span></span>  
 <span data-ttu-id="30602-218">次のセクションでは、WPF アプリとして例をビルドするコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="30602-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="30602-219">WPF アプリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="30602-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="30602-220">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="30602-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="30602-221">メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="30602-222">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="30602-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="30602-223">**インストールされたテンプレート** ウィンドウで、展開**Visual Basic**、順に展開**Windows**します。</span><span class="sxs-lookup"><span data-stu-id="30602-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="30602-224">プロジェクトの種類の一覧で選択**WPF アプリケーション**します。</span><span class="sxs-lookup"><span data-stu-id="30602-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="30602-225">プロジェクトに名前を`WebsiteDownloadWPF`を選択し、 **OK**  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="30602-226">新しいプロジェクトに表示されます**ソリューション エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="30602-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="30602-227">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="30602-228">タブが表示されない場合で MainWindow.xaml のショートカット メニューを開き**ソリューション エクスプ ローラー**、にして**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="30602-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="30602-229">**XAML** MainWindow.xaml のビューで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="30602-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="30602-230">テキスト ボックスとボタンを含む簡単なウィンドウに表示、**デザイン**MainWindow.xaml のビューです。</span><span class="sxs-lookup"><span data-stu-id="30602-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="30602-231"><xref:System.Net.Http>。</xref:System.Net.Http>への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="30602-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="30602-232">**ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**します。</span><span class="sxs-lookup"><span data-stu-id="30602-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="30602-233">MainWindow.xaml.vb で、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="30602-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="30602-234">CTRL + F5 キーをクリックして、プログラムの実行を**開始**を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="30602-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="30602-235">変更を加える[[スタート] ボタンを無効にする](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、[をキャンセルし、操作を再開](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、または[複数の操作を実行して出力をキュー](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)を行って再入を処理します。</span><span class="sxs-lookup"><span data-stu-id="30602-235">Make the changes from [Disable the Start Button](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30602-236">関連項目</span><span class="sxs-lookup"><span data-stu-id="30602-236">See Also</span></span>  
 <span data-ttu-id="30602-237">[チュートリアル: Async を使用して Web へのアクセスと Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="30602-237">[Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="30602-238"> [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="30602-238"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)</span></span>

