---
title: F# で非同期のプログラミング
description: 言語レベルのプログラミング モデルを使いやすく、自然言語を使用して非同期 f# のプログラミングを実現する方法について説明します。
keywords: .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: c3fde46e804b7acac78d3ce5454a3c6f806e24e7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="async-programming-in-f"></a><span data-ttu-id="bf952-104">F# で非同期のプログラミング</span><span class="sxs-lookup"><span data-stu-id="bf952-104">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="bf952-105">この記事には、いくつかに関する誤りの修正が検出されました。</span><span class="sxs-lookup"><span data-stu-id="bf952-105">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="bf952-106">これが書き込まれています。</span><span class="sxs-lookup"><span data-stu-id="bf952-106">It is being rewritten.</span></span>  <span data-ttu-id="bf952-107">参照してください[問題 #666](https://github.com/dotnet/docs/issues/666)への変更点について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf952-107">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="bf952-108">言語レベルのプログラミング モデルが使いやすく、自然言語にするように設計では、非同期 f# のプログラミングを実現できます。</span><span class="sxs-lookup"><span data-stu-id="bf952-108">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="bf952-109">非同期プログラミングの f# のコアは`Async<'T>`、バック グラウンドで実行する起動可能な作業の表現を`'T`特別なを介して、いずれかの型が返されます`return`キーワードまたは`unit`非同期ワークフローがあるない場合返される結果。</span><span class="sxs-lookup"><span data-stu-id="bf952-109">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="bf952-110">主要概念を理解するは非同期式の種類がある`Async<'T>`、これはだけで、_仕様_の非同期のコンテキストで実行する作業をします。</span><span class="sxs-lookup"><span data-stu-id="bf952-110">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="bf952-111">開始の関数のいずれかに明示的に開始されるまでは実行されません (など`Async.RunSynchronously`)。</span><span class="sxs-lookup"><span data-stu-id="bf952-111">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="bf952-112">作業を行って考えたの別の方法ですが、実際には非常にシンプルされていることを終了します。</span><span class="sxs-lookup"><span data-stu-id="bf952-112">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="bf952-113">たとえば、メイン スレッドをブロックすることがなく dotnetfoundation.org から HTML をダウンロードしたいとします。</span><span class="sxs-lookup"><span data-stu-id="bf952-113">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="bf952-114">次のように、これを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="bf952-114">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="bf952-115">以上です。</span><span class="sxs-lookup"><span data-stu-id="bf952-115">And that’s it!</span></span> <span data-ttu-id="bf952-116">使用する場合を除いて`async`、 `let!`、および`return`、これは、単に通常の f# コード。</span><span class="sxs-lookup"><span data-stu-id="bf952-116">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="bf952-117">注目すべきである、いくつかの構文構造があります。</span><span class="sxs-lookup"><span data-stu-id="bf952-117">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="bf952-118">`let!` (を実行する別のコンテキストで) 非同期式の結果にバインドします。</span><span class="sxs-lookup"><span data-stu-id="bf952-118">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="bf952-119">`use!` 同様に動作します`let!`がスコープ外になったときにバインドされているリソースを破棄します。</span><span class="sxs-lookup"><span data-stu-id="bf952-119">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="bf952-120">`do!` 何も返さない非同期ワークフローが待機されます。</span><span class="sxs-lookup"><span data-stu-id="bf952-120">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="bf952-121">`return` 単に非同期式から結果を返します。</span><span class="sxs-lookup"><span data-stu-id="bf952-121">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="bf952-122">`return!` 別の非同期ワークフローを実行し、その戻り値をその結果を返します。</span><span class="sxs-lookup"><span data-stu-id="bf952-122">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="bf952-123">さらに、通常`let`、 `use`、および`do`キーワードは、通常の関数と同様、非同期バージョンと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf952-123">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="bf952-124">F# で非同期コードを起動する方法</span><span class="sxs-lookup"><span data-stu-id="bf952-124">How to start Async Code in F#</span></span> #

