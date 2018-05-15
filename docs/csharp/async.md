---
title: 非同期プログラミング
description: .NET Core で提供される、C# 言語レベルの非同期プログラミング モデルについて説明します。
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 22a63ab55ba7f7888973f08ebdb3cbc149d6ac57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-programming"></a><span data-ttu-id="a54db-103">非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="a54db-103">Asynchronous programming</span></span>

<span data-ttu-id="a54db-104">I/O バインドのニーズ (ネットワークからのデータの要求、データベースへのアクセスなど) がある場合、非同期プログラミングを利用することになります。</span><span class="sxs-lookup"><span data-stu-id="a54db-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="a54db-105">CPU バインドのコードにも、コストのかかる計算の実行など、非同期コードに適したシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="a54db-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="a54db-106">C# は言語レベルで非同期プログラミング モデルを備えており、コールバックに苦労したり、非同期処理をサポートするライブラリに従ったりしなくても、非同期コードを簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="a54db-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="a54db-107">C# は、[タスク ベースの非同期パターン (TAP)](https://msdn.microsoft.com/library/hh873175.aspx) と呼ばれるものに従います。</span><span class="sxs-lookup"><span data-stu-id="a54db-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="a54db-108">非同期モデルの基本的な概要</span><span class="sxs-lookup"><span data-stu-id="a54db-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="a54db-109">非同期プログラミングの中心になるのは `Task` オブジェクトと `Task<T>` オブジェクトであり、非同期操作をモデル化します。</span><span class="sxs-lookup"><span data-stu-id="a54db-109">The core of async programming are the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="a54db-110">これらは、`async` および `await` キーワードによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a54db-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="a54db-111">ほとんどの場合、モデルは非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="a54db-111">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="a54db-112">I/O バインドのコードでは、`async` メソッドの内部で `Task` または `Task<T>` を返す操作を待機 (`await`) します。</span><span class="sxs-lookup"><span data-stu-id="a54db-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="a54db-113">CPU バインドのコードでは、`Task.Run` メソッドによってバックグラウンド スレッドで開始された操作を待機 (`await`) します。</span><span class="sxs-lookup"><span data-stu-id="a54db-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="a54db-114">`await` キーワードはマジックが行われる場所であり、</span><span class="sxs-lookup"><span data-stu-id="a54db-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="a54db-115">`await` を実行したメソッドの呼び出し元に制御が委譲されます。これによって最終的に、UI は応答できるようになり、サービスは柔軟性を持つようになります。</span><span class="sxs-lookup"><span data-stu-id="a54db-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="a54db-116">上でリンクされている TAP の記事で説明されているように `async` と `await` 以外にも非同期コードへのアプローチはありますが、このドキュメントではこれ以降、言語レベルの構造に注目します。</span><span class="sxs-lookup"><span data-stu-id="a54db-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="a54db-117">I/O バインドの例: Web サービスからのデータのダウンロード</span><span class="sxs-lookup"><span data-stu-id="a54db-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="a54db-118">ボタンがクリックされたら Web サービスからデータをダウンロードする必要がありますが UI スレッドはブロックしたくない、といった場合があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="a54db-119">これは、次のように簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="a54db-119">It can be accomplished simply like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="a54db-120">以上です。</span><span class="sxs-lookup"><span data-stu-id="a54db-120">And that’s it!</span></span> <span data-ttu-id="a54db-121">コードでは、Task オブジェクトとの対話に煩わされることなく意図すること (データを非同期的にダウンロードする) が表されています。</span><span class="sxs-lookup"><span data-stu-id="a54db-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="a54db-122">CPU バインドの例: ゲームの計算を実行する</span><span class="sxs-lookup"><span data-stu-id="a54db-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="a54db-123">ボタンをクリックすると画面上の多くの敵にダメージを与えることができるモバイル ゲームを作っています。</span><span class="sxs-lookup"><span data-stu-id="a54db-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="a54db-124">ダメージ計算の実行は負荷が大きく、UI スレッドで実行すると計算の実行中はゲームが停止しているように見えます。</span><span class="sxs-lookup"><span data-stu-id="a54db-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="a54db-125">これを処理する最善の方法は、バックグラウンド スレッドを開始し、その中で `Task.Run` を使って処理を実行して、結果を `await` することです。</span><span class="sxs-lookup"><span data-stu-id="a54db-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="a54db-126">このようにすると、処理が行われている間も UI が停止することはありません。</span><span class="sxs-lookup"><span data-stu-id="a54db-126">This will allow the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}


calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="a54db-127">以上です。</span><span class="sxs-lookup"><span data-stu-id="a54db-127">And that's it!</span></span>  <span data-ttu-id="a54db-128">このコードでは、ボタンのクリック イベントの意図が明瞭に表されています。バックグラウンド スレッドを手動で管理する必要はなく、ブロッキングが発生しない方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="a54db-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="a54db-129">内部での処理</span><span class="sxs-lookup"><span data-stu-id="a54db-129">What happens under the covers</span></span>

<span data-ttu-id="a54db-130">非同期操作には多数の動作要素が関係します。</span><span class="sxs-lookup"><span data-stu-id="a54db-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="a54db-131">`Task` と `Task<T>` の内部処理について詳しくは、「[非同期の詳細](../standard/async-in-depth.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a54db-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="a54db-132">C# 側では、コンパイラはコードをステート マシンに変換します。ステート マシンは、`await` に達したときの実行の委譲や、バックグラウンド ジョブが終了したときの実行の再開などを追跡します。</span><span class="sxs-lookup"><span data-stu-id="a54db-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="a54db-133">理論的には、これは[非同期処理の約束モデル](https://en.wikipedia.org/wiki/Futures_and_promises)の実装です。</span><span class="sxs-lookup"><span data-stu-id="a54db-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="a54db-134">理解すべき重要事項</span><span class="sxs-lookup"><span data-stu-id="a54db-134">Key Pieces to Understand</span></span>

*   <span data-ttu-id="a54db-135">非同期コードは I/O バインドと CPU バインドの両方のコードで使うことができますが、使い方はシナリオにより異なります。</span><span class="sxs-lookup"><span data-stu-id="a54db-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="a54db-136">非同期コードで使われる `Task<T>` と `Task` は、バックグラウンドで行われる処理のモデル化に使われる構成要素です。</span><span class="sxs-lookup"><span data-stu-id="a54db-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="a54db-137">キーワード `async` はメソッドを非同期メソッドに変換し、メソッドの本体で `await` キーワードを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a54db-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="a54db-138">適用された `await` キーワードは、呼び出しメソッドを中断し、待機中のタスクが完了するまで呼び出し元に制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="a54db-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="a54db-139">`await` は、非同期メソッドの中でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a54db-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="a54db-140">CPU バインドと I/O バインドの処理</span><span class="sxs-lookup"><span data-stu-id="a54db-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="a54db-141">このガイドの最初の 2 つの例では、CPU バインドと I/O バインドの処理に対して `async` および `await` を使う方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="a54db-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="a54db-142">行う必要のあるジョブが I/O バインドか CPU バインドかを識別できることが重要です。これは、コードのパフォーマンスに大きく影響し、特定の構成の誤った使用につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="a54db-143">コードを記述する前に次の 2 点について考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="a54db-144">コードは何か (データベースのデータなど) を "待機" していますか。</span><span class="sxs-lookup"><span data-stu-id="a54db-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="a54db-145">答えが "はい" の場合、その処理は **I/O バインド**です。</span><span class="sxs-lookup"><span data-stu-id="a54db-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="a54db-146">コードは、非常に負荷の大きい計算を実行しますか。</span><span class="sxs-lookup"><span data-stu-id="a54db-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="a54db-147">答えが "はい" の場合、その処理は **CPU バインド**です。</span><span class="sxs-lookup"><span data-stu-id="a54db-147">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="a54db-148">処理が **I/O バインド**の場合は、`async` と `await` を使いますが、`Task.Run` は "*使いません*"。</span><span class="sxs-lookup"><span data-stu-id="a54db-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="a54db-149">タスク並列ライブラリは "*使わないでください*"。</span><span class="sxs-lookup"><span data-stu-id="a54db-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="a54db-150">その理由について詳しくは、「[非同期の詳細](../standard/async-in-depth.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a54db-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="a54db-151">処理が **CPU バインド**であり、応答性が重要な場合は、`async` と `await` を使い、`Task.Run` を "*使って*" 別のスレッドで処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="a54db-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="a54db-152">処理が同時実行と並列処理に適している場合は、タスク並列ライブラリを使うことも考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-152">If the work is appropriate for concurrency and parallelism, you should also consider using the Task Parallel Library.</span></span>

<span data-ttu-id="a54db-153">さらに、常にコードの実行を測定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="a54db-154">たとえば、マルチスレッドでのコンテキスト切り替えのオーバーヘッドと比較して、CPU バインドの処理の負荷がそれほど大きくないことがわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="a54db-155">すべての選択肢にはトレードオフがあり、状況に合った適切なトレードオフを選ぶ必要があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="a54db-156">その他の例</span><span class="sxs-lookup"><span data-stu-id="a54db-156">More Examples</span></span>

<span data-ttu-id="a54db-157">以下では、C# で非同期コードを記述するさまざまな方法がわかる例を示します。</span><span class="sxs-lookup"><span data-stu-id="a54db-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="a54db-158">実際に遭遇する可能性があるいくつかの異なるシナリオを使います。</span><span class="sxs-lookup"><span data-stu-id="a54db-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="a54db-159">ネットワークからのデータの抽出</span><span class="sxs-lookup"><span data-stu-id="a54db-159">Extracting Data from a Network</span></span>

<span data-ttu-id="a54db-160">このスニペットは、www.dotnetfoundation.org から HTML をダウンロードし、HTML に文字列 ".NET" が出現する回数を数えます。</span><span class="sxs-lookup"><span data-stu-id="a54db-160">This snippet downloads the HTML from www.dotnetfoundation.org and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="a54db-161">ASP.NET MVC を使って定義されている Web コントローラー メソッドが、このタスクを実行して、数を返します。</span><span class="sxs-lookup"><span data-stu-id="a54db-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="a54db-162">運用コードで HTML の解析の実行を計画している場合は、正規表現を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="a54db-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="a54db-163">代わりに解析ライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="a54db-163">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.DownloadStringAsync("http://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="a54db-164">次に示すのはユニバーサル Windows アプリ用に記述された同じシナリオであり、ボタンがクリックされたら同じタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="a54db-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("http://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="a54db-165">複数タスクの完了の待機</span><span class="sxs-lookup"><span data-stu-id="a54db-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="a54db-166">複数のデータを同時に取得することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="a54db-167">`Task` API には 2 つのメソッド `Task.WhenAll` と `Task.WhenAny` が含まれており、これらを使用して、複数のバックグラウンド ジョブで非ブロッキング待機を実行する非同期コードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="a54db-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="a54db-168">次の例では、一連の `userId` に対する `User` データを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a54db-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }
    
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="a54db-169">LINQ を使ってもう少し簡潔に記述する別の方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a54db-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```
<span data-ttu-id="a54db-170">コードは少ないですが、LINQ と非同期コードを併用するときは注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="a54db-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="a54db-171">LINQ は遅延実行を使うので、生成されたシーケンスを `.ToList()` または `.ToArray()` の呼び出しで強制的に反復処理させない限り、`foreach()` ループ内で行われた非同期呼び出しはすぐに実行されません。</span><span class="sxs-lookup"><span data-stu-id="a54db-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="a54db-172">重要な情報とアドバイス</span><span class="sxs-lookup"><span data-stu-id="a54db-172">Important Info and Advice</span></span>

<span data-ttu-id="a54db-173">非同期プログラミングはそれほど難しくありませんが、留意することで予期しない動作を防ぐことができる細かい事柄がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a54db-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="a54db-174">`async` **メソッドの本体に** `await` **キーワードが含まれないと、何も行われません**</span><span class="sxs-lookup"><span data-stu-id="a54db-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="a54db-175">これは、忘れてはならない重要なことです。</span><span class="sxs-lookup"><span data-stu-id="a54db-175">This is important to keep in mind.</span></span>  <span data-ttu-id="a54db-176">`await` が `async` メソッドの本体で使われていない場合、C# コンパイラは警告を生成しますが、コードは通常のメソッドと同様にコンパイルされて実行されます。</span><span class="sxs-lookup"><span data-stu-id="a54db-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="a54db-177">また、非同期メソッドに対して C# コンパイラが生成するステート マシンは何も行わないので、非常に非効率的であることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="a54db-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="a54db-178">**記述するすべての非同期メソッド名のサフィックスとして、"Async" を追加する必要があります**</span><span class="sxs-lookup"><span data-stu-id="a54db-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="a54db-179">これは、同期メソッドと非同期メソッドの区別をより簡単にするために、.NET で使われる規則です。</span><span class="sxs-lookup"><span data-stu-id="a54db-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="a54db-180">コードによって明示的に呼び出されない一部のメソッド (イベント ハンドラーや Web コントローラー メソッドなど) には必ずしも当てはまらないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a54db-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="a54db-181">そのようなメソッドはコードでは明示的に呼び出されないため、明示的な命名はそれほど重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="a54db-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="a54db-182">`async void` **はイベント ハンドラーに対してのみ使う必要があります**</span><span class="sxs-lookup"><span data-stu-id="a54db-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="a54db-183">イベントには戻り値の型がないため、`async void` は非同期イベント ハンドラーの動作を可能にする唯一の方法です (したがって、`Task` と `Task<T>` を使うことはできません)。</span><span class="sxs-lookup"><span data-stu-id="a54db-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="a54db-184">`async void` のその他の使用はすべて TAP モデルに従わないので、使うのが難しい場合があります。以下はその例です。</span><span class="sxs-lookup"><span data-stu-id="a54db-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="a54db-185">`async void` メソッドでスローされた例外を、そのメソッドの外部でキャッチすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a54db-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="a54db-186">`async void` メソッドをテストするのは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="a54db-186">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="a54db-187">`async void` メソッドは、呼び出し元がそれを非同期と予期していないと、悪い副作用が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="a54db-188">**LINQ 式での非同期ラムダの使用は慎重に行う必要があります**</span><span class="sxs-lookup"><span data-stu-id="a54db-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="a54db-189">LINQ 内のラムダ式は遅延実行を使います。つまり、予期していないときにコードが実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="a54db-190">これにブロッキング タスクを組み込んだ場合、正しく作成されていないと、簡単にデッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="a54db-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="a54db-191">さらに、このように非同期コードを入れ子にすると、コードの実行についての推論も難しくなります。</span><span class="sxs-lookup"><span data-stu-id="a54db-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="a54db-192">非同期と LINQ は強力ですが、併用するときは可能な限り慎重かつ明確にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a54db-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="a54db-193">**タスクを待機するコードは非ブロッキング方式で作成します**</span><span class="sxs-lookup"><span data-stu-id="a54db-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="a54db-194">タスクが完了するのを待機するための手段として現在のスレッドをブロックすると、デッドロックおよびコンテキスト スレッドのブロックが発生する可能性があり、非常に複雑なエラー処理が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a54db-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="a54db-195">次の表では、非ブロッキング方式でタスクの待機に対処する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a54db-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="a54db-196">これを使う</span><span class="sxs-lookup"><span data-stu-id="a54db-196">Use this...</span></span> | <span data-ttu-id="a54db-197">これは使わない</span><span class="sxs-lookup"><span data-stu-id="a54db-197">Instead of this...</span></span> | <span data-ttu-id="a54db-198">行う処理</span><span class="sxs-lookup"><span data-stu-id="a54db-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="a54db-199">`Task.Wait` または `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="a54db-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="a54db-200">バックグラウンド タスクの結果の取得</span><span class="sxs-lookup"><span data-stu-id="a54db-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="a54db-201">任意のタスクの完了の待機</span><span class="sxs-lookup"><span data-stu-id="a54db-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="a54db-202">すべてのタスクの完了の待機</span><span class="sxs-lookup"><span data-stu-id="a54db-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="a54db-203">一定期間の待機</span><span class="sxs-lookup"><span data-stu-id="a54db-203">Waiting for a period of time</span></span> |

*   <span data-ttu-id="a54db-204">**ステートフル性の低いコードを記述します**</span><span class="sxs-lookup"><span data-stu-id="a54db-204">**Write less stateful code**</span></span>

<span data-ttu-id="a54db-205">グローバル オブジェクトの状態または特定のメソッドの実行に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="a54db-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="a54db-206">代わりに、メソッドの戻り値のみに依存するようにします。</span><span class="sxs-lookup"><span data-stu-id="a54db-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="a54db-207">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="a54db-207">Why?</span></span>

  *   <span data-ttu-id="a54db-208">コードを理解しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a54db-208">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="a54db-209">コードをテストしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a54db-209">Code will be easier to test.</span></span>
  *   <span data-ttu-id="a54db-210">非同期コードと同期コードの混在がはるかに簡単になります。</span><span class="sxs-lookup"><span data-stu-id="a54db-210">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="a54db-211">一般には、競合状態を完全に回避できます。</span><span class="sxs-lookup"><span data-stu-id="a54db-211">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="a54db-212">戻り値に依存すると、非同期コードの調整が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="a54db-212">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="a54db-213">(ボーナス) 依存関係の挿入で問題なく動作します。</span><span class="sxs-lookup"><span data-stu-id="a54db-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="a54db-214">推奨される目標は、完全またはほぼ完全な[参照の透過性](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29)をコードで実現することです。</span><span class="sxs-lookup"><span data-stu-id="a54db-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="a54db-215">そうすることで、予測、テスト、保守が非常に容易なコードベースになります。</span><span class="sxs-lookup"><span data-stu-id="a54db-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="a54db-216">その他の参照情報</span><span class="sxs-lookup"><span data-stu-id="a54db-216">Other Resources</span></span>

* <span data-ttu-id="a54db-217">「[非同期の詳細](../standard/async-in-depth.md)」では、タスクの動作方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a54db-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="a54db-218">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="a54db-218">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
* <span data-ttu-id="a54db-219">Lucian Wischik の「[Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async)」(非同期に関する 6 つの重要なヒント) は、非同期プログラミングのためのすばらしいリソースです。</span><span class="sxs-lookup"><span data-stu-id="a54db-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
