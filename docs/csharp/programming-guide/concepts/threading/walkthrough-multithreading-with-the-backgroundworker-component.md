---
title: "チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 541a1ec788c337eea9965b8a46155e5c6606ea2f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a>チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (C#)
このチュートリアルでは、テキスト ファイルで単語を検索する、マルチスレッドの Windows Forms アプリケーションを作成する方法について説明します。 具体的には、次のタスクについて説明します。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントによって呼び出すことができるメソッドを使用してクラスを定義する。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントによって生成されたイベントを処理する。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントを起動してメソッドを実行する。  
  
-   <xref:System.ComponentModel.BackgroundWorker> コンポーネントを停止する `Cancel` ボタンを実装する。  
  
### <a name="to-create-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  新しい C# Windows フォーム アプリケーション プロジェクトを開き、`Form1` という名前のフォームを作成します。  
  
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
  
2.  BackgroundWorker1 オブジェクトについて、次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|True|  
    |`WorkerSupportsCancellation`|True|  
  
3.  BackgroundWorker1 オブジェクトのイベントをサブスクライブします。 **[プロパティ]** ウィンドウの上部で、**[イベント]** アイコンをクリックします。 `RunWorkerCompleted` イベントをダブルクリックして、イベント ハンドラー メソッドを作成します。 `ProgressChanged` イベントと `DoWork` イベントについても、同じ操作を行いいます。  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a>個別のスレッドで実行されるメソッドを定義するには  
  
1.  **[プロジェクト]** メニューの **[クラスの追加]** を選択して、プロジェクトにクラスを追加します。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
2.  テンプレート ウィンドウから **[クラス]** を選択し、名前フィールドに「`Words.cs`」と入力します。  
  
3.  **[追加]**をクリックします。 `Words` クラスが表示されます。  
  
4.  `Words` クラスに次のコードを追加します。  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a>スレッドからイベントを処理するには  
  
-   メイン フォームに次のイベント ハンドラーを追加します。  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a>WordCount メソッドを実行する新しいスレッドを起動して呼び出すには  
  
1.  プログラムに次のプロシージャを追加します。  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  フォーム上の `Start` ボタンから `StartThread` メソッドを呼び出します。  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a>スレッドを停止するためのキャンセル ボタンを実装するには  
  
    -   `Cancel` ボタンの `Click` イベント ハンドラーから、`StopThread` プロシージャを呼び出します。  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
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
 [スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)   
 [方法: イベント サブスクリプションとサブスクリプションの解除](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

