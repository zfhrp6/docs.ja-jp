---
title: 標準的な .NET イベント パターン
description: .NET イベント パターンに関する情報を提供するほか、標準的なイベント ソースを作成し、標準的なイベントをコードでサブスクライブおよび処理する方法について説明します。
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 9bd9f71726647966dd1e4426b260484decb048c6
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827249"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="8d97c-103">標準的な .NET イベント パターン</span><span class="sxs-lookup"><span data-stu-id="8d97c-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="8d97c-104">前へ</span><span class="sxs-lookup"><span data-stu-id="8d97c-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="8d97c-105">一般的に、.NET イベントはいくつかの既知のパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="8d97c-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="8d97c-106">これらのパターンを標準化すれば、開発者はこうした標準的なパターンの知識を活用し、あらゆる .NET イベント プログラムに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="8d97c-107">これらの標準的なパターンを理解することにより、標準的なイベント ソースを作成し、標準的なイベントをコードでサブスクライブし処理するために必要な知識を習得してください。</span><span class="sxs-lookup"><span data-stu-id="8d97c-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="8d97c-108">イベント デリゲートのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="8d97c-108">Event Delegate Signatures</span></span>

<span data-ttu-id="8d97c-109">.NET イベント デリゲートの標準的なシグネチャは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="8d97c-110">戻り値の型は void です。</span><span class="sxs-lookup"><span data-stu-id="8d97c-110">The return type is void.</span></span> <span data-ttu-id="8d97c-111">イベントは、デリゲートを基本とするマルチキャスト デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="8d97c-112">このため、任意のイベント ソースに対して複数のサブスクライバーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8d97c-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="8d97c-113">メソッドが返す単一の戻り値が複数のイベント サブスクライバーに拡張されることはありません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="8d97c-114">イベント発生後にイベントソースはどの戻り値を受け取るのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="8d97c-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="8d97c-115">この記事の後半で、イベント サブスクライバーをサポートするイベント プロトコルの作成方法を説明します。イベント サブスクライバーはイベント ソースに情報をレポートします。</span><span class="sxs-lookup"><span data-stu-id="8d97c-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="8d97c-116">引数リストには、2 つの引数、すなわち送信元とイベント引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="8d97c-117">`sender` のコンパイル時型は `System.Object` です。常に正しいより確実な派生型が存在する可能性はありますが、</span><span class="sxs-lookup"><span data-stu-id="8d97c-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="8d97c-118">慣例に従って、`object` を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-118">By convention, use `object`.</span></span>

<span data-ttu-id="8d97c-119">2 番目の引数は、通常は `System.EventArgs` から派生した型です。</span><span class="sxs-lookup"><span data-stu-id="8d97c-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="8d97c-120">([次のセクション](modern-events.md)で、この規則が適用されなくなっていることを説明します。)イベント型に引数を追加する必要がない場合でも、両方の引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="8d97c-121">特殊な値である `EventArgs.Empty` は、イベントにその他の情報が含まれていないことを示すために使用します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="8d97c-122">これから、パターンに従うディレクトリ、またはそのサブディレクトリのいずれかでファイルを一覧表示するクラスをビルドしていきます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="8d97c-123">このコンポーネントでは、パターンに一致することが確認されたファイルごとにイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="8d97c-124">イベント モデルを使用すると、設計上の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="8d97c-125">要求されたファイルを検出すると、異なるアクションを実行する複数のイベント リスナーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="8d97c-126">別のリスナーと組み合わせることで、より堅牢なアルゴリズムを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="8d97c-127">次に示すのは、要求されたファイルを検索するイベント引数を最初に宣言する部分です。</span><span class="sxs-lookup"><span data-stu-id="8d97c-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="8d97c-128">この型はデータのみの小さな型のように見えますが、規則に従って、参照 (`class`) 型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="8d97c-129">つまり、引数オブジェクトは参照によって渡され、データが更新されると、すべてのサブスクライバーから参照されます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="8d97c-130">最初のバージョンは、変更不可のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-130">The first version is an immutable object.</span></span> <span data-ttu-id="8d97c-131">イベント引数の型のプロパティを変更不可に設定しておいた方がよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="8d97c-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="8d97c-132">このようにすれば、別のサブスクライバーが値を確認する前に、いずれかのサブスクライバーが値を変更することがありません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="8d97c-133">(下記に説明するとおり、これには例外があります。)</span><span class="sxs-lookup"><span data-stu-id="8d97c-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="8d97c-134">次に、FileSearcher クラスでイベント宣言を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="8d97c-135">`EventHandler<T>` 型を活用すれば、もう 1 つ別の型を定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="8d97c-136">ジェネリックの特殊化を使用するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="8d97c-137">パターンに一致するファイルを検索し、一致が検出されると、適切なイベントを発生する FileSearcher クラスを記述します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="definining-and-raising-field-like-events"></a><span data-ttu-id="8d97c-138">フィールドのように使用するイベントの定義と発生</span><span class="sxs-lookup"><span data-stu-id="8d97c-138">Definining and Raising Field-Like Events</span></span>

