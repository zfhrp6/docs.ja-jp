---
title: "Async で Web にアクセスして、Await (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
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
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)
プログラムを作成できます非同期より簡単かつ直感的にで導入された機能を使用して[!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)]します。 同期コードに似た非同期コードを記述し、通常の非同期コードが必要とする難しいコールバック関数や継続の処理をコンパイラに任せます。  
  
 非同期機能の詳細については、次を参照してください。 [Async と Await (Visual Basic) を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)します。  
  
 このチュートリアルは、Web サイトの一覧でのバイト数の合計を計算する同期 Windows Presentation Foundation (WPF) アプリケーションから開始します。 その後、新しい機能を使用して、アプリケーションを非同期ソリューションに変換します。  
  
 アプリケーションをビルドしたくない場合は、ダウンロード"Async サンプル: Web のチュートリアル (c# および Visual Basic) にアクセスする"から[デベロッパー サンプル コード集](http://go.microsoft.com/fwlink/?LinkId=255191)します。  
  
 このチュートリアルでは、次のタスクを行います。  
  
-   [WPF アプリケーションを作成するには](#CreateWPFApp)  
  
-   [単純な WPF MainWindow をデザインします。](#MainWindow)  
  
-   [参照を追加するには](#AddRef)  
  
-   [必要な Imports ステートメントを追加するには](#ImportsState)  
  
-   [同期アプリケーションを作成するには](#synchronous)  
  
-   [同期ソリューションをテストするには](#testSynch)  
  
-   [GetURLContents を非同期メソッドに変換するには](#GetURLContents)  
  
-   [SumPageSizes を非同期メソッドに変換するには](#SumPageSizes)  
  
-   [StartButton_Click を非同期メソッドに変換するには](#startButton)  
  
-   [非同期のソリューションをテストするには](#testAsynch)  
  
-   [GetURLContentsAsync メソッドを .NET Framework メソッドに置き換えます](#GetURLContentsAsync)  
  
-   [使用例](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2012 またはそれ以降は、お使いのコンピューターにインストールする必要があります。 詳細については、次を参照してください。、 [Microsoft web サイト](http://go.microsoft.com/fwlink/?LinkId=235233)します。  
  
###  <a name="CreateWPFApp"></a>WPF アプリケーションを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **インストールされたテンプレート**] ウィンドウでは、Visual Basic を選択し、[ **WPF アプリケーション**プロジェクトの種類の一覧からです。  
  
4.  **名**テキスト ボックスに、入力`AsyncExampleWPF`を選択し、 **OK**  ボタンをクリックします。  
  
     新しいプロジェクトに表示されます**ソリューション エクスプ ローラー**します。  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a>単純な WPF MainWindow をデザインします。  
  
1.  Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。  
  
2.  場合、**ツールボックス**ウィンドウが表示されている、開かれている、**ビュー** ] メニューの [クリックして**ツールボックス**します。  
  
3.  追加、**ボタン**コントロールと** テキスト ボックス**に制御を**MainWindow**ウィンドウです。  
  
4.  強調表示、 ** テキスト ボックス**コントロールと、**プロパティ**ウィンドウでは、次の値を設定します。  
  
    -   設定、**名**プロパティを`resultsTextBox`します。  
  
    -   設定、**高さ**250 プロパティです。  
  
    -   設定、**幅**500 プロパティです。  
  
    -   **テキスト**タブで、グローバル Monospace Lucida コンソールなどの等幅フォントを指定します。  
  
5.  強調表示、**ボタン**コントロールと、**プロパティ**ウィンドウでは、次の値を設定します。  
  
    -   設定、**名**プロパティを`startButton`します。  
  
    -   値を変更、**コンテンツ**プロパティから**ボタン**に**開始**します。  
  
6.  両方ともに表示されるように、テキスト ボックスとボタンを位置、 **MainWindow**ウィンドウです。  
  
     WPF XAML デザイナーの詳細については、次を参照してください。 [XAML デザイナーを使用して UI を作成する](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)です。  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a>参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**プロジェクトの名前を強調表示します。  
  
2.  メニュー バー**プロジェクト**、**参照の追加**します。  
  
     **参照マネージャー**  ダイアログ ボックスが表示されます。  
  
3.  ダイアログ ボックスの上部にあるプロジェクトが .NET Framework 4.5 以降を対象としていることを確認します。  
  
4.  **アセンブリ**領域で、選択**Framework**が選択されていない場合。  
  
5.  名前の一覧で、選択、 **System.Net.Http**チェック ボックスをオンします。  
  
6.  選択、 **OK**  ダイアログ ボックスを閉じます。  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a>必要な Imports ステートメントを追加するには  
  
1.  **ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**します。  
  
2.  次の追加`Imports`存在していない場合は、コード ファイルの上部にあるステートメントです。  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a>同期アプリケーションを作成するには  
  
1.  デザイン ウィンドウで、MainWindow.xaml をダブルクリック、**開始**を作成するボタン、 `startButton_Click` MainWindow.xaml.vb 内のイベント ハンドラーです。  
  
2.  MainWindow.xaml.vb の本文に次のコードをコピー `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     このコードは、`SumPageSizes` アプリケーションを実行するメソッドを呼び出し、`startButton_Click` に制御が戻るとメッセージを表示します。  
  
3.  同期ソリューションのコードには、次の&4; つのメソッドが含まれています。  
  
    -   `SumPageSizes` は、`SetUpURLList` から Web ページ URL のリストを取得し、`GetURLContents` と `DisplayResults` を呼び出して各 URL を処理します。  
  
    -   `SetUpURLList` は、Web アドレスのリストを作成して返します。  
  
    -   `GetURLContents` は、各 Web サイトのコンテンツをダウンロードし、バイト配列としてそのコンテンツを返します。  
  
    -   `DisplayResults` は、各 URL のバイト配列内のバイト数を表示します。  
  
     次の&4; つのメソッドをコピーして貼り付けて下に、 `startButton_Click` MainWindow.xaml.vb 内のイベント ハンドラー。  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
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
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
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
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a>同期ソリューションをテストするには  
  
1.  F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。  
  
     次の一覧のような出力が表示されます。  
  
    ```  
  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
  
    ```  
  
     カウントの表示には数秒かかる点に注意してください。 その間、要求されたリソースのダウンロードが完了するまで UI スレッドがブロックされます。 その結果、移動できない場合を最大化、最小化、またはを選択した後、表示 ウィンドウを閉じることも、**開始** ボタンをクリックします。 バイト カウントの表示が開始するまでは、これらの操作を実行しても失敗します。 Web サイトが応答していない場合、どのサイトに問題があるのかを示す情報は表示されません。 待つのをやめて、プログラムを閉じることさえ難しい状態になります。  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a>GetURLContents を非同期メソッドに変換するには  
  
1.  開始する最適な場所が、同期ソリューションを非同期のソリューションに変換する`GetURLContents`ためへの呼び出し、<xref:System.Net.HttpWebRequest>メソッド<xref:System.Net.HttpWebRequest.GetResponse%2A>にされ、<xref:System.IO.Stream>メソッド<xref:System.IO.Stream.CopyTo%2A>アプリケーションが web にアクセスするには</xref:System.IO.Stream.CopyTo%2A></xref:System.IO.Stream></xref:System.Net.HttpWebRequest.GetResponse%2A></xref:System.Net.HttpWebRequest>。 .NET Framework には両方のメソッドの非同期バージョンが用意されているため、変換は簡単です。  
  
     使用される方法の詳細については`GetURLContents`、 <xref:System.Net.WebRequest>.</xref:System.Net.WebRequest>を参照してください。  
  
    > [!NOTE]
    >  このチュートリアルの手順に従っていると、いくつかのコンパイラ エラーが表示されます。 これらのエラーは無視することで、チュートリアルを続行できます。  
  
     3 行目に呼び出されるメソッドを変更する`GetURLContents`から`GetResponse`、非同期タスク ベース<xref:System.Net.WebRequest.GetResponseAsync%2A>メソッド</xref:System.Net.WebRequest.GetResponseAsync%2A>。  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync`<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601>を返します ここで、*タスク戻り変数*、 `TResult`、型を持つ<xref:System.Net.WebResponse>.</xref:System.Net.WebResponse> このタスクは、要求されたデータのダウンロードが完了し、タスクが最後まで実行された後に、実際の `WebResponse` オブジェクトを生成するという約束です。  
  
     取得する、`WebResponse`タスクから値を適用、 [Await](../../../../visual-basic/language-reference/operators/await-operator.md)演算子への呼び出しを`GetResponseAsync`次のコードを示します。  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
     `Await`演算子は、現在のメソッドの実行を中断`GetURLContents`待機中のタスクが完了するまで、します。 その間、現在のメソッドの呼び出し元に制御が戻されます。 この例では、現在のメソッドが `GetURLContents` で、呼び出し元が `SumPageSizes` です。 タスクが完了すると、約束されていた `WebResponse` オブジェクトが完了したタスクの値として生成され、変数 `response` に割り当てられます。  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
     `webReq.GetResponseAsync` への呼び出しによって、`Task(Of WebResponse)` または `Task<WebResponse>` が返されます。 `Await`を取得するタスクに演算子を適用、`WebResponse`値。  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  追加したので、`Await`前の手順で演算子は、コンパイラ エラーが発生します。 マークされたメソッドでのみ使用できます、演算子、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾子です。 `CopyTo` への呼び出しを `CopyToAsync` への呼び出しに置き換える変換手順を繰り返す間は、エラーを無視してください。  
  
    -   <xref:System.IO.Stream.CopyToAsync%2A>。</xref:System.IO.Stream.CopyToAsync%2A>ために呼び出されるメソッドの名前を変更します。  
  
    -   `CopyTo` または `CopyToAsync` メソッドは、その引数 `content` にバイトをコピーし、意味のある値は返しません。 同期バージョンでは、`CopyTo` への呼び出しは値を返さない単純なステートメントです。 非同期バージョン`CopyToAsync`、 <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task>を返します タスクは "Task(void)" のように機能し、メソッドを待機できるようにします。 次のコードに示すように、`Await` または `await` を、`CopyToAsync` への呼び出しに適用します。  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
         上記のステートメントでは、次の&2; 行のコードを省略しています。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
4.  `GetURLContents` 内で必要な作業として残っているのは、メソッド シグネチャの調整のみです。 使用することができます、`Await`演算子でマークされたメソッドでのみ、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾子です。 メソッドとしてマークする修飾子を追加、 *async メソッド*次のコードを示します。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
5.  <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601></xref:System.Threading.Tasks.Task>できる、非同期メソッドの戻り値の型 Visual Basic でのメソッドは、`Task` または `Task(Of T)` を返す `Function` にするか、`Sub` にする必要があります。 通常、`Sub`メソッドは非同期のイベント ハンドラーでのみ使用場所`Sub`が必要です。 使用するその他の場合、 `Task(T)` 、完成したメソッドがある場合、[返す](../../../../visual-basic/language-reference/statements/return-statement.md)の値を返すステートメントは、T を入力し、使用する`Task`完成したメソッドの有効な値が返されない場合。  
  
     詳細については、次を参照してください。 [Async を返す型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。  
  
     メソッド `GetURLContents` には return ステートメントがあり、このステートメントはバイト配列を返します。 そのため、非同期バージョンの戻り値の型は Task(T) であり、T はバイト配列です。 メソッド シグネチャに、次の変更を加えます。  
  
    -   戻り値の型を変更する`Task(Of Byte())`です。  
  
    -   規則により、非同期メソッドは "Async" で終わる名前を持つことになっているため、メソッドの名前を `GetURLContentsAsync` に変更します。  
  
     これらの変更を次のコードに示します。  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     このいくつかの変更によって、`GetURLContents` の非同期メソッドへの変換が完了しました。  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a>SumPageSizes を非同期メソッドに変換するには  
  
1.  `SumPageSizes` に対して、前述した手順を繰り返します。 まずは、`GetURLContents` への呼び出しを非同期呼び出しに変更します。  
  
    -   呼び出されるメソッドの名前を `GetURLContents` から `GetURLContentsAsync` に変更します (まだ変更していない場合)。  
  
    -   適用`Await`タスクにいる`GetURLContentsAsync`バイトを取得するを返します。 配列の値。  
  
     これらの変更を次のコードに示します。  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     上記の割り当てでは、次の&2; 行のコードを省略しています。  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  メソッドのシグネチャに、次の変更を加えます。  
  
    -   使用してメソッドをマーク、`Async`修飾子です。  
  
    -   メソッド名に "Async" を追加します。  
  
    -   今回、タスク戻り変数の T がない理由は、`SumPageSizesAsync` が T のための値を返さないからです (メソッドには いいえ`Return`ステートメントです)。ただし、メソッドは待機可能になるために `Task` を返す必要があります。 したがってからメソッドの型を変更`Sub`に`Function`します。 関数の戻り値の型は、`Task` です。  
  
     これらの変更を次のコードに示します。  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     `SumPageSizes` から `SumPageSizesAsync` への変換が完了しました。  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a>StartButton_Click を非同期メソッドに変換するには  
  
1.  イベント ハンドラーで、呼び出されるメソッドの名前を `SumPageSizes` から `SumPageSizesAsync` に変更します (まだ変更していない場合)。  
  
2.  `SumPageSizesAsync` は非同期メソッドであるため、結果を待機するイベント ハンドラーのコードを変更します。  
  
     `SumPageSizesAsync` への呼び出しは、`GetURLContentsAsync` の `CopyToAsync` への呼び出しに似ています。 この呼び出しによって、`Task(T)` ではなく `Task` が返されます。  
  
     前述した手順と同様に、1 つまたは&2; つのステートメントを使用して、呼び出しを変換できます。 これらの変更を次のコードに示します。  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  誤って、操作を再入力を防ぐためには、次のステートメントを追加の上部にある`startButton_Click`を無効にする、**開始** ボタンをクリックします。  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     イベント ハンドラーの末尾で、ボタンを再び有効にできます。  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     再入の詳細については、次を参照してください。 [(Visual Basic) の非同期アプリにおける再入の処理](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)します。  
  
4.  最後に、追加、`Async`修飾子、宣言をイベント ハンドラーを待機できるように`SumPagSizesAsync`します。  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     通常、イベント ハンドラーの名前は変更されません。 戻り値の型は変更されずに`Task`イベント ハンドラーがある必要がありますので`Sub`Visual Basic におけるプロシージャです。  
  
     同期処理から非同期処理へのプロジェクトの変換が完了しました。  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a>非同期のソリューションをテストするには  
  
1.  F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。  
  
2.  同期ソリューションの出力に似た出力が表示されます。 ただし、次の相違点に注意してください。  
  
    -   処理の完了後に、すべての結果が同時に表示されることはありません。 たとえば、両方のプログラムの `startButton_Click` には、テキスト ボックスをクリアする行が含まれています。 選択した場合の実行の間のテキスト ボックスをオフにすることが目的、**開始**1 組の結果が表示されたら、2 回ボタンをクリックします。 同期バージョンでは、2 回目のカウントが表示される直前、ダウンロードが完了して UI スレッドが他の処理を実行できる状態になったときにテキスト ボックスがクリアされます。 選択した後すぐに、非同期バージョンで、テキスト ボックスをクリア、**開始** ボタンをクリックします。  
  
    -   最も重要な点は、ダウンロード中に UI スレッドがブロックされないことです。 Web リソースをダウンロード、カウント、および表示している間に、ウィンドウの移動やサイズ変更を行うことができます。 Web サイトのいずれかの処理が遅いか応答していないする操作を取り消すことを選択している場合、**閉じる**(右上隅の赤いフィールドに x) ボタンをクリックします。  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a>GetURLContentsAsync メソッドを .NET Framework メソッドに置き換えます  
  
1.  .NET Framework 4.5 では、使用できる非同期メソッドが数多く用意されています。 1 つで、<xref:System.Net.Http.HttpClient>メソッド<xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>、必要なものだけをこのチュートリアルでは</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29></xref:System.Net.Http.HttpClient>。 これを、前述の手順で作成した `GetURLContentsAsync` メソッドの代わりに使用できます。  
  
     まずは、`SumPageSizesAsync` メソッドに `HttpClient` オブジェクトを作成します。 次の宣言をメソッドの先頭に追加します。  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  `SumPageSizesAsync,` で、`GetURLContentsAsync` メソッドへの呼び出しを `HttpClient` メソッドへの呼び出しに置き換えます。  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  記述した `GetURLContentsAsync` メソッドを削除するかコメント アウトします。  
  
4.  F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。  
  
     このバージョンのプロジェクトの動作は、「非同期ソリューションをテストするには」の手順で説明している動作と同じですが、さらに少ない手間で作成できます。  
  
##  <a name="BKMK_CompleteCodeExamples"></a>使用例  
 次のコードには、記述した非同期 `GetURLContentsAsync` メソッドを使用する、同期ソリューションから非同期ソリューションへの変換例のすべてが含まれています。 この例は、元の同期ソリューションと非常によく似ています。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
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
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
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
  
 次のコードには、`HttpClient` の `GetByteArrayAsync` メソッドを使用するソリューション例のすべてが含まれています。  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
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
  
## <a name="see-also"></a>関連項目  
 [非同期のサンプル: Web のチュートリアル (c# および Visual Basic) にアクセスします。](http://go.microsoft.com/fwlink/?LinkId=255191)   
 [Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)   
 [非同期](../../../../visual-basic/language-reference/modifiers/async.md)   
 [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [タスク ベースの非同期プログラミング (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847)   
 [方法: Task.WhenAll (Visual Basic) を使用して Asyncwalkthrough を拡張](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)   
 [方法: 並列で Async を使用して、複数の Web 要求を実行して、Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
