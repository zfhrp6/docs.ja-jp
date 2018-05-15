---
title: イベントの処理 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 0ac3514505ca42870d77317feec30a27e4384e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="f7369-102">チュートリアル: イベントの処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7369-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="f7369-103">これは、2 番目のイベントを使用する方法を示す 2 つのトピックです。</span><span class="sxs-lookup"><span data-stu-id="f7369-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="f7369-104">最初のトピックでは、[チュートリアル: イベントを宣言して発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)、宣言およびイベントを発生させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7369-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="f7369-105">このセクションでは、行われるときにイベントを処理するのに方法を示します。 フォームとそのチュートリアルからクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f7369-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="f7369-106">`Widget`クラスの例は、従来のイベント処理のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f7369-106">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="f7369-107">Visual Basic では、イベントの処理の他の手法を提供します。</span><span class="sxs-lookup"><span data-stu-id="f7369-107">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="f7369-108">演習として使用するには、この例を変更することができます、`AddHandler`と`Handles`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="f7369-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="f7369-109">ウィジェットのクラスのことですイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="f7369-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="f7369-110">次のコードを配置`Form1`:</span><span class="sxs-lookup"><span data-stu-id="f7369-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="f7369-111">`WithEvents`キーワードを指定する変数`mWidget`オブジェクトのイベントを処理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f7369-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="f7369-112">オブジェクトの種類を指定するには、オブジェクトの作成元となるクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7369-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="f7369-113">変数`mWidget`で宣言された`Form1`ため`WithEvents`変数はクラス レベルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7369-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="f7369-114">これは、配置することでクラスの種類に関係なく当てはまります。</span><span class="sxs-lookup"><span data-stu-id="f7369-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="f7369-115">変数`mblnCancel`、キャンセルに使用、`LongTask`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f7369-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="f7369-116">イベントを処理するコードの記述</span><span class="sxs-lookup"><span data-stu-id="f7369-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="f7369-117">使用して変数を宣言するとすぐに`WithEvents`、クラスの左のドロップダウン リストで、変数名が表示されます**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="f7369-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="f7369-118">選択すると`mWidget`、`Widget`右のドロップダウン リストにクラスのイベントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f7369-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="f7369-119">イベントの対応するプロシージャのプレフィックスを持つイベントを選択すると表示`mWidget`とアンダー スコア。</span><span class="sxs-lookup"><span data-stu-id="f7369-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="f7369-120">関連付けられているすべてのイベント プロシージャ、`WithEvents`変数は、プレフィックスとして変数名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f7369-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="f7369-121">イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="f7369-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="f7369-122">選択`mWidget`で、左側のドロップダウン リストから、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="f7369-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="f7369-123">選択、`PercentDone`右のドロップダウン リストからのイベントです。</span><span class="sxs-lookup"><span data-stu-id="f7369-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="f7369-124">**コード エディター**開きます、`mWidget_PercentDone`イベント プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="f7369-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7369-125">**コード エディター**は役立ちますが、必須ではない新しいイベント ハンドラーを挿入するためです。</span><span class="sxs-lookup"><span data-stu-id="f7369-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="f7369-126">このチュートリアルでは、イベント ハンドラーのコードに直接コピーするより直接的です。</span><span class="sxs-lookup"><span data-stu-id="f7369-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="f7369-127">`mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f7369-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="f7369-128">ときに、`PercentDone`イベントは、イベントの手順で完了したパーセントが表示されます、`Label`コントロール。</span><span class="sxs-lookup"><span data-stu-id="f7369-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="f7369-129">`DoEvents`メソッドにより、再描画するラベルもにより、ユーザーをクリックして、**キャンセル**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7369-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="f7369-130">次のコードを追加、`Button2_Click`イベントのハンドラー。</span><span class="sxs-lookup"><span data-stu-id="f7369-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="f7369-131">ユーザーがクリックした場合、**キャンセル**中にボタン`LongTask`が実行されている、`Button2_Click`イベントが実行されるとすぐに、`DoEvents`ステートメントが発生するイベント処理を許可します。</span><span class="sxs-lookup"><span data-stu-id="f7369-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="f7369-132">クラス レベルの変数`mblnCancel`に設定されている`True`、および`mWidget_PercentDone`イベントことをテストし、設定、`ByRef Cancel`引数`True`です。</span><span class="sxs-lookup"><span data-stu-id="f7369-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="f7369-133">WithEvents 変数をオブジェクトに接続します。</span><span class="sxs-lookup"><span data-stu-id="f7369-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="f7369-134">`Form1` 処理するようになりました設定、`Widget`オブジェクトのイベントです。</span><span class="sxs-lookup"><span data-stu-id="f7369-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="f7369-135">すべてのタスクが見つかりません、`Widget`どこかにします。</span><span class="sxs-lookup"><span data-stu-id="f7369-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="f7369-136">変数を宣言するときに`WithEvents`デザイン時にオブジェクトが関連付けられていないこと。</span><span class="sxs-lookup"><span data-stu-id="f7369-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="f7369-137">A`WithEvents`変数は、その他のすべてのオブジェクト変数と同じようにします。</span><span class="sxs-lookup"><span data-stu-id="f7369-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="f7369-138">オブジェクトを作成しを使って参照を代入する必要がある、`WithEvents`変数。</span><span class="sxs-lookup"><span data-stu-id="f7369-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="f7369-139">オブジェクトを作成してへの参照を割り当てる</span><span class="sxs-lookup"><span data-stu-id="f7369-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="f7369-140">選択 **(Form1 イベント)** で、左側のドロップダウン リストから、**コード エディター**です。</span><span class="sxs-lookup"><span data-stu-id="f7369-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="f7369-141">選択、`Load`右のドロップダウン リストからのイベントです。</span><span class="sxs-lookup"><span data-stu-id="f7369-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="f7369-142">**コード エディター**開きます、`Form1_Load`イベント プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="f7369-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="f7369-143">次のコードを追加、`Form1_Load`イベントを作成する手順、 `Widget`:</span><span class="sxs-lookup"><span data-stu-id="f7369-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="f7369-144">このコードが実行されると、Visual Basic の作成、`Widget`オブジェクトをイベント 'éú' に関連付けられているイベント プロシージャ`mWidget`です。</span><span class="sxs-lookup"><span data-stu-id="f7369-144">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="f7369-145">した時点で、ときに、`Widget`を発生させますその`PercentDone`イベント、`mWidget_PercentDone`イベント プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7369-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="f7369-146">LongTask メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="f7369-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="f7369-147">`Button1_Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="f7369-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="f7369-148">前に、`LongTask`メソッドを呼び出すことは、完了した割合が表示されますが初期化する必要があります、ラベルと、クラス レベル`Boolean`フラグに設定する必要があります、メソッドの取り消し`False`です。</span><span class="sxs-lookup"><span data-stu-id="f7369-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="f7369-149">`LongTask` タスクの継続時間 12.2 秒の呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f7369-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="f7369-150">`PercentDone`イベントは、1 回すべて 3 分の 1 秒です。</span><span class="sxs-lookup"><span data-stu-id="f7369-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="f7369-151">イベントが発生するたびに、`mWidget_PercentDone`イベント プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7369-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="f7369-152">ときに`LongTask`が完了したら、`mblnCancel`かどうかをテスト`LongTask`通常は、終了したためが停止している場合、または`mblnCancel`に設定された`True`です。</span><span class="sxs-lookup"><span data-stu-id="f7369-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="f7369-153">前者の場合にのみ、完了したパーセントが更新されます。</span><span class="sxs-lookup"><span data-stu-id="f7369-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="f7369-154">プログラムを実行するには</span><span class="sxs-lookup"><span data-stu-id="f7369-154">To run the program</span></span>  
  
