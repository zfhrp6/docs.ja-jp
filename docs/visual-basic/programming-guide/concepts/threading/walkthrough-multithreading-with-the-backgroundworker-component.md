---
title: "BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド |Microsoft ドキュメント"
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
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 88d0711c8e417ae5c95b0e109504b69882015241
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="18ca5-102">チュートリアル: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド</span><span class="sxs-lookup"><span data-stu-id="18ca5-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="18ca5-103">このチュートリアルは、単語の出現回数をテキスト ファイルを検索するマルチ スレッドの Windows フォーム アプリケーションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="18ca5-104">これを示しています。</span><span class="sxs-lookup"><span data-stu-id="18ca5-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="18ca5-105">呼び出すことができるメソッドを使用してクラスを定義する、<xref:System.ComponentModel.BackgroundWorker>コンポーネント</xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="18ca5-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="18ca5-106">によって生成されるイベントを処理、<xref:System.ComponentModel.BackgroundWorker>コンポーネント</xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="18ca5-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="18ca5-107">以降、<xref:System.ComponentModel.BackgroundWorker>メソッドを実行するコンポーネント</xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="18ca5-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="18ca5-108">実装する、`Cancel`停止ボタン、<xref:System.ComponentModel.BackgroundWorker>コンポーネント</xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="18ca5-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="18ca5-109">ユーザー インターフェイスを作成するには</span><span class="sxs-lookup"><span data-stu-id="18ca5-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="18ca5-110">新しい Visual Basic Windows フォーム アプリケーション プロジェクトを開き、という名前のフォームを作成`Form1`します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="18ca5-111">2 つのボタンと&4; つのテキスト ボックスに追加`Form1`します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="18ca5-112">次の表に示すように、オブジェクトの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="18ca5-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="18ca5-113">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="18ca5-113">Object</span></span>|<span data-ttu-id="18ca5-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="18ca5-114">Property</span></span>|<span data-ttu-id="18ca5-115">設定</span><span class="sxs-lookup"><span data-stu-id="18ca5-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="18ca5-116">最初のボタン</span><span class="sxs-lookup"><span data-stu-id="18ca5-116">First button</span></span>|<span data-ttu-id="18ca5-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="18ca5-117">`Name`, `Text`</span></span>|<span data-ttu-id="18ca5-118">スタート、開始</span><span class="sxs-lookup"><span data-stu-id="18ca5-118">Start, Start</span></span>|  
    |<span data-ttu-id="18ca5-119">2 番目のボタン</span><span class="sxs-lookup"><span data-stu-id="18ca5-119">Second button</span></span>|<span data-ttu-id="18ca5-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="18ca5-120">`Name`, `Text`</span></span>|<span data-ttu-id="18ca5-121">[キャンセル]、[キャンセル]</span><span class="sxs-lookup"><span data-stu-id="18ca5-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="18ca5-122">最初のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="18ca5-122">First text box</span></span>|<span data-ttu-id="18ca5-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="18ca5-123">`Name`, `Text`</span></span>|<span data-ttu-id="18ca5-124">SourceFile、""</span><span class="sxs-lookup"><span data-stu-id="18ca5-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="18ca5-125">2 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="18ca5-125">Second text box</span></span>|<span data-ttu-id="18ca5-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="18ca5-126">`Name`, `Text`</span></span>|<span data-ttu-id="18ca5-127">通常、""</span><span class="sxs-lookup"><span data-stu-id="18ca5-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="18ca5-128">3 番目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="18ca5-128">Third text box</span></span>|<span data-ttu-id="18ca5-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="18ca5-129">`Name`, `Text`</span></span>|<span data-ttu-id="18ca5-130">WordsCounted、「0」</span><span class="sxs-lookup"><span data-stu-id="18ca5-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="18ca5-131">4 番目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="18ca5-131">Fourth text box</span></span>|<span data-ttu-id="18ca5-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="18ca5-132">`Name`, `Text`</span></span>|<span data-ttu-id="18ca5-133">LinesCounted、「0」</span><span class="sxs-lookup"><span data-stu-id="18ca5-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="18ca5-134">各テキスト ボックスの横にあるラベルを追加します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-134">Add a label next to each text box.</span></span> <span data-ttu-id="18ca5-135">設定、`Text`次の表に示すように、各ラベルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="18ca5-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="18ca5-136">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="18ca5-136">Object</span></span>|<span data-ttu-id="18ca5-137">プロパティ</span><span class="sxs-lookup"><span data-stu-id="18ca5-137">Property</span></span>|<span data-ttu-id="18ca5-138">設定</span><span class="sxs-lookup"><span data-stu-id="18ca5-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="18ca5-139">最初のラベル</span><span class="sxs-lookup"><span data-stu-id="18ca5-139">First label</span></span>|`Text`|<span data-ttu-id="18ca5-140">[ソース ファイル]</span><span class="sxs-lookup"><span data-stu-id="18ca5-140">Source File</span></span>|  
    |<span data-ttu-id="18ca5-141">2 番目のラベル</span><span class="sxs-lookup"><span data-stu-id="18ca5-141">Second label</span></span>|`Text`|<span data-ttu-id="18ca5-142">文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-142">Compare String</span></span>|  
    |<span data-ttu-id="18ca5-143">3 番目のラベル</span><span class="sxs-lookup"><span data-stu-id="18ca5-143">Third label</span></span>|`Text`|<span data-ttu-id="18ca5-144">単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-144">Matching Words</span></span>|  
    |<span data-ttu-id="18ca5-145">4 番目のラベル</span><span class="sxs-lookup"><span data-stu-id="18ca5-145">Fourth label</span></span>|`Text`|<span data-ttu-id="18ca5-146">行のカウント</span><span class="sxs-lookup"><span data-stu-id="18ca5-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="18ca5-147">BackgroundWorker コンポーネントを作成し、そのイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="18ca5-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="18ca5-148">追加、<xref:System.ComponentModel.BackgroundWorker>コンポーネントから、**コンポーネント**のセクションで、**ツールボックス**をフォームにします</xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="18ca5-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="18ca5-149">フォームのコンポーネント トレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="18ca5-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="18ca5-150">BackgroundWorker1 オブジェクトの次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="18ca5-151">プロパティ</span><span class="sxs-lookup"><span data-stu-id="18ca5-151">Property</span></span>|<span data-ttu-id="18ca5-152">設定</span><span class="sxs-lookup"><span data-stu-id="18ca5-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="18ca5-153">True</span><span class="sxs-lookup"><span data-stu-id="18ca5-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="18ca5-154">True</span><span class="sxs-lookup"><span data-stu-id="18ca5-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="18ca5-155">別のスレッドで実行されるメソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="18ca5-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="18ca5-156">**プロジェクト**] メニューの [選択**クラスの追加**クラスをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="18ca5-157">**新しい項目の追加** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18ca5-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="18ca5-158">選択**クラス**テンプレート ウィンドウから入力`Words.vb`名 フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="18ca5-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="18ca5-159">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18ca5-159">Click **Add**.</span></span> <span data-ttu-id="18ca5-160">`Words`クラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18ca5-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="18ca5-161">`Words` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-161">Add the following code to the `Words` class:</span></span>  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="18ca5-162">スレッドからイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="18ca5-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="18ca5-163">メイン フォームに次のイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-163">Add the following event handlers to your main form:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="18ca5-164">WordCount メソッドを実行して開始し、新しいスレッドを呼び出します</span><span class="sxs-lookup"><span data-stu-id="18ca5-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="18ca5-165">プログラムを次の手順を追加します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-165">Add the following procedures to your program:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="18ca5-166">呼び出す、`StartThread`メソッドから、`Start`フォーム上のボタン。</span><span class="sxs-lookup"><span data-stu-id="18ca5-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="18ca5-167">[キャンセル] ボタンを実装するには、スレッドを停止します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="18ca5-168">呼び出す、`StopThread`プロシージャから、`Click`のイベント ハンドラー、 `Cancel`  ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18ca5-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="18ca5-169">テスト中</span><span class="sxs-lookup"><span data-stu-id="18ca5-169">Testing</span></span>  
 <span data-ttu-id="18ca5-170">正常に動作を確認するアプリケーションをテストできます。</span><span class="sxs-lookup"><span data-stu-id="18ca5-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="18ca5-171">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="18ca5-171">To test the application</span></span>  
  
1.  <span data-ttu-id="18ca5-172">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="18ca5-173">フォームが表示されたら、ファイルのパスを入力でテストするファイル、`sourceFile`ボックス。</span><span class="sxs-lookup"><span data-stu-id="18ca5-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="18ca5-174">たとえば、テスト ファイルと仮定した場合は、Test.txt という名前を C:\Test.txt を入力します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="18ca5-175">2 つ目のテキスト ボックスには、アプリケーションでテキスト ファイル内で検索する語句を入力します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="18ca5-176">[`Start`] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18ca5-176">Click the `Start` button.</span></span> <span data-ttu-id="18ca5-177">`LinesCounted`ボタンがすぐに増分する操作を始める必要があります。</span><span class="sxs-lookup"><span data-stu-id="18ca5-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="18ca5-178">アプリケーションでは、処理が完了したら、「終了カウント」メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18ca5-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="18ca5-179">[キャンセル] ボタンをテストするには</span><span class="sxs-lookup"><span data-stu-id="18ca5-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="18ca5-180">F5 キーを押して、アプリケーションを起動し、前の手順に従って、ファイル名と検索語を入力します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="18ca5-181">選択したファイルが完了する前に、プロシージャをキャンセルする時間があることを確認するために十分であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18ca5-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="18ca5-182">クリックして、`Start`アプリケーションを起動するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18ca5-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="18ca5-183">[`Cancel`] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18ca5-183">Click the `Cancel` button.</span></span> <span data-ttu-id="18ca5-184">アプリケーションは、カウントをすぐに停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18ca5-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="18ca5-185">次の手順</span><span class="sxs-lookup"><span data-stu-id="18ca5-185">Next Steps</span></span>  
 <span data-ttu-id="18ca5-186">このアプリケーションには、基本的なエラー処理が含まれています。</span><span class="sxs-lookup"><span data-stu-id="18ca5-186">This application contains some basic error handling.</span></span> <span data-ttu-id="18ca5-187">空白の検索文字列を検出します。</span><span class="sxs-lookup"><span data-stu-id="18ca5-187">It detects blank search strings.</span></span> <span data-ttu-id="18ca5-188">単語やカウントできる行の最大数を超えた場合など、他のエラーを処理することによって行うと、このプログラムがより堅牢です。</span><span class="sxs-lookup"><span data-stu-id="18ca5-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ca5-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="18ca5-189">See Also</span></span>  
 <span data-ttu-id="18ca5-190">[スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="18ca5-190">[Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) </span></span>  
<span data-ttu-id="18ca5-191"> [チュートリアル: Visual Basic による簡単なマルチ スレッド コンポーネントの作成](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001) </span><span class="sxs-lookup"><span data-stu-id="18ca5-191"> [Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001) </span></span>  
<span data-ttu-id="18ca5-192"> [方法: イベント サブスクリプションとサブスクリプションの解除](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="18ca5-192"> [How to: Subscribe to and Unsubscribe from Events](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span></span>
