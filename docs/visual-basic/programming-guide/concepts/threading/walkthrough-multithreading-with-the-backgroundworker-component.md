---
title: "BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb0734b4bbf3f8bf5b27305754829f1a9f29f42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>チュートリアル: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド
このチュートリアルでは、テキスト ファイルで単語を検索する、マルチスレッドの Windows Forms アプリケーションを作成する方法について説明します。 具体的には、次のタスクについて説明します。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントによって呼び出すことができるメソッドを使用してクラスを定義する。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントによって生成されたイベントを処理する。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントを起動してメソッドを実行する。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントを停止する `Cancel` ボタンを実装する。  
  
### <a name="to-create-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  新しい Visual Basic Windows フォーム アプリケーション プロジェクトを開き、という名前のフォームを作成`Form1`です。  
  
2.  `Form1` に、2 つのボタンと 4 つのテキスト ボックスを追加します。  
  
3.  次の表のように、各オブジェクトに名前を付けます。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |1 つ目のボタン|`Name`, `Text`|Start, Start|  
    |2 つ目のボタン|`Name`, `Text`|Cancel, Cancel|  
    |1 つ目のテキスト ボックス|`Name`, `Text`|SourceFile, ""|  
    |2 つ目のテキスト ボックス|`Name`, `Text`|CompareString, ""|  
    |3 つ目のテキスト ボックス|`Name`, `Text`|WordsCounted, "0"|  
    |4 つ目のテキスト ボックス|`Name`, `Text`|LinesCounted, "0"|  
  
4.  各テキスト ボックスの横にラベルを追加します。 次の表のように、各ラベルの `Text` プロパティを設定します。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |1 つ目のラベル|`Text`|[ソース ファイル]|  
    |2 つ目のラベル|`Text`|Compare String|  
    |3 つ目のラベル|`Text`|Matching Words|  
    |4 つ目のラベル|`Text`|Lines Counted|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>BackgroundWorker コンポーネントを作成し、そのイベントをサブスクライブするには  
  
1.  **[ツールボックス]** の **[コンポーネント]** セクションから、<xref:System.ComponentModel.BackgroundWorker> コンポーネントをフォームに追加します。 追加したコンポーネントは、フォームのコンポーネント トレイに表示されます。  
  
2.  BackgroundWorker1 オブジェクトの次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>個別のスレッドで実行されるメソッドを定義するには  
  
1.  **[プロジェクト]** メニューの **[クラスの追加]** を選択して、プロジェクトにクラスを追加します。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
2.  テンプレート ウィンドウから **[クラス]** を選択し、名前 フィールドに「`Words.vb`」と入力します。  
  
3.  **[追加]**をクリックします。 `Words` クラスが表示されます。  
  
4.  `Words` クラスに次のコードを追加します。  
  
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
  
### <a name="to-handle-events-from-the-thread"></a>スレッドからイベントを処理するには  
  
-   メイン フォームに次のイベント ハンドラーを追加します。  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>WordCount メソッドを実行する新しいスレッドを起動して呼び出すには  
  
1.  プログラムに次のプロシージャを追加します。  
  
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
  
2.  フォーム上の `Start` ボタンから `StartThread` メソッドを呼び出します。  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>スレッドを停止するためのキャンセル ボタンを実装するには  
  
-   `Cancel` ボタンの `Click` イベント ハンドラーから、`StopThread` プロシージャを呼び出します。  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>テスト中  
 アプリケーションをテストして、正常に動作していることを確認できます。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  フォームが表示されたら、テストするファイルのファイル パスを `sourceFile` ボックスに入力します。 たとえば、テスト ファイルの名前が Test.txt の場合は、「C:\Test.txt」と入力します。  
  
3.  2 つ目のテキスト ボックスに、テキスト ファイル内で検索する単語または語句を入力します。  
  
4.  [`Start`] ボタンをクリックします。 `LinesCounted` ボタンがすぐにインクリメントし始めます。 処理が完了すると、「Finished Counting」というメッセージが表示されます。  
  
#### <a name="to-test-the-cancel-button"></a>キャンセル ボタンをテストするには  
  
1.  F5 キーを押してアプリケーションを起動し、前の手順で説明したように、ファイル名を入力して単語を検索します。 処理が完了する前にプロシージャをキャンセルできるだけの時間が必要なので、選択したファイルが十分なサイズであることを確認します。  
  
2.  `Start` ボタンをクリックしてアプリケーションを起動します。  
  
3.  [`Cancel`] ボタンをクリックします。 アプリケーションがすぐにカウントを停止します。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションには、基本的なエラー処理が含まれており、 このアプリケーションは空白の検索文字列を検出します。 その他のエラーを処理できるようにすれば、このプログラムの堅牢性をさらに高めることができます (カウントできる単語や行の最大数を超えた場合の処理を追加するなど)。  
  
## <a name="see-also"></a>関連項目  
 [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [チュートリアル: Visual Basic による簡単なマルチ スレッド コンポーネントの作成](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [方法: イベント サブスクリプションとサブスクリプションの解除](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
