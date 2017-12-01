---
title: "タスク ベースの非同期パターンの利用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90b2a36f0e6bf06b0fefe2191d5b17c9c07d1588
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>タスク ベースの非同期パターンの利用
タスク ベースの非同期パターン (TAP) を使用して非同期操作を行うと、コールバックを使用して、ブロックすることなく待機できます。  タスクについては、これは、メソッドによってなど<xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>です。 言語ベースの非同期サポートが、通常の制御フロー内での非同期操作の待機を許可することで、コールバックを隠し、コンパイラにより生成されたコードはこの同じ API レベルのサポートを提供します。  
  
## <a name="suspending-execution-with-await"></a>Await による実行の中断  
 以降で、 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、使用することができます、 [await](~/docs/csharp/language-reference/keywords/await.md)キーワード (C#) および[Await 演算子](~/docs/visual-basic/language-reference/operators/await-operator.md)を非同期的に待機する Visual Basic で<xref:System.Threading.Tasks.Task>と<xref:System.Threading.Tasks.Task%601>オブジェクト。 待機しているときに、 <xref:System.Threading.Tasks.Task>、`await`式の型は`void`します。 待機しているときに、 <xref:System.Threading.Tasks.Task%601>、`await`式の型は`TResult`します。 `await` 式は、非同期メソッドの本体内に含める必要があります。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] における C# および Visual Basic の言語サポートの詳細については、C# および Visual Basic の言語仕様を参照してください。  
  
 待機機能は、隠れた状態で継続を使用してタスクにコールバックをインストールします。  このコールバックは中断ポイントから非同期メソッドを再開します。 非同期のメソッドが再開されたときに、待機中の操作が正常に完了された場合、 <xref:System.Threading.Tasks.Task%601>、その`TResult`が返されます。  場合、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>で終了を待機するが、 <xref:System.Threading.Tasks.TaskStatus.Canceled> 、状態、<xref:System.OperationCanceledException>例外がスローされます。  場合、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>で終了を待機するが、<xref:System.Threading.Tasks.TaskStatus.Faulted>状態にある場合にエラーの原因となった例外がスローされます。 `Task` は複数の例外の結果としてエラーになることがありますが、反映されるのはこれらの例外の中の 1 つのみです。 ただし、<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>プロパティから返される、<xref:System.AggregateException>例外は、すべてのエラーが含まれています。  
  
 場合、同期コンテキスト (<xref:System.Threading.SynchronizationContext>オブジェクト) の中断時に、非同期メソッドが実行しているスレッドに関連付けられて (場合など、<xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType>プロパティは使用されません`null`)、非同期のメソッドが再開します。コンテキストを使用して、同じ同期コンテキスト<xref:System.Threading.SynchronizationContext.Post%2A>メソッドです。 それ以外の場合、依存タスク スケジューラ (<xref:System.Threading.Tasks.TaskScheduler>オブジェクト) が現在中断時にします。 通常、これは既定のタスク スケジューラ (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>)、スレッド プールを対象とします。 このタスク スケジューラによって、待機していた非同期操作が完了した場合に再開するかどうか、または再開のスケジュールを設定するかどうかが決定されます。 既定のスケジューラは、通常、待機していた操作が完了したスレッド上での実行の継続を許可します。  
  
 非同期メソッドが呼び出された場合、まだ完了していない待機可能なインスタンスの最初の await 式まで、関数の本体を同期をとって実行し、この時点で呼び出しを呼び出し元に返します。 非同期のメソッドが返されなかった場合`void`、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>を継続的な計算を表すオブジェクトが返されます。 非 void の非同期メソッドに return ステートメントが発生したか、またはメソッド本体の末尾に達した場合、タスクの完了で、<xref:System.Threading.Tasks.TaskStatus.RanToCompletion>最終的な状態です。 未処理の例外では、コントロールを非同期メソッドの本体外に出すとの終了、<xref:System.Threading.Tasks.TaskStatus.Faulted>状態です。 その例外がある場合、 <xref:System.OperationCanceledException>、タスクの代わりに終了日、<xref:System.Threading.Tasks.TaskStatus.Canceled>状態です。 この方法では、結果または例外が最終的に発行されます。  
  
 この動作には、いくつかの重要なバリエーションがあります。  タスクが待機されるまでに既に完了していた場合は、パフォーマンス上の理由から、制御が明け渡されず、関数が実行を継続します。  また、元のコンテキストに戻ることが必ずしも望ましい動作ではない場合は変更されることがあります。これは、次のセクションで詳しく説明します。  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Yield と ConfigureAwait を使用して中断と再開を構成する  
 一部のメソッドでは、非同期メソッドの実行をより詳細に制御できます。 たとえば、使用することができます、<xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType>非同期メソッドに、徐行を表すポイントを導入する方法。  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 これは、非同期にポストするか、現在のコンテキストにスケジュールを戻すことと同じです。  
  
```csharp  
Task.Run(async delegate  
{  
    for(int i=0; i<1000000; i++)  
    {  
        await Task.Yield(); // fork the continuation into a separate work item  
        ...  
    }  
});  
```  
  
 使用することも、<xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType>を中断および再開する非同期メソッドでより細かく制御メソッド。  再開時に非同期メソッドの継続を呼び出すために非同期メソッドが中断され、そのキャプチャされたコンテキストが使用されている場合、既定では、既に説明したように現在のコンテキストがキャプチャされます。  これは、多くの場合に求められる動作です。  その他の場合では、継続のコンテキストが重要でないこともあり、元のコンテキストへのポスト バックを回避することでパフォーマンスを向上できます。  これを有効にするには、<xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType>にキャプチャし、コンテキストの再開はなく、実行を継続する待機対象が非同期の操作が完了した場所に、await 操作を通知します。  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>非同期操作の取り消し  
 以降で、 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、キャンセルをサポートする TAP メソッドは、キャンセル トークンを受け入れるには、少なくとも 1 つのオーバー ロードを提供 (<xref:System.Threading.CancellationToken>オブジェクト)。  
  
 キャンセル トークンが、キャンセル トークン ソースを作成 (<xref:System.Threading.CancellationTokenSource>オブジェクト)。  ソースの<xref:System.Threading.CancellationTokenSource.Token%2A>プロパティには、通知されるキャンセル トークンが返されます。 ときに、ソースの<xref:System.Threading.CancellationTokenSource.Cancel%2A>メソッドが呼び出されます。  たとえば、1 つの web ページをダウンロードする場合、操作を取り消すことができるを作成する、<xref:System.Threading.CancellationTokenSource>オブジェクト、TAP メソッドにそのトークンを渡すし、ソースを呼び出す<xref:System.Threading.CancellationTokenSource.Cancel%2A>操作をキャンセルする準備ができたら、メソッド。  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 複数の非同期呼び出しを取り消す場合は、すべての呼び出しに同じトークンを渡すことができます。  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 または、操作の一部を選択して同じトークンを渡すこともできます。  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 取り消し要求は任意のスレッドから開始することができます。  
  
 渡すことができます、<xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType>取り消しが要求しないことを示すためにキャンセル トークンを受け入れるメソッドにする値。  これにより、<xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType>を返すプロパティ`false`、し、それに応じて、呼び出されたメソッドを最適化できます。  テストのためには、トークンが既に取り消された状態か取り消し不可能な状態で開始するかどうかを示すブール値を受け取るコンストラクターを使用してインスタンス化した、事前に取り消されたキャンセル トークンを渡すこともできます。  
  
 この取り消し方法には、いくつか利点があります。  
  
-   同じキャンセル トークンを、任意の数の同期操作および非同期操作に渡すことができます。  
  
-   同じ取り消し要求を、任意の数のリスナーに渡すことができます。  
  
-   取り消しが要求されるかどうか、およびそれがいつ実行されるかは、非同期 API の開発者が完全に制御します。  
  
-   API を使用するコードにより、取り消し要求が反映される非同期呼び出しが選択され、決定されます。  
  
## <a name="monitoring-progress"></a>進行状況の監視  
 一部の非同期メソッドは、非同期メソッドに渡される進行状況インターフェイスを通じて進行状況を公開します。  たとえば、テキスト文字列を非同期的にダウンロードし、その過程で完了したダウンロードの割合を含む進行状況の更新を発生させる関数があるとします。  このようなメソッドは、Windows Presentation Foundation (WPF) アプリケーションでは次のように使用できます。  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)    
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,   
            new Progress<int>(p => pbDownloadProgress.Value = p));  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