<span data-ttu-id="bf952-125">前述のように、非同期コードは、明示的に開始する必要がある別のコンテキストで実行する作業の仕様です。</span><span class="sxs-lookup"><span data-stu-id="bf952-125">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="bf952-126">これを実現する 2 つの主な方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bf952-126">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="bf952-127">`Async.RunSynchronously` 別のスレッドで非同期ワークフローを開始し、その結果を待機します。</span><span class="sxs-lookup"><span data-stu-id="bf952-127">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="bf952-128">`Async.Start` 別のスレッドで非同期ワークフローの開始し、は、**いない**結果を待機します。</span><span class="sxs-lookup"><span data-stu-id="bf952-128">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="bf952-129">具体的なシナリオに使用できる非同期ワークフローを開始するには、その他の方法はあります。</span><span class="sxs-lookup"><span data-stu-id="bf952-129">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="bf952-130">詳細については[Async リファレンス](https://msdn.microsoft.com/library/ee370232.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="bf952-130">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="bf952-131">スレッドに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="bf952-131">A Note on Threads</span></span>

<span data-ttu-id="bf952-132">"に別のスレッド"という語句が上記ことを知っておく重要な**非同期のワークフローがのファサードであるわけではないマルチ スレッド**です。</span><span class="sxs-lookup"><span data-stu-id="bf952-132">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="bf952-133">ワークフロー実際に「移動」を実際の作業を行うには時間の少量の借用して、スレッド間でします。</span><span class="sxs-lookup"><span data-stu-id="bf952-133">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="bf952-134">非同期ワークフロー待っているときに効果的に""(この例では、値を返すためのネットワーク呼び出しの待機)、他のオブジェクトに有効な作業を移動しないでくださいまで時点で借りてが、任意のスレッドは解放されます。</span><span class="sxs-lookup"><span data-stu-id="bf952-134">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="bf952-135">これにより、非同期のワークフローで、できるだけ効率的に実行されるシステムを利用され、大量の I/O シナリオで特に強力なをようになります。</span><span class="sxs-lookup"><span data-stu-id="bf952-135">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="bf952-136">非同期コードを並列処理を追加する方法</span><span class="sxs-lookup"><span data-stu-id="bf952-136">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="bf952-137">場合があります可能性があり、必要とする並列で複数の非同期ジョブを実行する、その結果を収集する何らかの方法で解釈します。</span><span class="sxs-lookup"><span data-stu-id="bf952-137">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="bf952-138">`Async.Parallel` これが行われます。 強制的に変換する必要があるタスク並列ライブラリを使用することなく実行できる`Task<'T>`と`Async<'T>`型です。</span><span class="sxs-lookup"><span data-stu-id="bf952-138">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="bf952-139">次の例を使用して`Async.Parallel`ダウンロードする HTML 並列で 4 つの人気のあるサイトからこれらのタスクを完了するまで待機し、ダウンロードされた、HTML を印刷します。</span><span class="sxs-lookup"><span data-stu-id="bf952-139">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="bf952-140">重要な情報とアドバイス</span><span class="sxs-lookup"><span data-stu-id="bf952-140">Important Info and Advice</span></span>

*   <span data-ttu-id="bf952-141">すべての関数の使用を最後に"Async"を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf952-141">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="bf952-142">これは、名前付け規則だけが、これは API の探索可能性などやすくするためです。</span><span class="sxs-lookup"><span data-stu-id="bf952-142">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="bf952-143">同じルーチンの同期および非同期のバージョンがある場合に特には、これは、名前を使用して非同期を明示的に記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bf952-143">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="bf952-144">コンパイラにリッスンします。</span><span class="sxs-lookup"><span data-stu-id="bf952-144">Listen to the compiler!</span></span>

 <span data-ttu-id="bf952-145"># のコンパイラは非常に厳格な処理を行うことがほぼ不可能になります troubling と同様に実行"async"コード同期的にします。</span><span class="sxs-lookup"><span data-stu-id="bf952-145">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="bf952-146">警告に遭遇した場合はそれを検討する方法にコードが実行されない記号です。</span><span class="sxs-lookup"><span data-stu-id="bf952-146">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="bf952-147">コンパイラを満足することができますと、ほとんどの場合に、コードは、期待どおりに実行されます。</span><span class="sxs-lookup"><span data-stu-id="bf952-147">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="bf952-148">F# に C #/vb プログラマにとって</span><span class="sxs-lookup"><span data-stu-id="bf952-148">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="bf952-149">このセクションでは、c# での非同期モデルに慣れているものと/vb です。</span><span class="sxs-lookup"><span data-stu-id="bf952-149">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="bf952-150">いない場合、 [c# での非同期プログラミング](../../../csharp/async.md)開始ポイントです。</span><span class="sxs-lookup"><span data-stu-id="bf952-150">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="bf952-151">C #/vb の非同期モデルと f# の非同期モデルの間の基本的な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="bf952-151">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="bf952-152">返す関数を呼び出すときに、`Task`または`Task<'T>`、そのジョブがすでに実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="bf952-152">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="bf952-153">返されたハンドルは、既に実行中の非同期ジョブを表します。</span><span class="sxs-lookup"><span data-stu-id="bf952-153">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="bf952-154">これに対し、f# で非同期関数を呼び出す場合、`Async<'a>`返されるとなるジョブを表す**生成**いくつかの時点です。</span><span class="sxs-lookup"><span data-stu-id="bf952-154">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="bf952-155">F# で非同期のジョブを連結できるために強力ですが、このモデルを理解することが容易に条件付きで実行され、細かくコントロールの使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="bf952-155">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="bf952-156">その他のいくつかの類似点と相違点も注目すべきがあります。</span><span class="sxs-lookup"><span data-stu-id="bf952-156">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="bf952-157">類似点</span><span class="sxs-lookup"><span data-stu-id="bf952-157">Similarities</span></span>