<span data-ttu-id="8d97c-139">クラスにイベントを追加する最も簡単な方法は、上記の例のように、そのイベントをパブリック フィールドとして宣言することです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="8d97c-140">これはパブリック フィールドを宣言しているように見えるため、不適切なオブジェクト指向プラクティスと考えられるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="8d97c-141">プロパティ、またはメソッドでデータ アクセスを保護したくなるところです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="8d97c-142">これは一見すると不適切なプラクティスのように見えますが、コンパイラによって生成されたコードがラッパーを作成するため、イベント オブジェクトは安全な方法によってのみアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-142">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="8d97c-143">フィールドのように使用するイベントで使用できる唯一の操作は、ハンドラーの追加です。</span><span class="sxs-lookup"><span data-stu-id="8d97c-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="8d97c-144">それと、ハンドラーの削除です。</span><span class="sxs-lookup"><span data-stu-id="8d97c-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="8d97c-145">このハンドラーにはローカル変数があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="8d97c-146">ラムダの本体を使用する場合、削除は正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="8d97c-147">ラムダ本体はデリゲートの別のインスタンスであるため、自動的に何か実行することはありません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="8d97c-148">クラスの外側にあるコードはイベントを発生させることも、その他の操作を実行することもできません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="8d97c-149">イベント サブスクライバーからの戻り値</span><span class="sxs-lookup"><span data-stu-id="8d97c-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="8d97c-150">この単純なバージョンは正常に動作しています。</span><span class="sxs-lookup"><span data-stu-id="8d97c-150">Your simple version is working fine.</span></span> <span data-ttu-id="8d97c-151">次に、別の機能、キャンセルを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="8d97c-152">検出されたイベントを発生させるとき、このファイルが要求された最後のファイルである場合、リスナーはその後の処理を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="8d97c-153">イベント ハンドラーは値は返さないため、別の方法で値を伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="8d97c-154">標準的なイベント パターンでは、イベント サブスクライバーがキャンセルを伝達するために使用するフィールドを含めるために、EventArgs オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="8d97c-155">使用できるパターンには 2 種類あり、それらは Cancel コントラクトのセマンティクスに基づいています。</span><span class="sxs-lookup"><span data-stu-id="8d97c-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="8d97c-156">どちらの場合も、検出されたファイル イベントの EventArguments にブール型フィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="8d97c-157">1 つのパターンでは、任意のサブスクライバーが単独で操作をキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="8d97c-158">このパターンでは、新しいフィールドは `false` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="8d97c-159">どのサブスクライバーでもこのフィールドを `true` に変更できます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="8d97c-160">すべてのサブスクライバーがイベントの発生を確認すると、FileSearcher コンポーネントがブール値を検証し、アクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="8d97c-161">2 つ目のパターンでは、すべてのサブスクライバーが操作のキャンセルを認める場合に限り、操作がキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="8d97c-162">このパターンでは、新しいフィールドは操作のキャンセルを示すように初期化され、任意のサブスクライバーが操作を続行するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="8d97c-163">すべてのサブスクライバーがイベントの発生を確認すると、FileSearcher コンポーネントがブール値を検証し、アクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="8d97c-164">このパターンには、手順がもう 1 つあり、コンポーネントは、いずれかのサブスクライバーがイベントを確認したか把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="8d97c-165">サブスクライバーが存在しない場合、フィールドが示すキャンセルは誤りとなります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="8d97c-166">次に、このサンプルの最初のバージョンを実装します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="8d97c-167">`FileFoundArgs` 型に `CancelRequested` という名前のブール型フィールドを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="8d97c-168">誤ってキャンセルすることがないように、この新しいフィールドは `false` (ブール型フィールドの既定値) に自動的に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="8d97c-169">コンポーネントのもう 1 つの変更点は、イベントが発生したあと、フラグをチェックして、いずれかのサブスクライバーがキャンセルを要求しているか確認することです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="8d97c-170">このパターンの利点の 1 つは、この変更が重大な変更ではないことです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="8d97c-171">いずれのサブスクライバーも前にキャンセルを要求していなければ、引き続き同じ状態が維持されます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="8d97c-172">サブスクライバーが新しいキャンセル プロトコルをサポートしない限り、どのサブスクライバーのコードも更新する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="8d97c-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="8d97c-173">非常にゆるやかな結合となっています。</span><span class="sxs-lookup"><span data-stu-id="8d97c-173">It's very loosely coupled.</span></span>

