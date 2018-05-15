---
title: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド
ms.date: 07/20/2015
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
ms.openlocfilehash: 07700aa526866729f1ba1a8d846f22ce333c356d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="83eb4-102">チュートリアル: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド</span><span class="sxs-lookup"><span data-stu-id="83eb4-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="83eb4-103">このチュートリアルでは、テキスト ファイルで単語を検索する、マルチスレッドの Windows Forms アプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="83eb4-104">具体的には、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="83eb4-105"><xref:System.ComponentModel.BackgroundWorker> コンポーネントによって呼び出すことができるメソッドを使用してクラスを定義する。</span><span class="sxs-lookup"><span data-stu-id="83eb4-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="83eb4-106"><xref:System.ComponentModel.BackgroundWorker> コンポーネントによって生成されたイベントを処理する。</span><span class="sxs-lookup"><span data-stu-id="83eb4-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="83eb4-107"><xref:System.ComponentModel.BackgroundWorker> コンポーネントを起動してメソッドを実行する。</span><span class="sxs-lookup"><span data-stu-id="83eb4-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="83eb4-108"><xref:System.ComponentModel.BackgroundWorker> コンポーネントを停止する `Cancel` ボタンを実装する。</span><span class="sxs-lookup"><span data-stu-id="83eb4-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="83eb4-109">ユーザー インターフェイスを作成するには</span><span class="sxs-lookup"><span data-stu-id="83eb4-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="83eb4-110">新しい Visual Basic Windows フォーム アプリケーション プロジェクトを開き、という名前のフォームを作成`Form1`です。</span><span class="sxs-lookup"><span data-stu-id="83eb4-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="83eb4-111">`Form1` に、2 つのボタンと 4 つのテキスト ボックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="83eb4-112">次の表のように、各オブジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="83eb4-113">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="83eb4-113">Object</span></span>|<span data-ttu-id="83eb4-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83eb4-114">Property</span></span>|<span data-ttu-id="83eb4-115">設定</span><span class="sxs-lookup"><span data-stu-id="83eb4-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="83eb4-116">1 つ目のボタン</span><span class="sxs-lookup"><span data-stu-id="83eb4-116">First button</span></span>|<span data-ttu-id="83eb4-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="83eb4-117">`Name`, `Text`</span></span>|<span data-ttu-id="83eb4-118">Start, Start</span><span class="sxs-lookup"><span data-stu-id="83eb4-118">Start, Start</span></span>|  
    |<span data-ttu-id="83eb4-119">2 つ目のボタン</span><span class="sxs-lookup"><span data-stu-id="83eb4-119">Second button</span></span>|<span data-ttu-id="83eb4-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="83eb4-120">`Name`, `Text`</span></span>|<span data-ttu-id="83eb4-121">Cancel, Cancel</span><span class="sxs-lookup"><span data-stu-id="83eb4-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="83eb4-122">1 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="83eb4-122">First text box</span></span>|<span data-ttu-id="83eb4-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="83eb4-123">`Name`, `Text`</span></span>|<span data-ttu-id="83eb4-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="83eb4-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="83eb4-125">2 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="83eb4-125">Second text box</span></span>|<span data-ttu-id="83eb4-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="83eb4-126">`Name`, `Text`</span></span>|<span data-ttu-id="83eb4-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="83eb4-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="83eb4-128">3 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="83eb4-128">Third text box</span></span>|<span data-ttu-id="83eb4-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="83eb4-129">`Name`, `Text`</span></span>|<span data-ttu-id="83eb4-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="83eb4-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="83eb4-131">4 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="83eb4-131">Fourth text box</span></span>|<span data-ttu-id="83eb4-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="83eb4-132">`Name`, `Text`</span></span>|<span data-ttu-id="83eb4-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="83eb4-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="83eb4-134">各テキスト ボックスの横にラベルを追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-134">Add a label next to each text box.</span></span> <span data-ttu-id="83eb4-135">次の表のように、各ラベルの `Text` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="83eb4-136">Object</span><span class="sxs-lookup"><span data-stu-id="83eb4-136">Object</span></span>|<span data-ttu-id="83eb4-137">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83eb4-137">Property</span></span>|<span data-ttu-id="83eb4-138">設定</span><span class="sxs-lookup"><span data-stu-id="83eb4-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="83eb4-139">1 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="83eb4-139">First label</span></span>|`Text`|<span data-ttu-id="83eb4-140">[ソース ファイル]</span><span class="sxs-lookup"><span data-stu-id="83eb4-140">Source File</span></span>|  
    |<span data-ttu-id="83eb4-141">2 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="83eb4-141">Second label</span></span>|`Text`|<span data-ttu-id="83eb4-142">Compare String</span><span class="sxs-lookup"><span data-stu-id="83eb4-142">Compare String</span></span>|  
    |<span data-ttu-id="83eb4-143">3 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="83eb4-143">Third label</span></span>|`Text`|<span data-ttu-id="83eb4-144">Matching Words</span><span class="sxs-lookup"><span data-stu-id="83eb4-144">Matching Words</span></span>|  
    |<span data-ttu-id="83eb4-145">4 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="83eb4-145">Fourth label</span></span>|`Text`|<span data-ttu-id="83eb4-146">Lines Counted</span><span class="sxs-lookup"><span data-stu-id="83eb4-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="83eb4-147">BackgroundWorker コンポーネントを作成し、そのイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="83eb4-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="83eb4-148">**[ツールボックス]** の **[コンポーネント]** セクションから、<xref:System.ComponentModel.BackgroundWorker> コンポーネントをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="83eb4-149">追加したコンポーネントは、フォームのコンポーネント トレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="83eb4-150">BackgroundWorker1 オブジェクトの次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="83eb4-151">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83eb4-151">Property</span></span>|<span data-ttu-id="83eb4-152">設定</span><span class="sxs-lookup"><span data-stu-id="83eb4-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="83eb4-153">True</span><span class="sxs-lookup"><span data-stu-id="83eb4-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="83eb4-154">True</span><span class="sxs-lookup"><span data-stu-id="83eb4-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="83eb4-155">個別のスレッドで実行されるメソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="83eb4-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="83eb4-156">**[プロジェクト]** メニューの **[クラスの追加]** を選択して、プロジェクトにクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="83eb4-157">**[新しい項目の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="83eb4-158">テンプレート ウィンドウから **[クラス]** を選択し、名前 フィールドに「`Words.vb`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="83eb4-159">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="83eb4-159">Click **Add**.</span></span> <span data-ttu-id="83eb4-160">`Words` クラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="83eb4-161">`Words` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-161">Add the following code to the `Words` class:</span></span>  
  
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
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="83eb4-162">スレッドからイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="83eb4-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="83eb4-163">メイン フォームに次のイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-163">Add the following event handlers to your main form:</span></span>  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="83eb4-164">WordCount メソッドを実行する新しいスレッドを起動して呼び出すには</span><span class="sxs-lookup"><span data-stu-id="83eb4-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="83eb4-165">プログラムに次のプロシージャを追加します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-165">Add the following procedures to your program:</span></span>  
  
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
  