*   <span data-ttu-id="bf952-158">`let!`、 `use!`、および`do!`に似ています`await`内から非同期ジョブを呼び出すときに、`async{ }`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="bf952-158">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="bf952-159">次の 3 つのキーワードは内でのみ使用できます、`async { }`ブロック、方法と似ています`await`内のみ呼び出すことができます、`async`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bf952-159">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="bf952-160">つまり、`let!`をキャプチャして、結果を使用する場合は`use!`同じが、何かのリソースが使用すると、後にクリーンアップする必要がありますと`do!`非同期のワークフローが終了する戻り値はありませんが待機する場合に続行する前にします。</span><span class="sxs-lookup"><span data-stu-id="bf952-160">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="bf952-161">F# で同様の方法でデータを並列化をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="bf952-161">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="bf952-162">まったく違う方法で動作が`Async.Parallel`に対応する`Task.WhenAll`シナリオでは、すべてが完了したときに、一連の非同期ジョブの結果をしたいのです。</span><span class="sxs-lookup"><span data-stu-id="bf952-162">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="bf952-163">相違点</span><span class="sxs-lookup"><span data-stu-id="bf952-163">Differences</span></span>

*   <span data-ttu-id="bf952-164">入れ子になった`let!`は使用できませんとは異なり、入れ子になった `await`</span><span class="sxs-lookup"><span data-stu-id="bf952-164">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="bf952-165">異なり`await`が無期限に、入れ子にすることができます`let!`ことはできませんし、その結果を別の内部で使用する前にバインドされている必要があります`let!`、 `do!`、または`use!`です。</span><span class="sxs-lookup"><span data-stu-id="bf952-165">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="bf952-166">キャンセルのサポートは単純な f# と c#/vb です。</span><span class="sxs-lookup"><span data-stu-id="bf952-166">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="bf952-167">C #/vb を実行して、タスクの中間にあるの取り消しをサポートする場合は、チェックする必要があります、`IsCancellationRequested`プロパティまたは呼び出す`ThrowIfCancellationRequested()`上、`CancellationToken`は async メソッドに渡されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bf952-167">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="bf952-168">これに対し、F# で非同期ワークフローより自然取り消し可能になりません。</span><span class="sxs-lookup"><span data-stu-id="bf952-168">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="bf952-169">キャンセルは、単純な 3 段階のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="bf952-169">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="bf952-170">新規の `CancellationTokenSource` を作成します。</span><span class="sxs-lookup"><span data-stu-id="bf952-170">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="bf952-171">開始の関数に渡します。</span><span class="sxs-lookup"><span data-stu-id="bf952-171">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="bf952-172">呼び出す`Cancel`トークンにします。</span><span class="sxs-lookup"><span data-stu-id="bf952-172">Call `Cancel` on the token.</span></span>

<span data-ttu-id="bf952-173">例:</span><span class="sxs-lookup"><span data-stu-id="bf952-173">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="bf952-174">以上です。</span><span class="sxs-lookup"><span data-stu-id="bf952-174">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="bf952-175">他のリソースについて:</span><span class="sxs-lookup"><span data-stu-id="bf952-175">Further resources:</span></span>

*   [<span data-ttu-id="bf952-176">MSDN の非同期ワークフロー</span><span class="sxs-lookup"><span data-stu-id="bf952-176">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="bf952-177">F# の非同期のシーケンス</span><span class="sxs-lookup"><span data-stu-id="bf952-177">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="bf952-178">F# データ HTTP ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="bf952-178">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
