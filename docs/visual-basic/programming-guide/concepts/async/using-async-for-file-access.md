---
title: "非同期ファイルへのアクセス (Visual Basic) の使用 |Microsoft ドキュメント"
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
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
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
ms.openlocfilehash: e0e548989b1d2c32b9faf5ce0dd90ae371dfc028
ms.lasthandoff: 03/13/2017

---
# <a name="using-async-for-file-access-visual-basic"></a>ファイル アクセスにおける非同期の使用 (Visual Basic)
非同期機能を使用して、ファイルにアクセスすることができます。 非同期機能を使用すると、コールバックの使用や複数のメソッドまたはラムダ式へのコードの分割を行わずに、非同期メソッドを呼び出すことができます。 同期コードを非同期にするだけ同期メソッドの代わりに非同期のメソッドを呼び出すをコードにいくつかのキーワードを追加します。  
  
 ファイル アクセスの呼び出しを非同期処理を追加するために、次の理由を考慮することがあります。  
  
-   非同期性により、UI アプリケーション応答性の高い、操作を起動する UI スレッドが他の作業を実行するためです。 コードを UI スレッドで実行する必要があります (たとえば、50 を超えるミリ秒) の長い時間がかかること、UI がフリーズ、I/O が完了して、UI スレッドをもう一度キーボードを処理およびマウス入力やその他のイベントまで。  
  
-   非同期処理では、ASP.NET のスケーラビリティおよびその他のサーバー ベースのアプリケーションがスレッドの必要性を減らすことによって向上します。 アプリケーションが応答ごとに専用のスレッドを使用して、1000 単位の要求が同時に処理されている場合は、3 桁のスレッドが必要です。 多くの場合、非同期操作は、待機中のスレッドを使用する必要ありません。 既存の I/O 完了スレッドは、最後に簡単に、使用します。  
  
-   ファイル アクセス操作の待機時間は、現在の状況では、非常に少ない可能性がありますが、待機時間は大幅に、将来増加します。 たとえば、世界中であるサーバーにファイルを移動することがあります。  
  
-   追加された非同期機能を使用するオーバーヘッドは小さいです。  
  
-   非同期タスクは、並列で簡単に実行できます。  
  
## <a name="running-the-examples"></a>例の実行  
 このトピックの例を実行するには、作成、 **WPF アプリケーション**または**Windows フォーム アプリケーション**し、追加、**ボタン**します。 ボタンの`Click`イベント、それぞれの例に最初のメソッドの呼び出しを追加します。  
  
 次の例については、次が含まれる`Imports`ステートメントです。  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>FileStream クラスの使用方法  
 このトピックで例として、<xref:System.IO.FileStream>クラスで、オペレーティング システム レベルで発生する非同期 I/O を原因となるオプションがあります</xref:System.IO.FileStream>。 このオプションを使用すると、多くの場合、ThreadPool のスレッドのブロックを回避できます。 指定するには、このオプションを有効にする、`useAsync=true`または`options=FileOptions.Asynchronous`のコンス トラクター呼び出しの引数。  
  
 <xref:System.IO.StreamReader><xref:System.IO.StreamWriter>ファイル パスを指定して直接開くかどうか</xref:System.IO.StreamWriter></xref:System.IO.StreamReader>と、このオプションを使用することはできません。 そこで指定する場合、このオプションを使用する、<xref:System.IO.Stream>を<xref:System.IO.FileStream>クラスを開く</xref:System.IO.FileStream></xref:System.IO.Stream>。 非同期呼び出しがあること UI アプリで高速なスレッド プールのスレッドがブロックされている場合でも、待機中に UI スレッドがブロックされていないので注意してください。  
  
## <a name="writing-text"></a>テキストの書き込み  
 次の例では、テキストをファイルに書き込みます。 Await ステートメントのそれぞれで、メソッドがすぐに終了します。 ファイル I/O が完了すると、メソッドは await ステートメントに続くステートメントから再開されます。 Async 修飾子が await ステートメントを使用するメソッドの定義に注意してください。  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 元の例には、ステートメントが含まれている`Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`、これは、次の 2 つのステートメントの省略形。  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 最初のステートメントは、タスクを返し、ファイル処理が開始します。 Await で&2; 番目のステートメントをすぐに終了し、別のタスクを返すメソッドです。 ファイルの後で処理が完了したら、実行が await の次のステートメントに返します。 詳細については、次を参照してください。[非同期プログラム (Visual Basic) の制御フロー](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)します。  
  
## <a name="reading-text"></a>テキストの読み取り  
 次の例では、ファイルからテキストを読み取ります。 テキストがバッファーに格納され、この場合、保存されます<xref:System.Text.StringBuilder>。</xref:System.Text.StringBuilder> 異なり、前の例で await の評価値を生成します。 <xref:System.IO.Stream.ReadAsync%2A>メソッドが返される、 <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>> await の評価を生成するため、`Int32`値 (`numRead`)、操作が完了した後</xref:System.Int32></xref:System.Threading.Tasks.Task></xref:System.IO.Stream.ReadAsync%2A>。 詳細については、次を参照してください。 [Async を返す型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a>並列の非同期 I/O  
 次の例では、10 個のテキスト ファイルを記述して並列処理を示します。 ファイルごとに、<xref:System.IO.Stream.WriteAsync%2A>メソッドは、タスクの一覧に追加するタスクを返します</xref:System.IO.Stream.WriteAsync%2A>。 `Await Task.WhenAll(tasks)`ステートメントは、メソッドを終了し、すべてのタスクのファイルの処理がメソッド内の再開を完了します。  
  
 この例ではすべて<xref:System.IO.FileStream>のインスタンス、`Finally`タスクが完了したらをブロックします</xref:System.IO.FileStream>。 各`FileStream`で作成した代わりに、`Imports`ステートメント、`FileStream`タスクが完了する前に破棄することがあります。  
  
 すべてのパフォーマンスの向上が並列処理と非同期処理ではないからほぼ完全ことに注意してください。 非同期性のメリットは、複数のスレッドせず拘束されないことと、ユーザー インターフェイス スレッドせず拘束されないことです。  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 使用する場合、<xref:System.IO.Stream.WriteAsync%2A>と<xref:System.IO.Stream.ReadAsync%2A>メソッドを指定できます、<xref:System.Threading.CancellationToken>を操作の途中で取り消すことができます</xref:System.Threading.CancellationToken></xref:System.IO.Stream.ReadAsync%2A></xref:System.IO.Stream.WriteAsync%2A>。 詳細については、次を参照してください。[微調整 Your Async アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)と[マネージ スレッドのキャンセル](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3)します。  
  
## <a name="see-also"></a>関連項目  
 [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [(Visual Basic) の非同期プログラムにおける制御フロー](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