<a name="combinators"></a>   
## <a name="using-the-built-in-task-based-combinators"></a>タスク ベースの組み込み連結子の使用  
 <xref:System.Threading.Tasks>名前空間には、作成するタスクを操作するためのいくつかのメソッドが含まれています。  
  
### <a name="taskrun"></a>Task.Run  
 <xref:System.Threading.Tasks.Task>クラスが含まれる<xref:System.Threading.Tasks.Task.Run%2A>簡単にするためのメソッドとしての作業をオフロードする、<xref:System.Threading.Tasks.Task>または<xref:System.Threading.Tasks.Task%601>例については、スレッド プールに。  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    textBox1.Text = await Task.Run(() =>  
    {  
        // … do compute-bound work here  
        return answer;  
    });  
}  
```  
  
 これらのいくつか<xref:System.Threading.Tasks.Task.Run%2A>メソッドなど、<xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>オーバー ロードする、短縮形として存在している、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>メソッドです。  などの他の overloads <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>、たとえばオフロードの作業内 await を使用することで有効にする。  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    pictureBox1.Image = await Task.Run(async() =>  
    {  
        using(Bitmap bmp1 = await DownloadFirstImageAsync())  
        using(Bitmap bmp2 = await DownloadSecondImageAsync())  
        return Mashup(bmp1, bmp2);  
    });  
}  
```  
  
 このようなオーバー ロードを使用してに論理的に等価、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>メソッドと組み合わせて、<xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>タスク並列ライブラリでも拡張メソッド。  
  