<span data-ttu-id="8d97c-174">次に、最初の実行可能ファイルが検索されると、キャンセルを要求するように、サブスクライバーを更新します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="8d97c-175">別のイベント宣言の追加</span><span class="sxs-lookup"><span data-stu-id="8d97c-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="8d97c-176">ここで、1 つの機能を追加し、イベント用の他の慣用句について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="8d97c-177">すべてのサブディレクトリを走査してファイルを検索する `Search()` メソッドのオーバーロードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-177">Let's add an overload of the `Search()` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="8d97c-178">多くのサブディレクトリを持つディレクトリでは、これは時間のかかる操作となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="8d97c-179">次に、新しいディレクトリの検索が開始するたびに発生するイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="8d97c-180">このイベントによって、サブスクライバーは進行状況を追跡し、進行状況の更新をユーザーに伝えます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="8d97c-181">これまでに作成したすべてのサンプルは、パブリックです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="8d97c-182">このイベントを内部イベントにします。</span><span class="sxs-lookup"><span data-stu-id="8d97c-182">Let's make this one an internal event.</span></span> <span data-ttu-id="8d97c-183">つまり、引数に使用される型を内部型にすることもできるということです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="8d97c-184">最初に、新しいディレクトリと進行状況をレポートする新しい EventArgs 派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="8d97c-185">ここでも、イベント引数に変更不可の参照型を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8d97c-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="8d97c-186">次に、イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-186">Next, define the event.</span></span> <span data-ttu-id="8d97c-187">今回は、別の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="8d97c-188">フィールドの構文を使用する以外に、明示的にプロパティを作成し、ハンドラーを追加、削除することができます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="8d97c-189">このサンプルでは、ハンドラーにコードを追加する必要はありませんが、次に示したのはそれを作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="8d97c-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="8d97c-190">ここで作成するコードは、多くの点で、コンパイラがフィールドのイベントを定義するために作成した先ほどのコードとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="8d97c-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="8d97c-191">イベントを作成するときに、[プロパティ](properties.md)で使用する構文と非常によく似た構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="8d97c-192">このハンドラーには、`add` および `remove` という別の名前があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8d97c-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="8d97c-193">これらはイベントをサブスクライブするか、またはイベントのサブスクリプションを解除するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="8d97c-194">また、イベント変数を格納するために、プライベートなバッキング フィールドを宣言する必要があることにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="8d97c-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="8d97c-195">このフィールドは null に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-195">It is initialized to null.</span></span>

<span data-ttu-id="8d97c-196">次に、サブディレクトリを走査し、両方のイベントを発生させる Search() メソッドのオーバー ロードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-196">Next, let's add the overload of the Search() method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="8d97c-197">これを実現する最も簡単な方法は、既定の引数を使用して、すべてのディレクトリの検索を指定することです。</span><span class="sxs-lookup"><span data-stu-id="8d97c-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="8d97c-198">この時点で、アプリケーションを実行し、すべてのサブディレクトリを検索するオーバーロードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="8d97c-199">新しい `ChangeDirectory` イベントでは、サブスクライバーが存在しませんが、`?.Invoke()` 慣用句を使用すれば、正常に動作させることができます。</span><span class="sxs-lookup"><span data-stu-id="8d97c-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="8d97c-200">ここで、コンソール ウィンドウに進行状況を表示する行を記述するハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d97c-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="8d97c-201">このトピックでは、.NET エコシステム全体で使用されるパターンを確認しました。</span><span class="sxs-lookup"><span data-stu-id="8d97c-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="8d97c-202">これらのパターンと規則を学習することにより、慣用句を使用した C# および .NET をすばやく記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8d97c-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="8d97c-203">次の項目では、.NET の最新のリリースで変更されたパターンを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8d97c-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="8d97c-204">次へ</span><span class="sxs-lookup"><span data-stu-id="8d97c-204">Next</span></span>](modern-events.md)
