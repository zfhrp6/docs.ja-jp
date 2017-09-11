---
title: "方法 : イベント サブスクリプションとサブスクリプションの解除 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d444a2efe03ec127ff88236deadab719d0d64259
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="dc004-102">方法 : イベント サブスクリプションとサブスクリプションの解除 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="dc004-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="dc004-103">別のクラスによってパブリッシュされるイベントが発生したときに呼び出されるカスタム コードを作成するときは、そのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="dc004-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="dc004-104">たとえば、ユーザーがボタンをクリックしたらアプリケーションで何かを行うには、ボタンの `click` イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="dc004-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="dc004-105">Visual Studio IDE を使ってイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="dc004-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="dc004-106">**デザイン** ビューに **[プロパティ]** ウィンドウが表示されない場合は、イベント ハンドラーを作成するフォームまたはコントロールを右クリックして、**[プロパティ]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="dc004-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="dc004-107">**[プロパティ]** ウィンドウの **[イベント]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dc004-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="dc004-108">作成するイベントをダブルクリックします (`Load` イベントなど)。</span><span class="sxs-lookup"><span data-stu-id="dc004-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     [!INCLUDE[csprcs](~/includes/csprcs-md.md)]<span data-ttu-id="dc004-109"> によって空のイベント ハンドラー メソッドを作成され、コードに追加されます。</span><span class="sxs-lookup"><span data-stu-id="dc004-109"> creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="dc004-110">または、**コード** ビューを使って手動でコードを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc004-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="dc004-111">たとえば、次のコード行では、`Form` クラスで `Load` イベントが発生すると呼び出されるイベント ハンドラー メソッドを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="dc004-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     <span data-ttu-id="dc004-112">[!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc004-112">[!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]</span></span>  
  
     <span data-ttu-id="dc004-113">イベントをサブスクライブするために必要なコード行も、プロジェクトの Form1.Designer.cs ファイルの `InitializeComponent` メソッドに自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="dc004-113">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="dc004-114">次のようなコードです。</span><span class="sxs-lookup"><span data-stu-id="dc004-114">It resembles this:</span></span>  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="dc004-115">プログラムでイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="dc004-115">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="dc004-116">シグネチャがイベントのデリゲート シグネチャと一致するイベント ハンドラー メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="dc004-116">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="dc004-117">たとえば、イベントが <xref:System.EventHandler> デリゲート型に基づいている場合は、次のコードがメソッド スタブを表します。</span><span class="sxs-lookup"><span data-stu-id="dc004-117">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="dc004-118">加算代入演算子 (`+=`) を使って、イベントにイベント ハンドラーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="dc004-118">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="dc004-119">次の例では、`publisher` オブジェクトに `RaiseCustomEvent` という名前のイベントがあるものとします。</span><span class="sxs-lookup"><span data-stu-id="dc004-119">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="dc004-120">イベントをサブスクライブするには、サブスクライバー クラスがそのパブリッシャー クラスを参照する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dc004-120">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="dc004-121">上の構文は、C# 2.0 で新しく追加されたものです。</span><span class="sxs-lookup"><span data-stu-id="dc004-121">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="dc004-122">これは、`new` キーワードを使ってカプセル化するデリゲートを明示的に作成する必要がある C# 1.0 の構文と完全に同等です。</span><span class="sxs-lookup"><span data-stu-id="dc004-122">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="dc004-123">イベント ハンドラーは、ラムダ式を使って追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="dc004-123">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="dc004-124">詳しくは、「[方法: LINQ 以外でラムダ式を使用する](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc004-124">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="dc004-125">匿名メソッドを使ってイベントをサブスクライブするには</span><span class="sxs-lookup"><span data-stu-id="dc004-125">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="dc004-126">後でイベントのサブスクリプションを解除する必要がない場合は、加算代入演算子 (`+=`) を使って匿名メソッドをイベントにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="dc004-126">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="dc004-127">次の例では、`publisher` オブジェクトに `RaiseCustomEvent` という名前のイベントがあり、`CustomEventArgs` クラスもある種の特別なイベント情報を保持するように定義されているものとします。</span><span class="sxs-lookup"><span data-stu-id="dc004-127">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="dc004-128">イベントをサブスクライブするには、サブスクライバー クラスがその `publisher` クラスを参照する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dc004-128">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="dc004-129">匿名関数を使ってイベントをサブスクライブした場合、簡単にはイベントのサブスクリプションを解除できないことに注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="dc004-129">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="dc004-130">このシナリオでサブスクリプションを解除するには、イベントをサブスクライブするコードに戻り、匿名メソッドをデリゲート変数に格納して、イベントにデリゲートを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc004-130">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="dc004-131">一般に、後のコードでイベントのサブスクリプションを解除する必要がある場合は、イベントのサブスクライブに匿名関数を使わないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="dc004-131">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="dc004-132">匿名関数について詳しくは、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dc004-132">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="dc004-133">サブスクリプションの解除</span><span class="sxs-lookup"><span data-stu-id="dc004-133">Unsubscribing</span></span>  
 <span data-ttu-id="dc004-134">イベントが発生したときにイベント ハンドラーが呼び出されないようにするには、イベントからサブスクリプションを解除します。</span><span class="sxs-lookup"><span data-stu-id="dc004-134">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="dc004-135">リソースのリークを防ぐには、サブスクライバー オブジェクトを破棄する前に、イベントのサブスクリプションを解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc004-135">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="dc004-136">イベントのサブスクリプションを解除するまで、パブリッシュ側オブジェクトでイベントの基盤になっているマルチキャスト デリゲートは、サブスクライバーのイベント ハンドラーをカプセル化するデリゲートへの参照を保持しています。</span><span class="sxs-lookup"><span data-stu-id="dc004-136">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="dc004-137">パブリッシュ側オブジェクトがその参照を保持している限り、ガベージ コレクションはサブスクライバー オブジェクトを削除しません。</span><span class="sxs-lookup"><span data-stu-id="dc004-137">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="dc004-138">イベントのサブスクリプションを解除するには</span><span class="sxs-lookup"><span data-stu-id="dc004-138">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="dc004-139">イベントのサブスクリプションを解除するには、減算代入演算子 (`-=`) を使います。</span><span class="sxs-lookup"><span data-stu-id="dc004-139">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="dc004-140">すべてのサブスクライバーがイベントのサブスクリプションを解除すると、パブリッシャー クラスのイベント インスタンスは `null` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="dc004-140">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc004-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc004-141">See Also</span></span>  
 <span data-ttu-id="dc004-142">[イベント](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc004-142">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="dc004-143">[event](../../../csharp/language-reference/keywords/event.md) </span><span class="sxs-lookup"><span data-stu-id="dc004-143">[event](../../../csharp/language-reference/keywords/event.md) </span></span>  
 <span data-ttu-id="dc004-144">[方法: .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md) </span><span class="sxs-lookup"><span data-stu-id="dc004-144">[How to: Publish Events that Conform to .NET Framework Guidelines](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md) </span></span>  
 <span data-ttu-id="dc004-145">[-= 演算子 (C# リファレンス)](../../language-reference/operators/subtraction-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="dc004-145">[-= Operator (C# Reference)](../../language-reference/operators/subtraction-assignment-operator.md) </span></span>  
 [<span data-ttu-id="dc004-146">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="dc004-146">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)

