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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 64a708e3b88f48ad30d3f3ad25141a31f3d8f73d
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>(Visual Basic) の非同期アプリにおける再入の処理
非同期コードをアプリに含める場合は、再入を考慮し、場合によっては回避することをお勧めします。これは、完了前に非同期操作の再入力を参照します。 再入の可能性を特定して処理しないと、予期しない結果が発生する可能性があります。  
  
 **このトピックの内容**  
  
-   [再入を認識](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [再入の処理](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [[スタート] ボタンを無効にします。](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [キャンセルし、操作を再開](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [複数の操作を実行し、キューの出力](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [確認して、アプリケーションの例を実行します。](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。  
  
##  <a name="BKMK_RecognizingReentrancy"></a>再入を認識  
 このトピックの例では、ユーザーが選択、**開始**を一連の web サイトをダウンロードして、ダウンロードされるバイト数の合計を計算する非同期のアプリを開始 ボタンをクリックします。 同期バージョンの例では、ユーザーが何回ボタンをクリックしても同じように応答します。2 回目以降はアプリが実行を完了するまで、UI スレッドはこれらのイベントを無視するからです。 ただし、非同期アプリでは、UI スレッドは応答し続けるので、完了前に非同期操作を再入力することがあります。  
  
 次の例は、予想される、ユーザーが選択したかどうかの出力、**開始**一度だけ ボタンをクリックします。 ダウンロードされた Web サイトの一覧には、各サイトのサイズがバイト単位で表示されます。 合計バイト数は最後に表示されます。  
  
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
  
 ただし、ユーザーがボタンを複数回クリックすると、イベント ハンドラーは繰り返し呼び出され、ダウンロード プロセスはそのたびに再入力されます。 その結果、複数の非同期操作が同時に実行され、出力は結果をインターリーブするので、合計バイト数がややこしくなります。  
  
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
  
 このトピックの最後にスクロールすると、この出力を生成するコードをレビューできます。 ローカル コンピューターに、ソリューションをダウンロードし、WebsiteDownload プロジェクトを実行してコードを試してみるか、コードは、このトピックの最後に使用すると詳細と手順については、独自のプロジェクトを作成する、次を参照してください。[確認して、アプリケーションの例を実行する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)です。  
  
##  <a name="BKMK_HandlingReentrancy"></a>再入の処理  
 再入の処理は、アプリで何を行うかに応じてさまざまな方法で実行できます。 このトピックでは、次の例を紹介します。  
  
-   [[スタート] ボタンを無効にします。](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     無効にする、**開始**ユーザーが中断できないように、操作の実行中にボタンをクリックします。  
  
-   [キャンセルし、操作を再開](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     ユーザーが選択したときに実行されているすべての操作をキャンセル、**開始**を再度クリックし、続行できるように、最後に要求された操作。  
  
-   [複数の操作を実行し、キューの出力](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     要求されたすべての処理を非同期的に実行できるようにします。ただし、各処理の結果が順番にまとめて表示されるように出力を調整します。  
  
###  <a name="BKMK_DisableTheStartButton"></a>[スタート] ボタンを無効にします。  
 ブロックすることができます、**開始**ボタンの上部にあるボタンを無効にすると、操作の実行中に、`StartButton_Click`イベント ハンドラーです。 処理が完了しユーザーが再度アプリを実行できるようになったら、`Finally` ブロック内からこのボタンを再度有効にできます。  
  
 次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。 変更内容を追加するには、このトピックの最後のコードにかから完成したアプリをダウンロードする[Async のサンプル: .NET デスクトップ アプリにおける再入](http://go.microsoft.com/fwlink/?LinkId=266571)します。 プロジェクト名は DisableStartButton です。  
  
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
  
 変更の結果、`AccessTheWebAsync` が Web サイトをダウンロードしている間は、ボタンが応答しないので、プロセスを再入力できません。  
  
###  <a name="BKMK_CancelAndRestart"></a>キャンセルし、操作を再開  
 無効にせず、**開始** ボタンをすることができます、ボタンをアクティブにしておくが、ここでも、そのボタンを選択した場合、処理を取り消しが既に実行されていると、最後に開始された処理を続行します。  
  
 キャンセルの詳細については、次を参照してください。[微調整 Your Async アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)します。  
  
 このシナリオをセットアップするには、基本的なコードで提供されている次の変更を加えて[確認して、アプリケーションの例を実行する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)です。 ダウンロードすることも、完了したアプリから[Async のサンプル: .NET デスクトップ アプリにおける再入](http://go.microsoft.com/fwlink/?LinkId=266571)します。 このプロジェクトの名前は CancelAndRestart です。  
  
1.  宣言、<xref:System.Threading.CancellationTokenSource>変数`cts`、すべてのメソッドのスコープである</xref:System.Threading.CancellationTokenSource>。  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  `StartButton_Click` で、処理が既に実行されているかどうかを確認します。 場合の値`cts`は`Nothing`操作は既にアクティブです。 値がない場合`Nothing`、既に実行されている操作が取り消されました。  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  `cts` に、現在のプロセスを表す別の値を設定します。  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  末尾に`StartButton_Click`、現在のプロセスが完了したら、そのための値を設定`cts`に`Nothing`します。  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 次のコードは、`StartButton_Click` のすべての変更を示しています。 追加部分はアスタリスクが付いています。  
  
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
  
 `AccessTheWebAsync` で、次の変更を行います。  
  
-   `StartButton_Click` からキャンセル トークンを受け取るためのパラメーターを追加します。  
  
-   使用して、<xref:System.Net.Http.HttpClient.GetAsync%2A>ために、web サイトをダウンロードする方法`GetAsync`を受け入れる、<xref:System.Threading.CancellationToken>引数</xref:System.Threading.CancellationToken></xref:System.Net.Http.HttpClient.GetAsync%2A>。  
  
-   `DisplayResults` を呼び出してダウンロードした各 Web サイトの結果を表示する前に、`ct` で、現在の処理が取り消されていないことを確認します。  
  
 次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。  
  
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
  
 選択した場合、**開始**を複数回クリックしてこのアプリの実行中には、次の出力のような結果が生成されます。  
  
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
  
 部分的なリストを削除するには、`StartButton_Click` コードの先頭行のコメントを解除して、ユーザーが操作を再開するたびに、テキスト ボックスをクリアします。  
  
###  <a name="BKMK_RunMultipleOperations"></a>複数の操作を実行し、キューの出力  
 この&3; 番目の例は、アプリケーション、ユーザーが選択されるたびに非同期操作の開始点で最も複雑な**開始** ボタン、およびすべての操作が完了するまで実行します。 要求されたすべての操作によって Web サイトがリストから非同期的にダウンロードされますが、操作からの出力は順次表示されます。 つまり、実際のダウンロード アクティビティはインターリーブされますに出力として[を認識する再入](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)が示すように、各グループの結果のリストは個別に表示されます。  
  
 操作共有グローバル<xref:System.Threading.Tasks.Task>、 `pendingWork`、これは、表示プロセスのゲートキーパーとして機能します</xref:System.Threading.Tasks.Task>。  
  
 内のコードに変更内容を貼り付けることによってこの例を実行する[アプリケーションを構築する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、」の手順に従うこともできます[アプリをダウンロードする](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)サンプルをダウンロードし、QueueResults プロジェクトを実行します。  
  
 次の出力は、ユーザーが選択したかどうか、結果を示します、**開始**一度だけ ボタンをクリックします。 文字ラベル A は、初めてから結果であることを示します、**開始**ボタンを選択します。 数字は、ダウンロード対象の一覧における URL の順序を示しています。  
  
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
  
 ユーザーが選択した場合、**開始**ボタンを&3; 回、アプリには、次の行のような出力が生成されます。 先頭にシャープ記号 (#) が付いている情報行は、アプリケーションの進行状況を追跡します。  
  
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
  
 グループ B とグループ C は、グループ A が終了する前に開始します。ただし、各グループの出力は個別に表示されます。 グループ A のすべての出力は表示グループ B のすべての出力とすべての出力グループ C. に続く&1; つは、アプリケーションは必ずの順序でグループを表示され、グループごとに、Url は、Url の一覧に表示される順序で常に個別の web サイトに関する情報を表示します。  
  
 ただし、ダウンロードが実際に行われる順序は予測できません。 複数のグループが開始されたら、そのグループが生成するダウンロード タスクはすべてのアクティブです。 B-1 の前に A-1 がダウンロードされる、また、A-2 の前に A-1 がダウンロードされると仮定することはできません。  
  
#### <a name="global-definitions"></a>グローバル定義  
 サンプル コードには、すべてのメソッドから参照できる次の&2; つのグローバル宣言が含まれます。  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 `Task` 変数、`pendingWork` は、表示プロセスを監視し、あるグループが別のグループの表示操作を中断しないようにします。 文字変数 `group` は、異なるグループからの出力にラベルを付け、予想された順序で結果が表示されていることを確認します。  
  
#### <a name="the-click-event-handler"></a>Click イベント ハンドラー  
 イベント ハンドラー `StartButton_Click`、インクリメントします、ユーザーが選択するたびに、**開始** ボタンをクリックします。 ハンドラーは `AccessTheWebAsync` を呼び出して、ダウンロード操作を実行します。  
  
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
  
#### <a name="the-accessthewebasync-method"></a>AccessTheWebAsync メソッド  
 この例では、`AccessTheWebAsync` を&2; つのメソッドに分割します。 最初のメソッド、`AccessTheWebAsync` は、グループのすべてのダウンロード タスクを開始し、`pendingWork` を設定して表示プロセスを制御します。 メソッドは、言語統合クエリ (LINQ クエリ) を使用し、<xref:System.Linq.Enumerable.ToArray%2A>を同時にすべてのダウンロード タスクを開始します</xref:System.Linq.Enumerable.ToArray%2A>。  
  
 その後、`AccessTheWebAsync` は、`FinishOneGroupAsync` を呼び出して各ダウンロードが完了するまで待機し、その長さを表示します。  
  
 `FinishOneGroupAsync` は、`pendingWork` の `AccessTheWebAsync` に割り当てられたタスクを返します。 この値は、タスクが完了する前に、別の操作によって操作が中断されないようにします。  
  
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
  
#### <a name="the-finishonegroupasync-method"></a>FinishOneGroupAsync メソッド  
 このメソッドは、グループのダウンロード タスクを循環参照し、それぞれを待機してから、ダウンロードされた Web サイトの長さを表示して、その長さを合計に追加します。  
  
 最初のステートメントで`FinishOneGroupAsync`を使用して`pendingWork`するメソッドを入力する妨げにならないで操作を実行、表示プロセスにではないかを既に待機しているかどうかを確認します。 これらの操作が進行中の場合、入力操作は順番を待つ必要があります。  
  
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
  
 内のコードに変更内容を貼り付けることによってこの例を実行する[アプリケーションを構築する](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、」の手順に従うこともできます[アプリをダウンロードする](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)サンプルをダウンロードし、QueueResults プロジェクトを実行します。  
  
#### <a name="points-of-interest"></a>目的のポイント  
 出力で先頭にシャープ記号 (#) が付いている情報行は、この例の動作を明確に示しています。  
  
 出力のパターンを次に示します。  
  
-   前のグループが出力を表示していても、グループを開始できます。その際、前のグループの出力の表示は中断されません。  
  
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
  
-   `pendingWork`タスクは、`Nothing`の開始時`FinishOneGroupAsync`グループ A についてのみが最初に開始します。 `FinishOneGroupAsync` に達したとき、グループ A はまだ await 式を完了していません。 したがって、コントロールは `AccessTheWebAsync` に戻っておらず、`pendingWork` への最初の割り当ては発生していません。  
  
-   次の&2; 行は、出力に必ず同時に表示されます。 `StartButton_Click` のグループ操作が開始してから、グループのタスクが `pendingWork` に割り当てられるまでの間、コードが中断されることは決してありません。  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     グループが `StartButton_Click` に移行したら、`FinishOneGroupAsync` に移行するまでは、await 式は完了しません。 したがって、コード セグメントの途中で、他の操作がコントロールを得ることはありません。  
  
##  <a name="BKMD_SettingUpTheExample"></a>確認して、アプリケーションの例を実行します。  
 サンプル アプリをさらに詳しく理解するには、そのアプリをダウンロードし、ご自身でビルドしてみてください。また、このトピックの最後にあるコードをレビューすることもできます。アプリを実装する必要はありません。  
  
> [!NOTE]
>  Windows Presentation Foundation (WPF) デスクトップ アプリとして例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。  
  
###  <a name="BKMK_DownloadingTheApp"></a>アプリをダウンロードします。  
  
1.  圧縮ファイルをダウンロード[Async のサンプル: .NET デスクトップ アプリにおける再入](http://go.microsoft.com/fwlink/?LinkId=266571)します。  
  
2.  ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。  
  
3.  メニュー バーで **[ファイル]**、 **[開く]**、 **[プロジェクト/ソリューション]**の順に選択します。  
  
4.  圧縮解除したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開きます。  
  
5.  **ソリューション エクスプ ローラー**、実行、および順に選択するプロジェクトのショートカット メニューを開いて**スタートアップ プロジェクトに設定として設定**します。  
  
6.  Ctrl キーを押しながら F5 キーを押してプロジェクトをビルドし、実行します。  
  
###  <a name="BKMK_BuildingTheApp"></a>アプリケーションを構築します。  
 次のセクションでは、WPF アプリとして例をビルドするコードを提供します。  
  
##### <a name="to-build-a-wpf-app"></a>WPF アプリをビルドするには  
  
1.  Visual Studio を起動します。  
  
2.  メニュー バーで、 **[ファイル]**、 **[新規作成]**、 **[プロジェクト]**の順にクリックします。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **インストールされたテンプレート** ウィンドウで、展開**Visual Basic**、順に展開**Windows**します。  
  
4.  プロジェクトの種類の一覧で選択**WPF アプリケーション**します。  
  
5.  プロジェクトに名前を`WebsiteDownloadWPF`を選択し、 **OK**  ボタンをクリックします。  
  
     新しいプロジェクトに表示されます**ソリューション エクスプ ローラー**します。  
  
6.  Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。  
  
     タブが表示されない場合で MainWindow.xaml のショートカット メニューを開き**ソリューション エクスプ ローラー**、にして**コードの表示**します。  
  
7.  **XAML** MainWindow.xaml のビューで、コードを次のコードに置き換えます。  
  
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
  
     テキスト ボックスとボタンを含む簡単なウィンドウに表示、**デザイン**MainWindow.xaml のビューです。  
  
8.  <xref:System.Net.Http>。</xref:System.Net.Http>への参照を追加します。  
  
9. **ソリューション エクスプ ローラー**MainWindow.xaml.vb のショートカット メニューを開き、クリックして**コードの表示**します。  
  
10. MainWindow.xaml.vb で、コードを次のコードに置き換えます。  
  
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
  
11. CTRL + F5 キーをクリックして、プログラムの実行を**開始**を複数回クリックします。  
  
12. 変更を加える[[スタート] ボタンを無効にする](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、[をキャンセルし、操作を再開](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)、または[複数の操作を実行して出力をキュー](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)を行って再入を処理します。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: Async を使用して Web へのアクセスと Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)

