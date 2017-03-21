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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3686eb230349876f6cfffd2ad94ed1f547779ab1
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a>チュートリアル: BackgroundWorker コンポーネント (Visual Basic) でのマルチ スレッド
このチュートリアルは、単語の出現回数をテキスト ファイルを検索するマルチ スレッドの Windows フォーム アプリケーションを作成する方法を示します。 これを示しています。  
  
-   呼び出すことができるメソッドを使用してクラスを定義する、<xref:System.ComponentModel.BackgroundWorker>コンポーネント</xref:System.ComponentModel.BackgroundWorker>。  
  
-   によって生成されるイベントを処理、<xref:System.ComponentModel.BackgroundWorker>コンポーネント</xref:System.ComponentModel.BackgroundWorker>。  
  
-   以降、<xref:System.ComponentModel.BackgroundWorker>メソッドを実行するコンポーネント</xref:System.ComponentModel.BackgroundWorker>。  
  
-   実装する、`Cancel`停止ボタン、<xref:System.ComponentModel.BackgroundWorker>コンポーネント</xref:System.ComponentModel.BackgroundWorker>。  
  
### <a name="to-create-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  新しい Visual Basic Windows フォーム アプリケーション プロジェクトを開き、という名前のフォームを作成`Form1`します。  
  
2.  2 つのボタンと&4; つのテキスト ボックスに追加`Form1`します。  
  
3.  次の表に示すように、オブジェクトの名前を付けます。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |最初のボタン|`Name`, `Text`|スタート、開始|  
    |2 番目のボタン|`Name`, `Text`|[キャンセル]、[キャンセル]|  
    |最初のテキスト ボックス|`Name`, `Text`|SourceFile、""|  
    |2 つ目のテキスト ボックス|`Name`, `Text`|通常、""|  
    |3 番目のテキスト ボックス|`Name`, `Text`|WordsCounted、「0」|  
    |4 番目のテキスト ボックス|`Name`, `Text`|LinesCounted、「0」|  
  
4.  各テキスト ボックスの横にあるラベルを追加します。 設定、`Text`次の表に示すように、各ラベルのプロパティです。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |最初のラベル|`Text`|[ソース ファイル]|  
    |2 番目のラベル|`Text`|文字列を比較します。|  
    |3 番目のラベル|`Text`|単語に一致します。|  
    |4 番目のラベル|`Text`|行のカウント|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a>BackgroundWorker コンポーネントを作成し、そのイベントをサブスクライブするには  
  
1.  追加、<xref:System.ComponentModel.BackgroundWorker>コンポーネントから、**コンポーネント**のセクションで、**ツールボックス**をフォームにします</xref:System.ComponentModel.BackgroundWorker>。 フォームのコンポーネント トレイに表示されます。  
  
2.  BackgroundWorker1 オブジェクトの次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>別のスレッドで実行されるメソッドを定義するには  
  
1.  **プロジェクト**] メニューの [選択**クラスの追加**クラスをプロジェクトに追加します。 **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
2.  選択**クラス**テンプレート ウィンドウから入力`Words.vb`名 フィールドにします。  
  
3.  **[追加]**をクリックします。 `Words`クラスが表示されます。  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>WordCount メソッドを実行して開始し、新しいスレッドを呼び出します  
  
1.  プログラムを次の手順を追加します。  
  
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
  
2.  呼び出す、`StartThread`メソッドから、`Start`フォーム上のボタン。  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>[キャンセル] ボタンを実装するには、スレッドを停止します。  
  
-   呼び出す、`StopThread`プロシージャから、`Click`のイベント ハンドラー、 `Cancel`  ボタンをクリックします。  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a>テスト中  
 正常に動作を確認するアプリケーションをテストできます。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  フォームが表示されたら、ファイルのパスを入力でテストするファイル、`sourceFile`ボックス。 たとえば、テスト ファイルと仮定した場合は、Test.txt という名前を C:\Test.txt を入力します。  
  
3.  2 つ目のテキスト ボックスには、アプリケーションでテキスト ファイル内で検索する語句を入力します。  
  
4.  [`Start`] ボタンをクリックします。 `LinesCounted`ボタンがすぐに増分する操作を始める必要があります。 アプリケーションでは、処理が完了したら、「終了カウント」メッセージが表示されます。  
  
#### <a name="to-test-the-cancel-button"></a>[キャンセル] ボタンをテストするには  
  
1.  F5 キーを押して、アプリケーションを起動し、前の手順に従って、ファイル名と検索語を入力します。 選択したファイルが完了する前に、プロシージャをキャンセルする時間があることを確認するために十分であることを確認してください。  
  
2.  クリックして、`Start`アプリケーションを起動するボタンをクリックします。  
  
3.  [`Cancel`] ボタンをクリックします。 アプリケーションは、カウントをすぐに停止する必要があります。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションには、基本的なエラー処理が含まれています。 空白の検索文字列を検出します。 単語やカウントできる行の最大数を超えた場合など、他のエラーを処理することによって行うと、このプログラムがより堅牢です。  
  
## <a name="see-also"></a>関連項目  
 [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [チュートリアル: Visual Basic による簡単なマルチ スレッド コンポーネントの作成](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)   
 [方法: イベント サブスクリプションとサブスクリプションの解除](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
