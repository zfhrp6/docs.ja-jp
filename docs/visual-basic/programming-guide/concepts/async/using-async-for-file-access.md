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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 85f5fe17a012402c406eed972debd1f5889dd393
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="f3d8f-102">ファイル アクセスにおける非同期の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3d8f-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="f3d8f-103">非同期機能を使用して、ファイルにアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="f3d8f-104">非同期機能を使用すると、コールバックの使用や複数のメソッドまたはラムダ式へのコードの分割を行わずに、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="f3d8f-105">同期コードを非同期にするだけ同期メソッドの代わりに非同期のメソッドを呼び出すをコードにいくつかのキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="f3d8f-106">ファイル アクセスの呼び出しを非同期処理を追加するために、次の理由を考慮することがあります。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="f3d8f-107">非同期性により、UI アプリケーション応答性の高い、操作を起動する UI スレッドが他の作業を実行するためです。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="f3d8f-108">コードを UI スレッドで実行する必要があります (たとえば、50 を超えるミリ秒) の長い時間がかかること、UI がフリーズ、I/O が完了して、UI スレッドをもう一度キーボードを処理およびマウス入力やその他のイベントまで。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="f3d8f-109">非同期処理では、ASP.NET のスケーラビリティおよびその他のサーバー ベースのアプリケーションがスレッドの必要性を減らすことによって向上します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="f3d8f-110">アプリケーションが応答ごとに専用のスレッドを使用して、1000 単位の要求が同時に処理されている場合は、3 桁のスレッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="f3d8f-111">多くの場合、非同期操作は、待機中のスレッドを使用する必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="f3d8f-112">既存の I/O 完了スレッドは、最後に簡単に、使用します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="f3d8f-113">ファイル アクセス操作の待機時間は、現在の状況では、非常に少ない可能性がありますが、待機時間は大幅に、将来増加します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="f3d8f-114">たとえば、世界中であるサーバーにファイルを移動することがあります。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="f3d8f-115">追加された非同期機能を使用するオーバーヘッドは小さいです。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="f3d8f-116">非同期タスクは、並列で簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="f3d8f-117">例の実行</span><span class="sxs-lookup"><span data-stu-id="f3d8f-117">Running the Examples</span></span>  
 <span data-ttu-id="f3d8f-118">このトピックの例を実行するには、作成、 **WPF アプリケーション**または**Windows フォーム アプリケーション**し、追加、**ボタン**します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="f3d8f-119">ボタンの`Click`イベント、それぞれの例に最初のメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="f3d8f-120">次の例については、次が含まれる`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="f3d8f-121">FileStream クラスの使用方法</span><span class="sxs-lookup"><span data-stu-id="f3d8f-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="f3d8f-122">このトピックで例として、<xref:System.IO.FileStream>クラスで、オペレーティング システム レベルで発生する非同期 I/O を原因となるオプションがあります</xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="f3d8f-123">このオプションを使用すると、多くの場合、ThreadPool のスレッドのブロックを回避できます。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="f3d8f-124">指定するには、このオプションを有効にする、`useAsync=true`または`options=FileOptions.Asynchronous`のコンス トラクター呼び出しの引数。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="f3d8f-125"><xref:System.IO.StreamReader><xref:System.IO.StreamWriter>ファイル パスを指定して直接開くかどうか</xref:System.IO.StreamWriter></xref:System.IO.StreamReader>と、このオプションを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="f3d8f-126">そこで指定する場合、このオプションを使用する、<xref:System.IO.Stream>を<xref:System.IO.FileStream>クラスを開く</xref:System.IO.FileStream></xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="f3d8f-127">非同期呼び出しがあること UI アプリで高速なスレッド プールのスレッドがブロックされている場合でも、待機中に UI スレッドがブロックされていないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="f3d8f-128">テキストの書き込み</span><span class="sxs-lookup"><span data-stu-id="f3d8f-128">Writing Text</span></span>  
 <span data-ttu-id="f3d8f-129">次の例では、テキストをファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-129">The following example writes text to a file.</span></span> <span data-ttu-id="f3d8f-130">Await ステートメントのそれぞれで、メソッドがすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="f3d8f-131">ファイル I/O が完了すると、メソッドは await ステートメントに続くステートメントから再開されます。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="f3d8f-132">Async 修飾子が await ステートメントを使用するメソッドの定義に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="f3d8f-133">元の例には、ステートメントが含まれている`Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`、これは、次の 2 つのステートメントの省略形。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="f3d8f-134">最初のステートメントは、タスクを返し、ファイル処理が開始します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="f3d8f-135">Await で&2; 番目のステートメントをすぐに終了し、別のタスクを返すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="f3d8f-136">ファイルの後で処理が完了したら、実行が await の次のステートメントに返します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="f3d8f-137">詳細については、次を参照してください。[非同期プログラム (Visual Basic) の制御フロー](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="f3d8f-138">テキストの読み取り</span><span class="sxs-lookup"><span data-stu-id="f3d8f-138">Reading Text</span></span>  
 <span data-ttu-id="f3d8f-139">次の例では、ファイルからテキストを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-139">The following example reads text from a file.</span></span> <span data-ttu-id="f3d8f-140">テキストがバッファーに格納され、この場合、保存されます<xref:System.Text.StringBuilder>。</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="f3d8f-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="f3d8f-141">異なり、前の例で await の評価値を生成します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="f3d8f-142"><xref:System.IO.Stream.ReadAsync%2A>メソッドが返される、 <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>> await の評価を生成するため、`Int32`値 (`numRead`)、操作が完了した後</xref:System.Int32></xref:System.Threading.Tasks.Task></xref:System.IO.Stream.ReadAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="f3d8f-143">詳細については、次を参照してください。 [Async を返す型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="f3d8f-144">並列の非同期 I/O</span><span class="sxs-lookup"><span data-stu-id="f3d8f-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="f3d8f-145">次の例では、10 個のテキスト ファイルを記述して並列処理を示します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="f3d8f-146">ファイルごとに、<xref:System.IO.Stream.WriteAsync%2A>メソッドは、タスクの一覧に追加するタスクを返します</xref:System.IO.Stream.WriteAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="f3d8f-147">`Await Task.WhenAll(tasks)`ステートメントは、メソッドを終了し、すべてのタスクのファイルの処理がメソッド内の再開を完了します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="f3d8f-148">この例ではすべて<xref:System.IO.FileStream>のインスタンス、`Finally`タスクが完了したらをブロックします</xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="f3d8f-149">各`FileStream`で作成した代わりに、`Imports`ステートメント、`FileStream`タスクが完了する前に破棄することがあります。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="f3d8f-150">すべてのパフォーマンスの向上が並列処理と非同期処理ではないからほぼ完全ことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="f3d8f-151">非同期性のメリットは、複数のスレッドせず拘束されないことと、ユーザー インターフェイス スレッドせず拘束されないことです。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="f3d8f-152">使用する場合、<xref:System.IO.Stream.WriteAsync%2A>と<xref:System.IO.Stream.ReadAsync%2A>メソッドを指定できます、<xref:System.Threading.CancellationToken>を操作の途中で取り消すことができます</xref:System.Threading.CancellationToken></xref:System.IO.Stream.ReadAsync%2A></xref:System.IO.Stream.WriteAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="f3d8f-153">詳細については、次を参照してください。[微調整 Your Async アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)と[マネージ スレッドのキャンセル](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3)します。</span><span class="sxs-lookup"><span data-stu-id="f3d8f-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d8f-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3d8f-154">See Also</span></span>  
 <span data-ttu-id="f3d8f-155">[非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3d8f-155">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="f3d8f-156"> [非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="f3d8f-156"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="f3d8f-157"> [(Visual Basic) の非同期プログラムにおける制御フロー](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span><span class="sxs-lookup"><span data-stu-id="f3d8f-157"> [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span></span>