### <a name="taskfromresult"></a>Task.FromResult  
 使用して、<xref:System.Threading.Tasks.Task.FromResult%2A>データことが既にある使用可能かつだけのシナリオでメソッドをクラスに退避タスクを返すメソッドから返される必要があります、 <xref:System.Threading.Tasks.Task%601>:  
  
```csharp  
public Task<int> GetValueAsync(string key)  
{  
    int cachedValue;  
    return TryGetCachedValue(out cachedValue) ?  
        Task.FromResult(cachedValue) :  
        GetValueAsyncInternal();  
}  
  
private async Task<int> GetValueAsyncInternal(string key)  
{  
    …  
}  
```  
  
### <a name="taskwhenall"></a>Task.WhenAll  
 使用して、<xref:System.Threading.Tasks.Task.WhenAll%2A>メソッドがタスクとして表される非同期操作を複数の非同期的に待機します。  メソッドには、一連の非ジェネリック タスクまたは不均一な一連のジェネリック タスク (複数の void を返す操作を非同期に待機したり、各値の型が異なる複数の値を返すメソッドを非同期に待機するなど) に加えて、均一な一連のジェネリック タスク (複数の `TResult` を返すメソッドを非同期に待機するなど) をサポートする複数のオーバーロードが含まれます。  
  
 複数の顧客に電子メール メッセージを送信するとします。 このような場合、1 つのメッセージの送信完了を待たずに次のメッセージを送信するような、メッセージのオーバーラップ送信が可能です。 送信操作がいつ完了したか、またエラーが発生したかを確認することもできます。  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 このコードは、例外が発生するが、例外の伝達されることができますを処理しない明示的に、`await`から結果のタスクで<xref:System.Threading.Tasks.Task.WhenAll%2A>です。  例外を処理するには、次のようなコードを使用できます。  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    ...  
}  
```  
  
 この例では、非同期操作が失敗した場合、すべての例外はで統合、<xref:System.AggregateException>に格納されている例外、<xref:System.Threading.Tasks.Task>から返された、<xref:System.Threading.Tasks.Task.WhenAll%2A>メソッドです。  ただし、これらの例外の 1 つだけが `await` キーワードによって反映されます。  すべての例外を調べる場合は、上記のコードを次のように書き直します。  
  
```csharp  
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
 Web から複数のファイルを非同期にダウンロードする例を考えてみます。  この場合、すべての非同期操作の結果の型が同種で、結果に簡単にアクセスできます。  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 前の void を返す場合で説明したのと同じ例外処理手法を使用できます。  
  