2.  <span data-ttu-id="83eb4-166">フォーム上の `Start` ボタンから `StartThread` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="83eb4-167">スレッドを停止するためのキャンセル ボタンを実装するには</span><span class="sxs-lookup"><span data-stu-id="83eb4-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="83eb4-168">`Cancel` ボタンの `Click` イベント ハンドラーから、`StopThread` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="83eb4-169">テスト中</span><span class="sxs-lookup"><span data-stu-id="83eb4-169">Testing</span></span>  
 <span data-ttu-id="83eb4-170">アプリケーションをテストして、正常に動作していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="83eb4-171">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="83eb4-171">To test the application</span></span>  
  
1.  <span data-ttu-id="83eb4-172">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="83eb4-173">フォームが表示されたら、テストするファイルのファイル パスを `sourceFile` ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="83eb4-174">たとえば、テスト ファイルの名前が Test.txt の場合は、「C:\Test.txt」と入力します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="83eb4-175">2 つ目のテキスト ボックスに、テキスト ファイル内で検索する単語または語句を入力します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="83eb4-176">[`Start`] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83eb4-176">Click the `Start` button.</span></span> <span data-ttu-id="83eb4-177">`LinesCounted` ボタンがすぐにインクリメントし始めます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="83eb4-178">処理が完了すると、「Finished Counting」というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83eb4-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="83eb4-179">キャンセル ボタンをテストするには</span><span class="sxs-lookup"><span data-stu-id="83eb4-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="83eb4-180">F5 キーを押してアプリケーションを起動し、前の手順で説明したように、ファイル名を入力して単語を検索します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="83eb4-181">処理が完了する前にプロシージャをキャンセルできるだけの時間が必要なので、選択したファイルが十分なサイズであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="83eb4-182">`Start` ボタンをクリックしてアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="83eb4-183">[`Cancel`] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="83eb4-183">Click the `Cancel` button.</span></span> <span data-ttu-id="83eb4-184">アプリケーションがすぐにカウントを停止します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="83eb4-185">次の手順</span><span class="sxs-lookup"><span data-stu-id="83eb4-185">Next Steps</span></span>  
 <span data-ttu-id="83eb4-186">このアプリケーションには、基本的なエラー処理が含まれており、</span><span class="sxs-lookup"><span data-stu-id="83eb4-186">This application contains some basic error handling.</span></span> <span data-ttu-id="83eb4-187">このアプリケーションは空白の検索文字列を検出します。</span><span class="sxs-lookup"><span data-stu-id="83eb4-187">It detects blank search strings.</span></span> <span data-ttu-id="83eb4-188">その他のエラーを処理できるようにすれば、このプログラムの堅牢性をさらに高めることができます (カウントできる単語や行の最大数を超えた場合の処理を追加するなど)。</span><span class="sxs-lookup"><span data-stu-id="83eb4-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83eb4-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="83eb4-189">See Also</span></span>  
 [<span data-ttu-id="83eb4-190">スレッド処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83eb4-190">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="83eb4-191">チュートリアル: Visual Basic による簡単なマルチ スレッド コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="83eb4-191">Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic</span></span>](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [<span data-ttu-id="83eb4-192">方法: イベント サブスクリプションとサブスクリプションの解除</span><span class="sxs-lookup"><span data-stu-id="83eb4-192">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
