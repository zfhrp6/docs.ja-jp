---
title: "更新された .NET Core イベント パターン"
description: ".NET Core イベント パターンによって旧バージョンとの互換性を提供する柔軟性を実現する方法と、非同期サブスクライバーによる安全なイベント処理を実装する方法について説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cf69cbe0a7adbd274d1cb9e9544dda77d9fa1740
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="88622-104">更新された .NET Core イベント パターン</span><span class="sxs-lookup"><span data-stu-id="88622-104">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="88622-105">前へ</span><span class="sxs-lookup"><span data-stu-id="88622-105">Previous</span></span>](event-pattern.md)

<span data-ttu-id="88622-106">前回の記事では、最も一般的なイベント パターンについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="88622-106">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="88622-107">.NET Core には、もっと柔軟なパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="88622-107">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="88622-108">このバージョンでは、`EventHandler<TEventArgs>` 定義に、`TEventArgs` は `System.EventArgs` から派生したクラスでなければならないという制約がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="88622-108">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="88622-109">これにより、柔軟性が向上し、旧バージョンとの互換性が与えられます。</span><span class="sxs-lookup"><span data-stu-id="88622-109">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="88622-110">柔軟性から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="88622-110">Let's start with the flexibility.</span></span> <span data-ttu-id="88622-111">クラス System.EventArgs で `MemberwiseClone()` というメソッドが導入されました。これはオブジェクトの簡易コピーを作成するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="88622-111">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="88622-112">そのメソッドでは、`EventArgs` から派生したあらゆるクラスのための機能を実装する目的で、リフレクションを利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88622-112">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="88622-113">その機能では、特定の派生クラスでの作成が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="88622-113">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="88622-114">つまり、System.EventArgs からの派生は設計を制限する制約ですが、他に利点はありません。</span><span class="sxs-lookup"><span data-stu-id="88622-114">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="88622-115">実際、`EventArgs` から派生しないように `FileFoundArgs` と `SearchDirectoryArgs` の定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="88622-115">In fact, you can changes the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="88622-116">このプログラムはまったく同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="88622-116">The program will work exactly the same.</span></span>

<span data-ttu-id="88622-117">さらに 1 つ変更するのであれば、`SearchDirectoryArgs` を構造体に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="88622-117">You could also change the `SearchDirectoryArgs` to a struct, if you also make one more change:</span></span>

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

<span data-ttu-id="88622-118">追加の変更は、すべてのフィールドを初期化するコンストラクターに入る前に既定のコンストラクターを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="88622-118">The additional change is to call the default constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="88622-119">その追加がなければ、C# のルールは、割り当てられる前にプロパティがアクセスされていると報告するでしょう。</span><span class="sxs-lookup"><span data-stu-id="88622-119">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="88622-120">`FileFoundArgs` はクラス (参照型) から構造体 (値型) に変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="88622-120">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="88622-121">キャンセルを処理するプロトコルで、イベント引数が参照で渡されることが要求されるためです。</span><span class="sxs-lookup"><span data-stu-id="88622-121">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="88622-122">同じ変更をした場合、ファイル検索クラスは、イベント サブスクライバーが行った変更を観察できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88622-122">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="88622-123">サブスクライバーごとに構造体の新しいコピーが使用され、そのコピーは、ファイル検索オブジェクトで確認されるものとは別のコピーになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="88622-123">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="88622-124">次に、この変更を下位互換可能にする方法について考えましょう。</span><span class="sxs-lookup"><span data-stu-id="88622-124">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="88622-125">制約を削除しても、既存のコードには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="88622-125">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="88622-126">既存のイベントの引数の型は引き続き `System.EventArgs` から派生します。</span><span class="sxs-lookup"><span data-stu-id="88622-126">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="88622-127">`System.EventArgs` から引き続き派生する理由の 1 つが下位互換性です。</span><span class="sxs-lookup"><span data-stu-id="88622-127">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="88622-128">既存のイベント サブスクライバーは、従来のパターンに従ったイベントのサブスクライバーになります。</span><span class="sxs-lookup"><span data-stu-id="88622-128">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="88622-129">同様の論理に従うと、今、イベントの引数の型を作成すると、それには既存のコードベースのサブスクライバーが与えられないでしょう。</span><span class="sxs-lookup"><span data-stu-id="88622-129">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="88622-130">`System.EventArgs` から派生しない新しいイベントの型は、そのようなコードベースを壊しません。</span><span class="sxs-lookup"><span data-stu-id="88622-130">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="88622-131">非同期サブスクライバーのあるイベント</span><span class="sxs-lookup"><span data-stu-id="88622-131">Events with Async subscribers</span></span>

