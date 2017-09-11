---
title: "イベントの概要"
description: "この概要では、.NET Core のイベントと、イベントの言語上の設計目標について説明します。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f81c2d9fc2ec69c295485fe06029b5de65335db0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="introduction-to-events"></a><span data-ttu-id="449ba-104">イベントの概要</span><span class="sxs-lookup"><span data-stu-id="449ba-104">Introduction to Events</span></span>

[<span data-ttu-id="449ba-105">前へ</span><span class="sxs-lookup"><span data-stu-id="449ba-105">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="449ba-106">デリゲートのようなイベントは*遅延バインディング* メカニズムになっています。</span><span class="sxs-lookup"><span data-stu-id="449ba-106">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="449ba-107">実際、イベントはデリゲートの言語サポートに基づいて構築されます。</span><span class="sxs-lookup"><span data-stu-id="449ba-107">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="449ba-108">イベントは、何かが起こったことをオブジェクトが (システム内のあらゆる関連コンポーネントに) ブロードキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="449ba-108">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="449ba-109">他のコンポーネントはイベントを受信登録できます。イベントが発生すると通知されます。</span><span class="sxs-lookup"><span data-stu-id="449ba-109">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="449ba-110">プログラミングにイベントを利用した経験があることでしょう。</span><span class="sxs-lookup"><span data-stu-id="449ba-110">You've probably used events in some of your programming.</span></span> <span data-ttu-id="449ba-111">グラフィカル システムの多くには、ユーザー操作を報告するイベント モデルがあります。</span><span class="sxs-lookup"><span data-stu-id="449ba-111">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="449ba-112">そのようなイベントは、マウスが動いた、ボタンが押されたなどの動作を報告します。</span><span class="sxs-lookup"><span data-stu-id="449ba-112">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="449ba-113">それは最も一般的なイベントの 1 つですが、イベントが利用されるシナリオはこれだけではありません。</span><span class="sxs-lookup"><span data-stu-id="449ba-113">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="449ba-114">クラスに対して発生させるイベントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="449ba-114">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="449ba-115">イベントを使用するときに考慮するべき重要なことは、特定のイベントに登録されていないオブジェクトの可能性です。</span><span class="sxs-lookup"><span data-stu-id="449ba-115">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="449ba-116">リスナーが構成されていないときはイベントを発生させないようにコードを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-116">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="449ba-117">イベントを受信登録すると、2 つのオブジェクト (イベント ソースとイベント シンク) の間に結合も生成されます。</span><span class="sxs-lookup"><span data-stu-id="449ba-117">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="449ba-118">イベント シンクにイベントに対する関心がなくなったとき、イベント ソースの受信登録を解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-118">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="449ba-119">イベント サポートのデザイン目標</span><span class="sxs-lookup"><span data-stu-id="449ba-119">Design Goals for Event Support</span></span>

<span data-ttu-id="449ba-120">イベントの言語デザインには次のような目標があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-120">The language design for events targets these goals.</span></span>

<span data-ttu-id="449ba-121">最初の目標は、イベント ソースとイベント シンクの間で最小限の結合を有効にすることです。</span><span class="sxs-lookup"><span data-stu-id="449ba-121">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="449ba-122">これら 2 つのコンポーネントは、別々の組織に記述されることがあります。まったく異なる日程で更新されることもあります。</span><span class="sxs-lookup"><span data-stu-id="449ba-122">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="449ba-123">2 つ目の目標は、イベントの受信登録と登録解除を非常にシンプルにすることです。</span><span class="sxs-lookup"><span data-stu-id="449ba-123">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="449ba-124">最後の目標は、イベント ソースで複数のイベント サブスクライバーに対応することです。</span><span class="sxs-lookup"><span data-stu-id="449ba-124">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="449ba-125">イベント サブスクライバーをアタッチしないことにも対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-125">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="449ba-126">イベントの目標はデリゲートの目標とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="449ba-126">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="449ba-127">そのような理由から、イベント言語サポートはデリゲート言語サポートに基づいて構築されます。</span><span class="sxs-lookup"><span data-stu-id="449ba-127">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="449ba-128">イベントの言語サポート</span><span class="sxs-lookup"><span data-stu-id="449ba-128">Language Support for Events</span></span>

<span data-ttu-id="449ba-129">イベントの定義、受信登録、登録解除の構文は、デリゲートの構文の拡張になります。</span><span class="sxs-lookup"><span data-stu-id="449ba-129">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="449ba-130">イベントを定義するには、`event` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="449ba-130">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="449ba-131">イベントの種類 (この例の `EventHandler<FileListArgs>`) はデリゲート型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-131">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="449ba-132">イベントを宣言するときはさまざまな決まりごとを守る必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-132">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="449ba-133">通常、イベント デリゲート型には戻り値 void があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-133">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="449ba-134">イベント宣言は動詞または動詞句にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ba-134">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="449ba-135">何かが起こったことをイベントが報告するときは (この例のように) 過去時制を使用します。</span><span class="sxs-lookup"><span data-stu-id="449ba-135">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="449ba-136">何かが起こりそうなことを報告するには、現在時制の動詞 (たとえば、`Closing`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="449ba-136">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="449ba-137">多くの場合、現在時制の使用は、お使いのクラスで何らかのカスタマイズ動作をサポートしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="449ba-137">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="449ba-138">最も一般的なシナリオの 1 つがキャンセルのサポートです。</span><span class="sxs-lookup"><span data-stu-id="449ba-138">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="449ba-139">たとえば、`Closing` イベントには、close 操作を続行するかどうかを示す引数が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="449ba-139">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="449ba-140">イベント引数のプロパティを更新することで呼び出し元が動作を変更するシナリオもあります。</span><span class="sxs-lookup"><span data-stu-id="449ba-140">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="449ba-141">アルゴリズムに実行させる次のアクションを提案するイベントを発生させることもできます。</span><span class="sxs-lookup"><span data-stu-id="449ba-141">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="449ba-142">イベント ハンドラーは、イベント引数のプロパティを変更することで、別のアクションを命令することもあります。</span><span class="sxs-lookup"><span data-stu-id="449ba-142">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="449ba-143">イベントが発生させるとき、デリゲート呼び出し構文を利用してイベント ハンドラーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="449ba-143">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="449ba-144">[デリゲート](delegates-patterns.md)に関するセクションで説明したように、</span><span class="sxs-lookup"><span data-stu-id="449ba-144">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="449ba-145">?. 演算子を利用すると、イベントのサブスクライバーが存在しないとき、そのイベントの発生を試行しないように容易に確保できます。</span><span class="sxs-lookup"><span data-stu-id="449ba-145">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="449ba-146">`+=` 演算子を利用し、イベントを受信登録します。</span><span class="sxs-lookup"><span data-stu-id="449ba-146">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="449ba-147">上の画像のように、一般的にハンドラー メソッドはプレフィックス 'On' の後にイベント名を続けたものになります。</span><span class="sxs-lookup"><span data-stu-id="449ba-147">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="449ba-148">`-=` 演算子を利用して受信登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="449ba-148">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="449ba-149">イベント ハンドラーを表す式にローカル変数が宣言されたことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="449ba-149">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="449ba-150">これで受信登録解除によりハンドラーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="449ba-150">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="449ba-151">代わりにラムダ式の本文を使用した場合、アタッチされたことがないハンドラーの削除が試行され、何も起こりません。</span><span class="sxs-lookup"><span data-stu-id="449ba-151">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="449ba-152">次回の記事では、一般的なイベント パターンと今回のサンプルのさまざまなバリエーションについて学習します。</span><span class="sxs-lookup"><span data-stu-id="449ba-152">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="449ba-153">次へ</span><span class="sxs-lookup"><span data-stu-id="449ba-153">Next</span></span>](event-pattern.md)