```csharp  
Task [] asyncOps =   
    (from url in urls select DownloadStringAsync(url)).ToArray();  
try  
{  
    string [] pages = await Task.WhenAll(asyncOps);  
    ...  
}  
catch(Exception exc)  
{  
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
### <a name="taskwhenany"></a>Task.WhenAny  
 使用することができます、<xref:System.Threading.Tasks.Task.WhenAny%2A>複数の非同期操作の 1 つの非同期的に待機するメソッドが完了するタスクとして表されます。  このメソッドは、次の 4 つの主なユース ケースで役立ちます。  
  
-   冗長性:  1 つの操作を複数回実行し、最初に完了したものを選択する (たとえば、1 つの結果を生成する複数の株価情報 Web サービスに問い合わせて、最も速く完了したものを選択する)。  
  
-   インターリーブ: 複数の操作を起動してそのすべてが完了するのを待機するが、それらの操作を完了時に処理する。  
  
-   調整:  他の操作が完了したら追加の操作を開始できるようにする。  これは、インターリーブのシナリオを拡張したものです。  
  
-   初期の保留: でなどにタスク t1 で表される操作をグループ化することができます、<xref:System.Threading.Tasks.Task.WhenAny%2A>で別のタスク t2 とするタスクが待機できる、<xref:System.Threading.Tasks.Task.WhenAny%2A>タスク。 タスク t2 は、タイムアウト、またはキャンセル、または原因となるその他のいくつかの信号を表すことが、 <xref:System.Threading.Tasks.Task.WhenAny%2A> t1 が完了する前に完了するタスク。  
  
#### <a name="redundancy"></a>冗長性  
 株式を購入するかどうかを決定するとします。  信頼できるいくつかの株式推薦 Web サービスがありますが、日常的な負荷によっては、時に応じて各サービスがかなり遅くなることがあります。  使用することができます、<xref:System.Threading.Tasks.Task.WhenAny%2A>任意の操作が完了したら、通知を受信するメソッド。  
  
```csharp  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol),   
    GetBuyRecommendation2Async(symbol),  
    GetBuyRecommendation3Async(symbol)  
};  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
if (await recommendation) BuyStock(symbol);  
```  
  
 異なり<xref:System.Threading.Tasks.Task.WhenAll%2A>、正常に完了しているすべてのタスクのラップ解除された結果が返されます<xref:System.Threading.Tasks.Task.WhenAny%2A>完了タスクを返します。 タスクが失敗した場合は、それを把握することが重要です。タスクが成功した場合は、戻り値が関連付けられているタスクを把握することが重要です。  そのため、この例で示すように、返されるタスクの結果にアクセスするか、引き続き待機する必要があります。  
  
 同様に<xref:System.Threading.Tasks.Task.WhenAll%2A>例外に対応することができる必要があります。  完了したタスクを受け取るので、適切に `try/catch` で囲んで、エラーが反映されて返されるタスクを待機できます。次に例を示します。  
  
```csharp  
Task<bool> [] recommendations = …;  
while(recommendations.Count > 0)  
{   
    Task<bool> recommendation = await Task.WhenAny(recommendations);      
    try  
    {  
        if (await recommendation) BuyStock(symbol);  
        break;  
    }  
    catch(WebException exc)  
    {  
        recommendations.Remove(recommendation);  
    }  
}  
```  
  
 さらに、最初のタスクが正常に完了しても、以降のタスクが失敗する可能性があります。  この時点では、例外を処理するためのいくつかのオプションがある: 使用する場合、起動されたすべてのタスクが完了するまでに待機することができます、<xref:System.Threading.Tasks.Task.WhenAll%2A>メソッド、またはするは、すべての例外が重要で、ログインする必要があるを決定できます。  そのためには、継続を使用してタスクが非同期に完了した時点で通知を受け取ることができます。  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
```  
  
 または  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
