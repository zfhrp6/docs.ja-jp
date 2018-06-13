---
title: イベント (F#)
description: F# のイベントを使用すると、ユーザーの操作は、GUI プログラミングの重要な関数呼び出しを関連付ける方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e90d3abc5b5222f60c4e08539ee40bf83ac70ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564784"
---
# <a name="events"></a><span data-ttu-id="5223b-103">イベント</span><span class="sxs-lookup"><span data-stu-id="5223b-103">Events</span></span>

> [!NOTE]
<span data-ttu-id="5223b-104">この記事の API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="5223b-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="5223b-105">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="5223b-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="5223b-106">イベントを使用すると、関数呼び出しをユーザーによる操作に関連付けることができます。イベントは、GUI プログラミングの重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="5223b-106">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="5223b-107">イベントは、アプリケーションまたはオペレーティング システムによってトリガーすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5223b-107">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="5223b-108">イベントの処理</span><span class="sxs-lookup"><span data-stu-id="5223b-108">Handling Events</span></span>
<span data-ttu-id="5223b-109">Windows フォームや WPF (Windows Presentation Foundation) などの GUI ライブラリを使用する場合、アプリケーションのコードの大半は、ライブラリによって定義されたイベントに応答して実行されます。</span><span class="sxs-lookup"><span data-stu-id="5223b-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="5223b-110">これらの定義済みイベントは、フォームやコントロールなどの GUI クラスのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="5223b-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="5223b-111">ボタン クリックなどの既存のイベントにカスタム動作を追加するには、次のコードに示すように、目的の名前付きイベント (たとえば、`Click` クラスの `Form` イベント) を参照し、`Add` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5223b-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="5223b-112">F# Interactive からこれを実行する場合は、`System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` の呼び出しを省略します。</span><span class="sxs-lookup"><span data-stu-id="5223b-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="5223b-113">`Add` メソッドの型は、`('a -> unit) -> unit` です。</span><span class="sxs-lookup"><span data-stu-id="5223b-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="5223b-114">したがって、イベント ハンドラー メソッドは、1 つのパラメーター (通常はイベント引数) を受け取り、`unit` を返します。</span><span class="sxs-lookup"><span data-stu-id="5223b-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="5223b-115">前の例は、ラムダ式としてのイベント ハンドラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="5223b-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="5223b-116">イベント ハンドラーは、次のコード例に示すように、関数値である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5223b-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="5223b-117">次のコード例は、イベントの種類に固有の情報を提供するイベント ハンドラー パラメーターの使い方も示しています。</span><span class="sxs-lookup"><span data-stu-id="5223b-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="5223b-118">`MouseMove` イベントの場合、システムはポインターの `System.Windows.Forms.MouseEventArgs` 位置および `X` 位置を含む `Y` オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="5223b-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a><span data-ttu-id="5223b-119">カスタム イベントの作成</span><span class="sxs-lookup"><span data-stu-id="5223b-119">Creating Custom Events</span></span>
<span data-ttu-id="5223b-120">F# のイベントは、f# で表されます[イベント](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9)クラスを実装する、 [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="5223b-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="5223b-121">`IEvent` その他の 2 つのインターフェイスの機能を結合するインターフェイス自体が`System.IObservable<'T>`と[IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a)です。</span><span class="sxs-lookup"><span data-stu-id="5223b-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="5223b-122">したがって、`Event` は、他の言語のデリゲートに相当する機能と、`IObservable` からの追加機能を備えていることになります。つまり、F# のイベントでは、イベントのフィルター処理がサポートされるほか、F# のファースト クラスの関数とラムダ式をイベント ハンドラーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="5223b-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="5223b-123">この機能を提供、[イベント モジュール](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)です。</span><span class="sxs-lookup"><span data-stu-id="5223b-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="5223b-124">他の任意の .NET Framework イベントと同様に動作するイベントをクラスに作成するには、クラスのフィールドとして `let` を定義する `Event` 束縛をクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="5223b-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="5223b-125">目的のイベント引数の型を型引数として指定することも、指定せずにコンパイラによって適切な型を推論することもできます。</span><span class="sxs-lookup"><span data-stu-id="5223b-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="5223b-126">CLI イベントとしてイベントを公開するイベント メンバーも定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5223b-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="5223b-127">このメンバーである必要があります、 [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333)属性。</span><span class="sxs-lookup"><span data-stu-id="5223b-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="5223b-128">プロパティのように宣言されているとその実装がへの呼び出しだけ、[発行](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e)イベントのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5223b-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="5223b-129">クラスのユーザーは、公開されたイベントの `Add` メソッドを使用してハンドラーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="5223b-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="5223b-130">`Add` メソッドの引数はラムダ式にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5223b-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="5223b-131">イベントの `Trigger` プロパティを使用すると、イベントを発生させて、引数をハンドラー関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5223b-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="5223b-132">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5223b-132">The following code example illustrates this.</span></span> <span data-ttu-id="5223b-133">この例では、イベントの型引数はタプルとして推論され、ラムダ式の引数を表します。</span><span class="sxs-lookup"><span data-stu-id="5223b-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="5223b-134">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5223b-134">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="5223b-135">`Event` モジュールで提供される追加の機能を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="5223b-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="5223b-136">次のコードは、`Event.create` の基本的な使用例を示しています。イベントおよびトリガー メソッドを作成し、ラムダ式の形式で 2 つのイベント ハンドラーを追加して、イベントを発生させて両方のラムダ式を実行します。</span><span class="sxs-lookup"><span data-stu-id="5223b-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="5223b-137">このコードの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5223b-137">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="5223b-138">イベント ストリームの処理</span><span class="sxs-lookup"><span data-stu-id="5223b-138">Processing Event Streams</span></span>
<span data-ttu-id="5223b-139">使用して、イベントのイベント ハンドラーを追加するだけではなく、 [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd)関数内の関数を使用することができます、`Event`詳細にカスタマイズされた方法でイベントのストリームを処理モジュールです。</span><span class="sxs-lookup"><span data-stu-id="5223b-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="5223b-140">これを行うには、一連の関数呼び出しの最初の値として、イベントと共に前方パイプ (`|>`) を使用します。`Event` モジュールは、以降の関数呼び出しとして機能します。</span><span class="sxs-lookup"><span data-stu-id="5223b-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="5223b-141">特定の条件でのみ呼び出されるハンドラーを持つイベントを設定する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5223b-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="5223b-142">[Observable モジュール](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227)観測可能なオブジェクトを操作する同様の機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5223b-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="5223b-143">観測可能なオブジェクトはイベントに似ていますが、オブジェクト自体がサブスクライブされている場合にのみ、イベントをアクティブにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="5223b-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>


## <a name="implementing-an-interface-event"></a><span data-ttu-id="5223b-144">インターフェイス イベントの実装</span><span class="sxs-lookup"><span data-stu-id="5223b-144">Implementing an Interface Event</span></span>
<span data-ttu-id="5223b-145">UI コンポーネントを開発するときは、多くの場合、まず、既存のフォームまたはコントロールを継承した新しいフォームまたはコントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="5223b-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="5223b-146">イベントは、しばしばインターフェイスで定義され、その場合、インターフェイスを実装してイベントを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5223b-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="5223b-147">`System.ComponentModel.INotifyPropertyChanged` インターフェイスは単一の `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="5223b-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="5223b-148">次のコードは、この継承されたインターフェイスで定義されたイベントを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5223b-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish


    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="5223b-149">コンストラクターでイベントをフックアップする場合、イベント フックアップが追加のコンストラクターの `then` ブロックに存在する必要があるため、コードは次の例のように少し複雑になります。</span><span class="sxs-lookup"><span data-stu-id="5223b-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")


    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)


// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="5223b-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="5223b-150">See Also</span></span>
[<span data-ttu-id="5223b-151">メンバー</span><span class="sxs-lookup"><span data-stu-id="5223b-151">Members</span></span>](index.md)

[<span data-ttu-id="5223b-152">処理と、イベントを発生させる</span><span class="sxs-lookup"><span data-stu-id="5223b-152">Handling and Raising Events</span></span>](../../../../docs/standard/events/index.md)

[<span data-ttu-id="5223b-153">ラムダ式:`fun`キーワード</span><span class="sxs-lookup"><span data-stu-id="5223b-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)

[<span data-ttu-id="5223b-154">Control.Event モジュール</span><span class="sxs-lookup"><span data-stu-id="5223b-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[<span data-ttu-id="5223b-155">Control.Event&#60;' T&#62;クラス</span><span class="sxs-lookup"><span data-stu-id="5223b-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[<span data-ttu-id="5223b-156">Control.Event&#60;'Delegate'、Args&#62;クラス</span><span class="sxs-lookup"><span data-stu-id="5223b-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