1.  <span data-ttu-id="f7369-155">F5 キーを押してプロジェクトを実行モードにします。</span><span class="sxs-lookup"><span data-stu-id="f7369-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="f7369-156">クリックして、**タスクの開始**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7369-156">Click the **Start Task** button.</span></span> <span data-ttu-id="f7369-157">毎回、`PercentDone`イベントは、ラベルは、タスクが完了の割合で更新します。</span><span class="sxs-lookup"><span data-stu-id="f7369-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="f7369-158">クリックして、**キャンセル**タスクを停止するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7369-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="f7369-159">注意しての外観、**キャンセル**ボタンをクリックすると、すぐには変化しません。</span><span class="sxs-lookup"><span data-stu-id="f7369-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="f7369-160">`Click`イベントまで発生することはできません、`My.Application.DoEvents`ステートメントにより、イベント処理します。</span><span class="sxs-lookup"><span data-stu-id="f7369-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7369-161">`My.Application.DoEvents`の形式として、メソッドがまったく同じ方法でイベントを処理できません。</span><span class="sxs-lookup"><span data-stu-id="f7369-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="f7369-162">たとえば、このチュートリアルでは、する必要があります をクリックして、**キャンセル**2 回ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7369-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="f7369-163">使用することができますを許可するフォームがイベントを直接処理する場合のマルチ スレッド化します。</span><span class="sxs-lookup"><span data-stu-id="f7369-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="f7369-164">詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)です。</span><span class="sxs-lookup"><span data-stu-id="f7369-164">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="f7369-165">F11 キーをプログラムを実行して、コードを 1 行ずつ処理するときにあります。</span><span class="sxs-lookup"><span data-stu-id="f7369-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="f7369-166">実行に入力する方法がわかります`LongTask`、し、簡単に再入力`Form1`たびに、`PercentDone`イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="f7369-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="f7369-167">何が起こる場合、実行中のコードに戻ってに`Form1`、`LongTask`メソッドが再び呼び出されたしますか?</span><span class="sxs-lookup"><span data-stu-id="f7369-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="f7369-168">場合、スタック オーバーフローが発生する最悪の場合、`LongTask`イベントが発生するたびに呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="f7369-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="f7369-169">変数が発生することができます`mWidget`別のイベントを処理する`Widget`新しいへの参照を割り当てることによってオブジェクト`Widget`に`mWidget`です。</span><span class="sxs-lookup"><span data-stu-id="f7369-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="f7369-170">実際には、内のコードを行うことができます`Button1_Click`ボタンをクリックするたびにこの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f7369-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="f7369-171">さまざまなウィジェットのイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="f7369-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="f7369-172">次のコード行を追加、`Button1_Click`を読み取る行のすぐ前の手順`mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="f7369-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="f7369-173">上記のコードが新たに作成`Widget`たびにこのボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f7369-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="f7369-174">すぐに、`LongTask`メソッドが完了するへの参照を`Widget`がリリースされると、`Widget`は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="f7369-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="f7369-175">A`WithEvents`変数は、一度に 1 つのオブジェクト参照を含めることができる場合は、異なるを割り当てるよう`Widget`オブジェクトを`mWidget`、前の`Widget`オブジェクトのイベントを処理しなくなります。</span><span class="sxs-lookup"><span data-stu-id="f7369-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="f7369-176">場合`mWidget`古いへの参照を含む唯一のオブジェクト変数`Widget`オブジェクトは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="f7369-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="f7369-177">いくつかからイベントを処理する場合`Widget`オブジェクトを使用して、`AddHandler`ステートメントを個別に各オブジェクトからのイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="f7369-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7369-178">だけを宣言できます`WithEvents`、として変数が必要なの配列が`WithEvents`変数はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="f7369-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7369-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7369-179">See Also</span></span>  
 [<span data-ttu-id="f7369-180">チュートリアル : イベントの宣言と発生</span><span class="sxs-lookup"><span data-stu-id="f7369-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="f7369-181">イベント</span><span class="sxs-lookup"><span data-stu-id="f7369-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