```  
  
 または、以下のように指定できます。  
  
```  
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)  
{  
    foreach(var task in tasks)  
    {  
        try { await task; }  
        catch(Exception exc) { Log(exc); }  
    }  
}  
…  
LogCompletionIfFailed(recommendations);  
```  
  
 最後に、残りのすべての操作を取り消すこともできます。  
  
```csharp  
var cts = new CancellationTokenSource();  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol, cts.Token),   
    GetBuyRecommendation2Async(symbol, cts.Token),  
    GetBuyRecommendation3Async(symbol, cts.Token)  
};  
  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
cts.Cancel();  
if (await recommendation) BuyStock(symbol);  
```  
  
#### <a name="interleaving"></a>インターリーブ  
 Web からイメージをダウンロードして、各イメージを処理するとします (イメージを UI コントロールに追加するなど)。  UI スレッドで順次処理する必要があるとしても、イメージはできるだけ同時にダウンロードすることを考えています。 また、すべてダウンロードされるまで UI へのイメージの追加を保留するのは望ましくないので、ダウンロードが完了した順に追加します。  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
 負荷の高い処理を行うシナリオをインターリーブを適用することも、<xref:System.Threading.ThreadPool>ダウンロードしたイメージの; 例。  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)  
         .ContinueWith(t => ConvertImage(t.Result)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
#### <a name="throttling"></a>調整  
 インターリーブの例ではユーザーが多くのイメージをダウンロードするため、このダウンロード数を絞り込み、たとえば、特定の数のダウンロードだけを同時実行する必要がある場合を考えます。 これを行うには、非同期操作のサブセットを開始します。  操作が完了したら、追加操作を開始して、完了した操作に代えて実行します。  
  
```csharp  
const int CONCURRENCY_LEVEL = 15;  
Uri [] urls = …;  
int nextIndex = 0;  
var imageTasks = new List<Task<Bitmap>>();  
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)  
{  
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
    nextIndex++;  
}  
  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch(Exception exc) { Log(exc); }  
  
    if (nextIndex < urls.Length)  
    {  
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
        nextIndex++;  
    }  
}  
```  
  
#### <a name="early-bailout"></a>初期のエスケープ  
 ユーザーの取り消し要求 (キャンセル ボタンがクリックされたなど) に同時に対応できるようにしながら、1 つの操作の完了を非同期に待機するとします。 このシナリオのコードを次に示します。  
  
```csharp  
private CancellationTokenSource m_cts;   
  
public void btnCancel_Click(object sender, EventArgs e)  
{  
    if (m_cts != null) m_cts.Cancel();  
}  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        if (imageDownload.IsCompleted)  
        {  
            Bitmap image = await imageDownload;  
            panel.AddImage(image);  
        }  
        else imageDownload.ContinueWith(t => Log(t));  
    }  
    finally { btnRun.Enabled = true; }  
}  
  