<span data-ttu-id="88622-132">学習する最後のパターンは、非同期コードを呼び出すイベント サブスクライバーを正しく記述する方法です。</span><span class="sxs-lookup"><span data-stu-id="88622-132">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="88622-133">この難題の説明は、[async と await](async.md) に関する記事にあります。</span><span class="sxs-lookup"><span data-stu-id="88622-133">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="88622-134">非同期メソッドには戻り値の型 void を指定できますが、指定しないことが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="88622-134">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="88622-135">イベント サブスクライバーのコードが非同期メソッドを呼び出すとき、`async void` メソッドを作成する以外の選択肢はありません。</span><span class="sxs-lookup"><span data-stu-id="88622-135">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="88622-136">イベント ハンドラー シグネチャでそれが要求されます。</span><span class="sxs-lookup"><span data-stu-id="88622-136">The event handler signature requires it.</span></span>

<span data-ttu-id="88622-137">このような相反する指示と何とか折り合いを付け、</span><span class="sxs-lookup"><span data-stu-id="88622-137">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="88622-138">無難な `async void` メソッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88622-138">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="88622-139">実装が必要なパターンの基本は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="88622-139">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="88622-140">最初に、ハンドラーが非同期ハンドラーとしてマークされていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="88622-140">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="88622-141">イベント ハンドラーのデリゲート型に割り当てられているため、戻り値の型 void が与えられます。</span><span class="sxs-lookup"><span data-stu-id="88622-141">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="88622-142">つまり、ハンドラーに示されるパターンに従う必要があります。非同期ハンドラーのコンテキストから例外をスローすることを許可しません。</span><span class="sxs-lookup"><span data-stu-id="88622-142">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="88622-143">タスクを返さないため、エラーが発生してもタスクはそれを報告できません。</span><span class="sxs-lookup"><span data-stu-id="88622-143">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="88622-144">メソッドは非同期であるため、例外をスローできません。</span><span class="sxs-lookup"><span data-stu-id="88622-144">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="88622-145">(呼び出しメソッドは `async` であるため、実行を続行しています。)実際の実行時動作は、環境が異なれば各様に定義されます。</span><span class="sxs-lookup"><span data-stu-id="88622-145">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="88622-146">スレッドを終了すること、プログラムを終了すること、プログラムを未決定の状態にすることがあります。</span><span class="sxs-lookup"><span data-stu-id="88622-146">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="88622-147">どれも好ましい結果ではありません。</span><span class="sxs-lookup"><span data-stu-id="88622-147">None of those are good outcomes.</span></span>

<span data-ttu-id="88622-148">そのため、独自の try ブロックに非同期タスクの await ステートメントをラップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="88622-148">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="88622-149">それでタスクにエラーが発生した場合、エラーをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="88622-149">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="88622-150">アプリケーションがエラーから復旧できない場合、プログラムを至急、正常に終了できます。</span><span class="sxs-lookup"><span data-stu-id="88622-150">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="88622-151">以上が .NET イベント パターンの主要な更新でした。</span><span class="sxs-lookup"><span data-stu-id="88622-151">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="88622-152">使用するライブラリには以前のバージョンのサンプルがたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="88622-152">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="88622-153">しかしながら、最新のパターンも理解してください。</span><span class="sxs-lookup"><span data-stu-id="88622-153">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="88622-154">このシリーズの次の記事では、設計における `delegates` と `events` の使い分けについて説明します。</span><span class="sxs-lookup"><span data-stu-id="88622-154">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="88622-155">概念は似ており、最良のプログラムを作るための知識をその記事で得ることができます。</span><span class="sxs-lookup"><span data-stu-id="88622-155">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="88622-156">次へ</span><span class="sxs-lookup"><span data-stu-id="88622-156">Next</span></span>](distinguish-delegates-events.md)

