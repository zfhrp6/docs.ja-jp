---
title: "ファイル アクセスにおける非同期の使用 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d6272baa9beae405148185abfebde84ca0cb7d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="e2f74-102">ファイル アクセスにおける非同期の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="e2f74-102">Using Async for File Access (C#)</span></span>
<span data-ttu-id="e2f74-103">ファイルにアクセスする際に非同期機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-103">You can use the async feature to access files.</span></span> <span data-ttu-id="e2f74-104">非同期機能を使用すると、コールバックの使用や複数のメソッドまたはラムダ式へのコードの分割を行わずに、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-104">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="e2f74-105">同期コードを非同期コードにするには、同期メソッドの代わりに非同期メソッドを呼び出して、コードにいくつかのキーワードを追加するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="e2f74-106">ファイル アクセスの呼び出しに非同期性を適用する利点には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="e2f74-107">非同期性により、UI アプリケーションの応答性が向上します。非同期処理を開始した UI スレッドが他の処理を実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="e2f74-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="e2f74-108">UI スレッドが、時間のかかるコード、たとえば 50 ミリ秒を超えるコードを実行する必要がある場合、I/O が完了して、UI スレッドがキーボードやマウス入力などのイベントを再度処理できるようになるまで、UI が停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="e2f74-109">非同期性を適用すると、スレッドの必要性が軽減され、ASP.NET などのサーバー ベースのアプリケーションのスケーラビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="e2f74-110">アプリケーションが応答ごとに専用スレッドを使用している場合、1,000 個の要求を同時に処理するには、1,000 個のスレッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="e2f74-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="e2f74-111">非同期処理では、待機中にスレッドを使用する必要がほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="e2f74-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="e2f74-112">既存の I/O 完了スレッドが最後に少しだけ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="e2f74-113">現状ではファイル アクセス操作の待機時間が非常に短くても、将来に大幅に長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="e2f74-114">たとえば、地球の裏側にあるサーバーにファイルが移動される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="e2f74-115">非同期機能の使用に伴うオーバーヘッドはわずかです。</span><span class="sxs-lookup"><span data-stu-id="e2f74-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="e2f74-116">非同期タスクは簡単に並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="e2f74-117">例の実行</span><span class="sxs-lookup"><span data-stu-id="e2f74-117">Running the Examples</span></span>  
 <span data-ttu-id="e2f74-118">このトピックの例を実行するには、**WPF アプリケーション**または **Windows フォーム アプリケーション**を作成し、**ボタン**を追加します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="e2f74-119">ボタンの `Click` イベントに、それぞれの例で最初のメソッドの呼び出しを追加してください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="e2f74-120">以降の例には、次の `using` ステートメントを含めてください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-120">In the following examples, include the following `using` statements.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="e2f74-121">FileStream クラスの使用</span><span class="sxs-lookup"><span data-stu-id="e2f74-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="e2f74-122">このトピックの例では、<xref:System.IO.FileStream> クラスを使用します。このクラスには、非同期 I/O をオペレーティング システム レベルで発生させるオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e2f74-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="e2f74-123">このオプションを使用すると、多くのケースで ThreadPool スレッドがブロックされるのを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="e2f74-124">このオプションを有効にするには、コンストラクター呼び出しで `useAsync=true` または `options=FileOptions.Asynchronous` 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="e2f74-125">ファイル パスを指定して <xref:System.IO.StreamReader> と <xref:System.IO.StreamWriter> を直接開いた場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="e2f74-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="e2f74-126">一方、<xref:System.IO.FileStream> クラスによって開かれた <xref:System.IO.Stream> を使用する場合は、このオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="e2f74-127">UI アプリでは、ThreadPool スレッドがブロックされた場合でも、非同期呼び出しのほうが高速です。これは、UI スレッドは待機中にブロックされないためです。</span><span class="sxs-lookup"><span data-stu-id="e2f74-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="e2f74-128">テキストの書き込み</span><span class="sxs-lookup"><span data-stu-id="e2f74-128">Writing Text</span></span>  
 <span data-ttu-id="e2f74-129">次の例では、ファイルにテキストを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-129">The following example writes text to a file.</span></span> <span data-ttu-id="e2f74-130">各 await ステートメントに達すると、メソッドは直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="e2f74-131">ファイル I/O が完了すると、メソッドは await ステートメントの後のステートメントから再開します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="e2f74-132">await ステートメントを使用するメソッドの定義に async 修飾子が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async void ProcessWrite()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="e2f74-133">元の例には `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` ステートメントがあります。これは、次の 2 つのステートメントの省略形です。</span><span class="sxs-lookup"><span data-stu-id="e2f74-133">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="e2f74-134">最初のステートメントはタスクを返し、ファイル処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="e2f74-135">await が含まれた 2 番目のステートメントによって、メソッドが直ちに終了し、別のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="e2f74-136">ファイル処理が完了すると、await の後のステートメントに実行が戻ります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="e2f74-137">詳細については、「[非同期プログラムにおける制御フロー (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-137">For more information, see  [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="e2f74-138">テキストの読み取り</span><span class="sxs-lookup"><span data-stu-id="e2f74-138">Reading Text</span></span>  
 <span data-ttu-id="e2f74-139">次の例では、ファイルからテキストを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-139">The following example reads text from a file.</span></span> <span data-ttu-id="e2f74-140">テキストはバッファーに格納されます。この例では <xref:System.Text.StringBuilder> に配置されます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="e2f74-141">前の例と異なり、await の評価で値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="e2f74-142"><xref:System.IO.Stream.ReadAsync%2A> メソッドによって <xref:System.Threading.Tasks.Task>\<<xref:System.Int32> が返されます。処理の完了後、await の評価によって `Int32` 値 (`numRead`) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="e2f74-143">詳しくは、「[非同期の戻り値の型 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-143">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
```csharp  
public async void ProcessRead()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="e2f74-144">並列非同期 I/O</span><span class="sxs-lookup"><span data-stu-id="e2f74-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="e2f74-145">次の例では、10 個のテキスト ファイルを記述する並列処理を示します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="e2f74-146"><xref:System.IO.Stream.WriteAsync%2A> メソッドは、ファイルごとにタスクを返します。タスクはタスクの一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="e2f74-147">`await Task.WhenAll(tasks);` ステートメントはメソッドを終了し、すべてのタスクのファイル処理が完了すると、メソッド内で再開します。</span><span class="sxs-lookup"><span data-stu-id="e2f74-147">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="e2f74-148">この例では、タスクの完了後、`finally` ブロックのすべての <xref:System.IO.FileStream> インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-148">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="e2f74-149">`using` ステートメントで `FileStream` が作成された場合は、タスクが完了する前に `FileStream` が破棄されることがあります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-149">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="e2f74-150">パフォーマンスの向上のほとんどが、非同期処理ではなく並列処理によって実現していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="e2f74-151">非同期性の利点は、複数のスレッドやユーザー インターフェイス スレッドが拘束されなくなる点にあります。</span><span class="sxs-lookup"><span data-stu-id="e2f74-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async void ProcessWriteMult()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="e2f74-152"><xref:System.IO.Stream.WriteAsync%2A> メソッドと <xref:System.IO.Stream.ReadAsync%2A> メソッドを使用すると、<xref:System.Threading.CancellationToken> を指定して、途中で処理をキャンセルすることができます。</span><span class="sxs-lookup"><span data-stu-id="e2f74-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="e2f74-153">詳細については、「[非同期アプリケーションの微調整 (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)」および「[マネージ スレッドのキャンセル](../../../../standard/threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2f74-153">For more information, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f74-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2f74-154">See Also</span></span>  
 [<span data-ttu-id="e2f74-155">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="e2f74-155">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="e2f74-156">非同期の戻り値の型 (C#)</span><span class="sxs-lookup"><span data-stu-id="e2f74-156">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="e2f74-157">非同期プログラムにおける制御フロー (C#)</span><span class="sxs-lookup"><span data-stu-id="e2f74-157">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
