---
title: "方法 : イベント サブスクリプションとサブスクリプションの解除 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5555cc8913bff953601c54aa7430143dc22173c0
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="ef8f7-102">方法 : イベント サブスクリプションとサブスクリプションの解除 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ef8f7-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="ef8f7-103">別のクラスによってパブリッシュされるイベントが発生したときに呼び出されるカスタム コードを作成するときは、そのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="ef8f7-104">たとえば、ユーザーがボタンをクリックしたらアプリケーションで何かを行うには、ボタンの `click` イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="ef8f7-105">Visual Studio IDE を使ってイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="ef8f7-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="ef8f7-106">**デザイン** ビューに **[プロパティ]** ウィンドウが表示されない場合は、イベント ハンドラーを作成するフォームまたはコントロールを右クリックして、**[プロパティ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="ef8f7-107">**[プロパティ]** ウィンドウの **[イベント]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="ef8f7-108">作成するイベントをダブルクリックします (`Load` イベントなど)。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     [!INCLUDE[csprcs](~/includes/csprcs-md.md)]<span data-ttu-id="ef8f7-109"> によって空のイベント ハンドラー メソッドを作成され、コードに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-109"> creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="ef8f7-110">または、**コード** ビューを使って手動でコードを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="ef8f7-111">たとえば、次のコード行では、`Form` クラスで `Load` イベントが発生すると呼び出されるイベント ハンドラー メソッドを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     <span data-ttu-id="ef8f7-112">イベントをサブスクライブするために必要なコード行も、プロジェクトの Form1.Designer.cs ファイルの `InitializeComponent` メソッドに自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="ef8f7-113">次のようなコードです。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="ef8f7-114">プログラムでイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="ef8f7-114">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="ef8f7-115">シグネチャがイベントのデリゲート シグネチャと一致するイベント ハンドラー メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="ef8f7-116">たとえば、イベントが <xref:System.EventHandler> デリゲート型に基づいている場合は、次のコードがメソッド スタブを表します。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="ef8f7-117">加算代入演算子 (`+=`) を使って、イベントにイベント ハンドラーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="ef8f7-118">次の例では、`publisher` オブジェクトに `RaiseCustomEvent` という名前のイベントがあるものとします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="ef8f7-119">イベントをサブスクライブするには、サブスクライバー クラスがそのパブリッシャー クラスを参照する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="ef8f7-120">上の構文は、C# 2.0 で新しく追加されたものです。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="ef8f7-121">これは、`new` キーワードを使ってカプセル化するデリゲートを明示的に作成する必要がある C# 1.0 の構文と完全に同等です。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="ef8f7-122">イベント ハンドラーは、ラムダ式を使って追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="ef8f7-123">詳しくは、「[方法: LINQ 以外でラムダ式を使用する](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="ef8f7-124">匿名メソッドを使ってイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="ef8f7-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="ef8f7-125">後でイベントのサブスクリプションを解除する必要がない場合は、加算代入演算子 (`+=`) を使って匿名メソッドをイベントにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="ef8f7-126">次の例では、`publisher` オブジェクトに `RaiseCustomEvent` という名前のイベントがあり、`CustomEventArgs` クラスもある種の特別なイベント情報を保持するように定義されているものとします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="ef8f7-127">イベントをサブスクライブするには、サブスクライバー クラスがその `publisher` クラスを参照する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="ef8f7-128">匿名関数を使ってイベントをサブスクライブした場合、簡単にはイベントのサブスクリプションを解除できないことに注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="ef8f7-129">このシナリオでサブスクリプションを解除するには、イベントをサブスクライブするコードに戻り、匿名メソッドをデリゲート変数に格納して、イベントにデリゲートを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="ef8f7-130">一般に、後のコードでイベントのサブスクリプションを解除する必要がある場合は、イベントのサブスクライブに匿名関数を使わないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="ef8f7-131">匿名関数について詳しくは、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="ef8f7-132">サブスクリプションの解除</span><span class="sxs-lookup"><span data-stu-id="ef8f7-132">Unsubscribing</span></span>  
 <span data-ttu-id="ef8f7-133">イベントが発生したときにイベント ハンドラーが呼び出されないようにするには、イベントからサブスクリプションを解除します。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="ef8f7-134">リソースのリークを防ぐには、サブスクライバー オブジェクトを破棄する前に、イベントのサブスクリプションを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="ef8f7-135">イベントのサブスクリプションを解除するまで、パブリッシュ側オブジェクトでイベントの基盤になっているマルチキャスト デリゲートは、サブスクライバーのイベント ハンドラーをカプセル化するデリゲートへの参照を保持しています。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="ef8f7-136">パブリッシュ側オブジェクトがその参照を保持している限り、ガベージ コレクションはサブスクライバー オブジェクトを削除しません。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="ef8f7-137">イベントのサブスクリプションを解除するには</span><span class="sxs-lookup"><span data-stu-id="ef8f7-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="ef8f7-138">イベントのサブスクリプションを解除するには、減算代入演算子 (`-=`) を使います。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="ef8f7-139">すべてのサブスクライバーがイベントのサブスクリプションを解除すると、パブリッシャー クラスのイベント インスタンスは `null` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ef8f7-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8f7-140">参照</span><span class="sxs-lookup"><span data-stu-id="ef8f7-140">See Also</span></span>  
 [<span data-ttu-id="ef8f7-141">イベント</span><span class="sxs-lookup"><span data-stu-id="ef8f7-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="ef8f7-142">event</span><span class="sxs-lookup"><span data-stu-id="ef8f7-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)  
 [<span data-ttu-id="ef8f7-143">方法: .NET Framework ガイドラインに準拠したイベントを発行する</span><span class="sxs-lookup"><span data-stu-id="ef8f7-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [<span data-ttu-id="ef8f7-144">-= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ef8f7-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="ef8f7-145">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="ef8f7-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)