private static async Task UntilCompletionOrCancellation(  
    Task asyncOp, CancellationToken ct)  
{  
    var tcs = new TaskCompletionSource<bool>();  
    using(ct.Register(() => tcs.TrySetResult(true)))  
        await Task.WhenAny(asyncOp, tcs.Task);  
    return asyncOp;  
}  
```  
  
 この実装は、エスケープを決めた直後にユーザー インターフェイスを再度使用できるようにしますが、基になる非同期操作は取り消しません。  別の方法として、エスケープを決めたときに保留中の操作を取り消すことがありますが、取り消し要求のために途中で終了する場合など、操作が実際に完了するまでユーザー インターフェイスを再確立しません。  
  
```csharp  
private CancellationTokenSource m_cts;  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        Bitmap image = await imageDownload;  
        panel.AddImage(image);  
    }  
    catch(OperationCanceledException) {}  
    finally { btnRun.Enabled = true; }  
}  
```  
  
 初期の保留の別の例を使用して、<xref:System.Threading.Tasks.Task.WhenAny%2A>メソッドと組み合わせて、<xref:System.Threading.Tasks.Task.Delay%2A>メソッドを次のセクションで説明したようにします。  
  
### <a name="taskdelay"></a>Task.Delay  
 使用することができます、<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>を導入するメソッドが非同期メソッドの実行を一時停止します。  これは、ポーリング ループのビルド、あらかじめ指定された期間にわたるユーザー入力処理の遅延など、さまざまな機能に役立ちます。  <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>メソッドにも役立ちますと組み合わせて<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>の待機のタイムアウトを実装します。  
  
 大規模な非同期操作 (ASP.NET Web サービスなど) の一部を構成するタスクが完了するまで時間がかかる場合 (特に操作が完了しない場合) には、操作全般に影響が及びます。  そのため、非同期操作の待機をタイムアウトできるようにすることが重要になります。  同期<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>、 <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>、および<xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType>メソッドが、対応するが、タイムアウト値を受け入れる<xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>前に説明したと<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>メソッドがありません。  使用する代わりに、<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>と<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>を組み合わせると、タイムアウトを実装します。  
  
 たとえば、UI アプリケーションで、イメージをダウンロードし、そのダウンロード中は UI を無効にするとします。 ただし、ダウンロードに時間がかかりすぎる場合には、UI を再び有効にしてダウンロードを破棄します。  
  
```csharp  
public async void btnDownload_Click(object sender, EventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap> download = GetBitmapAsync(url);  
        if (download == await Task.WhenAny(download, Task.Delay(3000)))  
        {  
            Bitmap bmp = await download;  
            pictureBox.Image = bmp;  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            pictureBox.Image = null;  
            status.Text = "Timed out";  
            var ignored = download.ContinueWith(  
                t => Trace("Task finally completed"));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
 同じに適用される複数のダウンロードのため<xref:System.Threading.Tasks.Task.WhenAll%2A>タスクを返します。  
  
```csharp  
public async void btnDownload_Click(object sender, RoutedEventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap[]> downloads =   
            Task.WhenAll(from url in urls select GetBitmapAsync(url));  
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))  
        {  
            foreach(var bmp in downloads) panel.AddImage(bmp);  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            status.Text = "Timed out";  
            downloads.ContinueWith(t => Log(t));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
## <a name="building-task-based-combinators"></a>タスク ベースの連結子のビルド  
 タスクは、非同期操作を完全に表現し、操作の結合、その結果の取得などの同期機能と非同期機能を提供することができるため、大きなパターンをビルドするためのタスクを構成する有益な連結子ライブラリを構築できるようになります。  前のセクションで説明したように、.NET Framework には、いくつかの組み込み連結子が用意されていますが、独自にビルドすることもできます。 以下のセクションでは、有効な連結子メソッドと型の例をいくつか示します。  
  
### <a name="retryonfault"></a>RetryOnFault  
 多くの状況では、前の操作が失敗した場合に再試行することが望まれます。  同期コードの場合は、次の例のように `RetryOnFault` などのヘルパー メソッドをビルドしてこれを行うことができます。  
  
```csharp  
public static T RetryOnFault<T>(  
    Func<T> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return function(); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 非同期操作の場合も、ほとんど同じヘルパー メソッドをビルドでき、TAP を使用して非同期操作を実装し、タスクを返します。  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 次のように、この連結子を使用してアプリケーションのロジックに再試行をエンコードできます。  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 `RetryOnFault` 関数をさらに拡張できます。 たとえば、この関数は別の `Func<Task>` を受け取り、次のように再試行のタイミングを判断するために、再試行の間に呼び出されます。  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
        await retryWhen().ConfigureAwait(false);  
    }  
    return default(T);  
}  
```  
  
 次の関数を使用して、操作を再試行する前に 1 秒待機するようにできます。  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 操作の待機時間と成功の確率を改善するために、冗長性を活用できる場合があります。  株価情報を提供する複数の Web サービスがあるとします。しかし、時間によって、各サービスの品質レベルと応答時間が変化します。  この変動に対応するには、すべての Web サービスに要求を出し、最初の応答を取得した時点で残りの要求を取り消します。  複数の操作を起動し、応答を待機し、残りの操作を取り消すというこの一般的なパターンの実装は、ヘルパー関数を実装して簡略化できます。 次の例の `NeedOnlyOne` 関数は、このシナリオを示します。  
  
```csharp  
public static async Task<T> NeedOnlyOne(  
    params Func<CancellationToken,Task<T>> [] functions)  
{  
    var cts = new CancellationTokenSource();  
    var tasks = (from function in functions  
                 select function(cts.Token)).ToArray();  
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);  
    cts.Cancel();  
    foreach(var task in tasks)   
    {  
        var ignored = task.ContinueWith(  
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);  
    }  
    return completed;  
}  
```  
  
 この関数は次のように使用できます。  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a>インターリーブされた操作  
 使用して潜在的なパフォーマンスの問題がある、<xref:System.Threading.Tasks.Task.WhenAny%2A>タスクの非常に大きなセットを使用している場合、インターリーブのシナリオをサポートするメソッド。  すべての呼び出しに<xref:System.Threading.Tasks.Task.WhenAny%2A>登録されると、各タスクの継続で発生します。 タスクの数を N とすると、インターリーブ操作の有効期間に作成された O (N2) の継続になります。  多数のタスクを使用する場合は、連結子 (次の例の `Interleaved`) を使用してパフォーマンスの問題に対処できます。  
  
```csharp  
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputTasks = tasks.ToList();  
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)   
                   select new TaskCompletionSource<T>()).ToList();  
    int nextTaskIndex = -1;  
    foreach (var inputTask in inputTasks)  
    {  
        inputTask.ContinueWith(completed =>  
        {  
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];  
            if (completed.IsFaulted)   
                source.TrySetException(completed.Exception.InnerExceptions);  
            else if (completed.IsCanceled)   
                source.TrySetCanceled();  
            else   
                source.TrySetResult(completed.Result);  
        }, CancellationToken.None,   
           TaskContinuationOptions.ExecuteSynchronously,   
           TaskScheduler.Default);  
    }  
    return from source in sources   
           select source.Task;  
}  
```  
  
 タスクが完了すると、たとえば次のように、連結子を使用してタスクの結果を処理できます。  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 特定のスキャッター/ギャザー シナリオでは、すべてのタスクの完了を待機することが考えられますが、そのうちの 1 つがエラーになった場合には、例外の発生時点で待機を停止することが望まれます。  これは、次の例の `WhenAllOrFirstException` などの連結子メソッドを使用して実行できます。  
  
```csharp  
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputs = tasks.ToList();  
    var ce = new CountdownEvent(inputs.Count);  
    var tcs = new TaskCompletionSource<T[]>();  
  
    Action<Task> onCompleted = (Task completed) =>  
    {  
        if (completed.IsFaulted)   
            tcs.TrySetException(completed.Exception.InnerExceptions);  
        if (ce.Signal() && !tcs.Task.IsCompleted)  
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());  
    };  
  
    foreach (var t in inputs) t.ContinueWith(onCompleted);  
    return tcs.Task;  
}  
```  
  
## <a name="building-task-based-data-structures"></a>タスク ベースのデータ構造のビルド  
 データ構造を持つできるだけでなく、カスタムのタスク ベースの連結子を構築する、<xref:System.Threading.Tasks.Task>と<xref:System.Threading.Tasks.Task%601>非同期操作の両方の結果を表すし、それに参加するために必要な同期では、非常に強力な非同期のシナリオで使用するカスタム データ構造を構築するために入力します。  
  
### <a name="asynccache"></a>AsyncCache  
 その結果または例外を取得 1 つのタスクの重要な側面は、そのことがあります配ることで、登録継続 await の可能性があります、複数のコンシューマーに (の場合、 <xref:System.Threading.Tasks.Task%601>) のようにします。  これにより、<xref:System.Threading.Tasks.Task>と<xref:System.Threading.Tasks.Task%601>非同期キャッシュ インフラストラクチャで使用するのには最適です。  小規模の例を次に示しますが、強力な非同期キャッシュの上に構築<xref:System.Threading.Tasks.Task%601>:  
  
```csharp  
public class AsyncCache<TKey, TValue>  
{  
    private readonly Func<TKey, Task<TValue>> _valueFactory;  
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;  
  
    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)  
    {  
        if (valueFactory == null) throw new ArgumentNullException("loader");  
        _valueFactory = valueFactory;  
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();  
    }  
  
    public Task<TValue> this[TKey key]  
    {  
        get  
        {  
            if (key == null) throw new ArgumentNullException("key");  
            return _map.GetOrAdd(key, toAdd =>   
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;  
        }  
    }  
}  
```  
  
 [AsyncCache\<TKey, TValue >](http://go.microsoft.com/fwlink/p/?LinkId=251941)を受け取る関数、クラス、コンス トラクターにデリゲートを受け入れる、`TKey`を返します、<xref:System.Threading.Tasks.Task%601>です。  以前にキャッシュからアクセスした値は内部ディクショナリに格納され、`AsyncCache` によって、キャッシュに同時にアクセスしてもキーごとにタスクが 1 つしか生成されないようにします。  
  
 たとえば、次のようにダウンロードされた Web ページのキャッシュをビルドできます。  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Web ページのコンテンツが必要なときはいつでも、非同期メソッドでこのキャッシュを使用できます。 `AsyncCache` クラスは、できるだけ少ない数のページがダウンロードされるようにして、結果をキャッシュします。  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection  
 タスクは、非同期アクティビティを調整するためのデータ構造のビルドにも使用できます。  プロデューサー/コンシューマーというクラシックな並列設計パターンの 1 つについて考えてみます。  このパターンでは、コンシューマーによって使用されるデータをプロデューサーが生成し、プロデューサーおよびコンシューマーは並列に実行できます。 たとえば、コンシューマーは、項目 2 を生成中のプロデューサーが以前に生成した項目 1 を処理します。  プロデューサー/コンシューマー パターンでは、新しいデータについてコンシューマーに通知され、そのデータが使用可能な場合にコンシューマーが見つけられるように、プロデューサーが作成した作業を格納するデータ構造が必ず必要です。  
  
 プロデューサーおよびコンシューマーとして使用する非同期メソッドを有効にするタスク上にビルドされた単純なデータ構造を次に示します。  
  
```csharp  
public class AsyncProducerConsumerCollection<T>  
{  
    private readonly Queue<T> m_collection = new Queue<T>();  
    private readonly Queue<TaskCompletionSource<T>> m_waiting =   
        new Queue<TaskCompletionSource<T>>();  
  
