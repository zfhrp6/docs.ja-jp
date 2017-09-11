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
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="289c3-102">チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (C#)</span><span class="sxs-lookup"><span data-stu-id="289c3-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="289c3-103">このチュートリアルでは、テキスト ファイルで単語を検索する、マルチスレッドの Windows Forms アプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="289c3-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="289c3-104">具体的には、次のタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="289c3-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="289c3-105"><xref:System.ComponentModel.BackgroundWorker> コンポーネントによって呼び出すことができるメソッドを使用してクラスを定義する。</span><span class="sxs-lookup"><span data-stu-id="289c3-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="289c3-106"><xref:System.ComponentModel.BackgroundWorker> コンポーネントによって生成されたイベントを処理する。</span><span class="sxs-lookup"><span data-stu-id="289c3-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="289c3-107"><xref:System.ComponentModel.BackgroundWorker> コンポーネントを起動してメソッドを実行する。</span><span class="sxs-lookup"><span data-stu-id="289c3-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="289c3-108"><xref:System.ComponentModel.BackgroundWorker> コンポーネントを停止する `Cancel` ボタンを実装する。</span><span class="sxs-lookup"><span data-stu-id="289c3-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="289c3-109">ユーザー インターフェイスを作成するには</span><span class="sxs-lookup"><span data-stu-id="289c3-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="289c3-110">新しい C# Windows フォーム アプリケーション プロジェクトを開き、`Form1` という名前のフォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="289c3-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="289c3-111">`Form1` に、2 つのボタンと 4 つのテキスト ボックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="289c3-112">次の表のように、各オブジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="289c3-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="289c3-113">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="289c3-113">Object</span></span>|<span data-ttu-id="289c3-114">プロパティ</span><span class="sxs-lookup"><span data-stu-id="289c3-114">Property</span></span>|<span data-ttu-id="289c3-115">設定</span><span class="sxs-lookup"><span data-stu-id="289c3-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="289c3-116">1 つ目のボタン</span><span class="sxs-lookup"><span data-stu-id="289c3-116">First button</span></span>|<span data-ttu-id="289c3-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="289c3-117">`Name`, `Text`</span></span>|<span data-ttu-id="289c3-118">Start, Start</span><span class="sxs-lookup"><span data-stu-id="289c3-118">Start, Start</span></span>|  
    |<span data-ttu-id="289c3-119">2 つ目のボタン</span><span class="sxs-lookup"><span data-stu-id="289c3-119">Second button</span></span>|<span data-ttu-id="289c3-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="289c3-120">`Name`, `Text`</span></span>|<span data-ttu-id="289c3-121">Cancel, Cancel</span><span class="sxs-lookup"><span data-stu-id="289c3-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="289c3-122">1 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="289c3-122">First text box</span></span>|<span data-ttu-id="289c3-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="289c3-123">`Name`, `Text`</span></span>|<span data-ttu-id="289c3-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="289c3-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="289c3-125">2 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="289c3-125">Second text box</span></span>|<span data-ttu-id="289c3-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="289c3-126">`Name`, `Text`</span></span>|<span data-ttu-id="289c3-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="289c3-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="289c3-128">3 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="289c3-128">Third text box</span></span>|<span data-ttu-id="289c3-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="289c3-129">`Name`, `Text`</span></span>|<span data-ttu-id="289c3-130">WordsCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="289c3-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="289c3-131">4 つ目のテキスト ボックス</span><span class="sxs-lookup"><span data-stu-id="289c3-131">Fourth text box</span></span>|<span data-ttu-id="289c3-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="289c3-132">`Name`, `Text`</span></span>|<span data-ttu-id="289c3-133">LinesCounted, "0"</span><span class="sxs-lookup"><span data-stu-id="289c3-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="289c3-134">各テキスト ボックスの横にラベルを追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-134">Add a label next to each text box.</span></span> <span data-ttu-id="289c3-135">次の表のように、各ラベルの `Text` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="289c3-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="289c3-136">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="289c3-136">Object</span></span>|<span data-ttu-id="289c3-137">プロパティ</span><span class="sxs-lookup"><span data-stu-id="289c3-137">Property</span></span>|<span data-ttu-id="289c3-138">設定</span><span class="sxs-lookup"><span data-stu-id="289c3-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="289c3-139">1 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="289c3-139">First label</span></span>|`Text`|<span data-ttu-id="289c3-140">[ソース ファイル]</span><span class="sxs-lookup"><span data-stu-id="289c3-140">Source File</span></span>|  
    |<span data-ttu-id="289c3-141">2 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="289c3-141">Second label</span></span>|`Text`|<span data-ttu-id="289c3-142">Compare String</span><span class="sxs-lookup"><span data-stu-id="289c3-142">Compare String</span></span>|  
    |<span data-ttu-id="289c3-143">3 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="289c3-143">Third label</span></span>|`Text`|<span data-ttu-id="289c3-144">Matching Words</span><span class="sxs-lookup"><span data-stu-id="289c3-144">Matching Words</span></span>|  
    |<span data-ttu-id="289c3-145">4 つ目のラベル</span><span class="sxs-lookup"><span data-stu-id="289c3-145">Fourth label</span></span>|`Text`|<span data-ttu-id="289c3-146">Lines Counted</span><span class="sxs-lookup"><span data-stu-id="289c3-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="289c3-147">BackgroundWorker コンポーネントを作成し、そのイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="289c3-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="289c3-148">**[ツールボックス]** の **[コンポーネント]** セクションから、<xref:System.ComponentModel.BackgroundWorker> コンポーネントをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="289c3-149">追加したコンポーネントは、フォームのコンポーネント トレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="289c3-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="289c3-150">BackgroundWorker1 オブジェクトについて、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="289c3-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="289c3-151">プロパティ</span><span class="sxs-lookup"><span data-stu-id="289c3-151">Property</span></span>|<span data-ttu-id="289c3-152">設定</span><span class="sxs-lookup"><span data-stu-id="289c3-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="289c3-153">True</span><span class="sxs-lookup"><span data-stu-id="289c3-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="289c3-154">True</span><span class="sxs-lookup"><span data-stu-id="289c3-154">True</span></span>|  
  
3.  <span data-ttu-id="289c3-155">BackgroundWorker1 オブジェクトのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="289c3-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="289c3-156">**[プロパティ]** ウィンドウの上部で、**[イベント]** アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="289c3-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="289c3-157">`RunWorkerCompleted` イベントをダブルクリックして、イベント ハンドラー メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="289c3-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="289c3-158">`ProgressChanged` イベントと `DoWork` イベントについても、同じ操作を行いいます。</span><span class="sxs-lookup"><span data-stu-id="289c3-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="289c3-159">個別のスレッドで実行されるメソッドを定義するには</span><span class="sxs-lookup"><span data-stu-id="289c3-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="289c3-160">**[プロジェクト]** メニューの **[クラスの追加]** を選択して、プロジェクトにクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="289c3-161">**[新しい項目の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="289c3-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="289c3-162">テンプレート ウィンドウから **[クラス]** を選択し、名前フィールドに「`Words.cs`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="289c3-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="289c3-163">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="289c3-163">Click **Add**.</span></span> <span data-ttu-id="289c3-164">`Words` クラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="289c3-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="289c3-165">`Words` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-165">Add the following code to the `Words` class:</span></span>  
  
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
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="289c3-166">スレッドからイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="289c3-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="289c3-167">メイン フォームに次のイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-167">Add the following event handlers to your main form:</span></span>  
  
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
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="289c3-168">WordCount メソッドを実行する新しいスレッドを起動して呼び出すには</span><span class="sxs-lookup"><span data-stu-id="289c3-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="289c3-169">プログラムに次のプロシージャを追加します。</span><span class="sxs-lookup"><span data-stu-id="289c3-169">Add the following procedures to your program:</span></span>  
  
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
  
2.  <span data-ttu-id="289c3-170">フォーム上の `Start` ボタンから `StartThread` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="289c3-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="289c3-171">スレッドを停止するためのキャンセル ボタンを実装するには</span><span class="sxs-lookup"><span data-stu-id="289c3-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="289c3-172">`Cancel` ボタンの `Click` イベント ハンドラーから、`StopThread` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="289c3-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="289c3-173">テスト中</span><span class="sxs-lookup"><span data-stu-id="289c3-173">Testing</span></span>  
 <span data-ttu-id="289c3-174">アプリケーションをテストして、正常に動作していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="289c3-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="289c3-175">アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="289c3-175">To test the application</span></span>  
  
1.  <span data-ttu-id="289c3-176">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="289c3-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="289c3-177">フォームが表示されたら、テストするファイルのファイル パスを `sourceFile` ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="289c3-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="289c3-178">たとえば、テスト ファイルの名前が Test.txt の場合は、「C:\Test.txt」と入力します。</span><span class="sxs-lookup"><span data-stu-id="289c3-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="289c3-179">2 つ目のテキスト ボックスに、テキスト ファイル内で検索する単語または語句を入力します。</span><span class="sxs-lookup"><span data-stu-id="289c3-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="289c3-180">[`Start`] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="289c3-180">Click the `Start` button.</span></span> <span data-ttu-id="289c3-181">`LinesCounted` ボタンがすぐにインクリメントし始めます。</span><span class="sxs-lookup"><span data-stu-id="289c3-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="289c3-182">処理が完了すると、「Finished Counting」というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="289c3-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="289c3-183">キャンセル ボタンをテストするには</span><span class="sxs-lookup"><span data-stu-id="289c3-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="289c3-184">F5 キーを押してアプリケーションを起動し、前の手順で説明したように、ファイル名を入力して単語を検索します。</span><span class="sxs-lookup"><span data-stu-id="289c3-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="289c3-185">処理が完了する前にプロシージャをキャンセルできるだけの時間が必要なので、選択したファイルが十分なサイズであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="289c3-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="289c3-186">`Start` ボタンをクリックしてアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="289c3-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="289c3-187">[`Cancel`] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="289c3-187">Click the `Cancel` button.</span></span> <span data-ttu-id="289c3-188">アプリケーションがすぐにカウントを停止します。</span><span class="sxs-lookup"><span data-stu-id="289c3-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="289c3-189">次の手順</span><span class="sxs-lookup"><span data-stu-id="289c3-189">Next Steps</span></span>  
 <span data-ttu-id="289c3-190">このアプリケーションには、基本的なエラー処理が含まれており、</span><span class="sxs-lookup"><span data-stu-id="289c3-190">This application contains some basic error handling.</span></span> <span data-ttu-id="289c3-191">このアプリケーションは空白の検索文字列を検出します。</span><span class="sxs-lookup"><span data-stu-id="289c3-191">It detects blank search strings.</span></span> <span data-ttu-id="289c3-192">その他のエラーを処理できるようにすれば、このプログラムの堅牢性をさらに高めることができます (カウントできる単語や行の最大数を超えた場合の処理を追加するなど)。</span><span class="sxs-lookup"><span data-stu-id="289c3-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="289c3-193">関連項目</span><span class="sxs-lookup"><span data-stu-id="289c3-193">See Also</span></span>  
 <span data-ttu-id="289c3-194">[スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) </span><span class="sxs-lookup"><span data-stu-id="289c3-194">[Threading (C#)](../../../../csharp/programming-guide/concepts/threading/index.md) </span></span>  
 [<span data-ttu-id="289c3-195">方法: イベント サブスクリプションとサブスクリプションの解除</span><span class="sxs-lookup"><span data-stu-id="289c3-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)