    public void Add(T item)  
    {  
        TaskCompletionSource<T> tcs = null;  
        lock (m_collection)  
        {  
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();  
            else m_collection.Enqueue(item);  
        }  
        if (tcs != null) tcs.TrySetResult(item);  
    }  
  
    public Task<T> Take()  
    {  
        lock (m_collection)  
        {  
            if (m_collection.Count > 0)   
            {  
                return Task.FromResult(m_collection.Dequeue());   
            }  
            else   
            {  
                var tcs = new TaskCompletionSource<T>();  
                m_waiting.Enqueue(tcs);  
                return tcs.Task;  
            }  
        }  
    }  
}  
```  
  
 このデータ構造を使用すると、次のようなコードを作成できます。  
  
```csharp  
private static AsyncProducerConsumerCollection<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.Take();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Add(data);  
}  
```  
  
 <xref:System.Threading.Tasks.Dataflow>名前空間が含まれています、<xref:System.Threading.Tasks.Dataflow.BufferBlock%601>型で、カスタム コレクション型を構築する必要はありませんが、同様の方法で行うこともできます。  
  
```csharp  
private static BufferBlock<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.ReceiveAsync();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Post(data);  
}  
```  
  
> [!NOTE]
>  <xref:System.Threading.Tasks.Dataflow>名前空間で使用できる、[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]を通じて**NuGet**です。 含むアセンブリをインストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**から、[プロジェクト] メニューのし、Microsoft.Tpl.Dataflow パッケージをオンライン検索します。  
  
## <a name="see-also"></a>関連項目  
 [タスク ベースの非同期パターン (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [タスク ベースの非同期パターンの実装](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [他の非同期パターンと型との相互運用](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
