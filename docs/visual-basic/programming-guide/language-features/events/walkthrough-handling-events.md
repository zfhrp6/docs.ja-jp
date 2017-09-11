---
title: "イベントの処理 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b4ad77b3b0236e762fc17b8aba9d34108c8d75b5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="e90e2-102">チュートリアル: イベントの処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e90e2-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="e90e2-103">これは、2 番目のイベントを使用する方法を示す&2; つのトピックです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="e90e2-104">最初のトピックでは、[チュートリアル: イベントの宣言と発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)を宣言し、イベントを発生させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="e90e2-105">このセクションでは、フォームとそのチュートリアルからクラスを使用して、行われるときにイベントを処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="e90e2-106">`Widget`クラスの例は、従来のイベント処理のステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-106">The `Widget` class example uses traditional event-handling statements.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="e90e2-107">イベントを操作するためには、その他の手法を提供します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-107"> provides other techniques for working with events.</span></span> <span data-ttu-id="e90e2-108">演習として使用するには、この例を変更することができます、`AddHandler`と`Handles`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="e90e2-109">ウィジェット クラスのことですイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="e90e2-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="e90e2-110">次のコードを配置`Form1`:</span><span class="sxs-lookup"><span data-stu-id="e90e2-110">Place the following code in `Form1`:</span></span>  
  
     <span data-ttu-id="e90e2-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e90e2-111">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]</span></span>  
  
     <span data-ttu-id="e90e2-112">`WithEvents`キーワードを指定する変数`mWidget`オブジェクトのイベントを処理するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="e90e2-113">オブジェクトの種類を指定するには、オブジェクトの作成元となるクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="e90e2-114">変数`mWidget`で宣言された`Form1`ため`WithEvents`変数はクラス レベルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e90e2-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="e90e2-115">これは配置することでクラスの種類に関係なく当てはまります。</span><span class="sxs-lookup"><span data-stu-id="e90e2-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="e90e2-116">変数`mblnCancel`、キャンセルに使用、`LongTask`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="e90e2-117">イベントを処理するコードの記述</span><span class="sxs-lookup"><span data-stu-id="e90e2-117">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="e90e2-118">使用して変数を宣言するとすぐに`WithEvents`、クラスの左側のドロップダウン リストに表示される変数名**コード エディター**します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="e90e2-119">選択すると`mWidget`、`Widget`クラスのイベントが右のドロップダウン リストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="e90e2-120">イベントの対応するプロシージャのプレフィックスを持つイベントを選択すると表示`mWidget`とアンダー スコア。</span><span class="sxs-lookup"><span data-stu-id="e90e2-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="e90e2-121">関連付けられているすべてのイベント プロシージャ、`WithEvents`変数は、プレフィックスとして変数名に付与されます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="e90e2-122">イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="e90e2-122">To handle an event</span></span>  
  
1.  <span data-ttu-id="e90e2-123">選択`mWidget`で、左側のドロップダウン リストから、**コード エディター**します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="e90e2-124">選択、`PercentDone`右のドロップダウン リストからのイベントです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="e90e2-125">**コード エディター**が開き、`mWidget_PercentDone`イベント プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e90e2-126">**コード エディター**は役立ちますが、必須ではない新しいイベント ハンドラーを挿入するためです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="e90e2-127">このチュートリアルでは、イベント ハンドラーのコードに直接コピーするより直接的です。</span><span class="sxs-lookup"><span data-stu-id="e90e2-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="e90e2-128">`mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     <span data-ttu-id="e90e2-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e90e2-129">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]</span></span>  
  
     <span data-ttu-id="e90e2-130">ときに、`PercentDone`イベントは、イベント プロシージャが完了の割合を表示、`Label`コントロールです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-130">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="e90e2-131">`DoEvents`メソッドを使用して、ラベルを再描画し、また、ユーザーがクリックすること、**キャンセル** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-131">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="e90e2-132">次のコードを追加、`Button2_Click`イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="e90e2-132">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     <span data-ttu-id="e90e2-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e90e2-133">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]</span></span>  
  
 <span data-ttu-id="e90e2-134">ユーザーがクリックした場合、**キャンセル**中にボタン`LongTask`が実行されている、`Button2_Click`イベントが実行されるとすぐに、`DoEvents`ステートメントで発生するイベントの処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-134">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="e90e2-135">クラス レベルの変数`mblnCancel`に設定されている`True`、および`mWidget_PercentDone`イベントことをテストし、設定、`ByRef Cancel`引数`True`します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-135">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="e90e2-136">WithEvents 変数をオブジェクトに接続します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-136">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="e90e2-137">`Form1`今すぐ処理する設定、`Widget`オブジェクトのイベントです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-137">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="e90e2-138">あとは検索する、`Widget`どこかにします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-138">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="e90e2-139">変数を宣言するときに`WithEvents`デザイン時にオブジェクトが関連付けられていないことです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-139">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="e90e2-140">A`WithEvents`変数は、その他のすべてのオブジェクト変数と同じようにします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-140">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="e90e2-141">オブジェクトを作成してにへの参照を割り当てる必要がある、`WithEvents`変数です。</span><span class="sxs-lookup"><span data-stu-id="e90e2-141">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="e90e2-142">オブジェクトを作成してへの参照を割り当てる</span><span class="sxs-lookup"><span data-stu-id="e90e2-142">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="e90e2-143">選択**(Form1 イベント)**で、左側のドロップダウン リストから、**コード エディター**します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-143">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="e90e2-144">選択、`Load`右のドロップダウン リストからのイベントです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-144">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="e90e2-145">**コード エディター**が開き、`Form1_Load`イベント プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-145">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="e90e2-146">次のコードを追加、`Form1_Load`イベントを作成する手順、 `Widget`:</span><span class="sxs-lookup"><span data-stu-id="e90e2-146">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     <span data-ttu-id="e90e2-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e90e2-147">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]</span></span>  
  
 <span data-ttu-id="e90e2-148">このコードの実行時に[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を作成、`Widget`オブジェクトおよびに関連付けられているイベント プロシージャにそのイベントを接続する`mWidget`です。</span><span class="sxs-lookup"><span data-stu-id="e90e2-148">When this code executes, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="e90e2-149">した時点で、ときに、`Widget`を発生させますその`PercentDone`、イベント、`mWidget_PercentDone`イベント プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-149">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="e90e2-150">LongTask メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="e90e2-150">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="e90e2-151">`Button1_Click` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-151">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     <span data-ttu-id="e90e2-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="e90e2-152">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]</span></span>  
  
 <span data-ttu-id="e90e2-153">前に、`LongTask`メソッドが呼び出されるラベルの表示が完了した割合を初期化する必要があり、クラス レベル`Boolean`フラグに設定するメソッドをキャンセルする必要があります`False`します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-153">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="e90e2-154">`LongTask`12.2 秒のタスクの実行時間と呼びます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-154">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="e90e2-155">`PercentDone`イベントは、1 回ごと&3; 分の&1; 秒です。</span><span class="sxs-lookup"><span data-stu-id="e90e2-155">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="e90e2-156">このイベントが発生するたびに、`mWidget_PercentDone`イベント プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-156">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="e90e2-157">`LongTask`が完了したら、`mblnCancel`かどうかをテスト`LongTask`通常は、終了したためが停止している場合、または`mblnCancel`に設定されている`True`します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-157">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="e90e2-158">前者の場合にのみ、完了したパーセントが更新されます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-158">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="e90e2-159">プログラムを実行するには</span><span class="sxs-lookup"><span data-stu-id="e90e2-159">To run the program</span></span>  
  
1.  <span data-ttu-id="e90e2-160">F5 キーを押して、プロジェクトを実行モードにします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-160">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="e90e2-161">クリックして、**タスクの開始** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-161">Click the **Start Task** button.</span></span> <span data-ttu-id="e90e2-162">毎回、`PercentDone`イベントは、タスクが完了の割合でラベルを更新します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-162">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="e90e2-163">クリックして、**キャンセル**タスクを停止する ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-163">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="e90e2-164">注意しての外観、**キャンセル**ボタンでは、クリックするとすぐには変化しません。</span><span class="sxs-lookup"><span data-stu-id="e90e2-164">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="e90e2-165">`Click`までイベントが発生しない、`My.Application.DoEvents`ステートメントでは、イベント処理を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-165">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e90e2-166">`My.Application.DoEvents`フォームは、メソッドがまったく同じ方法でイベントを処理できません。</span><span class="sxs-lookup"><span data-stu-id="e90e2-166">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="e90e2-167">たとえば、このチュートリアルでをクリックして、**キャンセル**2 回ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-167">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="e90e2-168">使用できるイベントを直接処理するためのフォームを許可するようにマルチ スレッドです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-168">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="e90e2-169">詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-169">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="e90e2-170">F11 キーで、プログラムを実行し、コードを&1; 行ずつ処理するときにあります。</span><span class="sxs-lookup"><span data-stu-id="e90e2-170">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="e90e2-171">実行に入力する方法がわかります`LongTask`、し、簡単に再入力`Form1`たびに、`PercentDone`イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-171">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="e90e2-172">何が起こる場合、実行中のコードに戻る`Form1`、`LongTask`メソッドが再び呼び出されるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e90e2-172">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="e90e2-173">場合、スタック オーバーフローが発生する最悪の場合、`LongTask`イベントが発生するたびに呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="e90e2-173">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="e90e2-174">変数が発生することができます`mWidget`、別のイベントを処理する`Widget`新しいへの参照を割り当てることによってオブジェクト`Widget`に`mWidget`します。</span><span class="sxs-lookup"><span data-stu-id="e90e2-174">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="e90e2-175">実際には、コードを行うことができます`Button1_Click`ボタンをクリックするたびにこの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="e90e2-175">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="e90e2-176">さまざまなウィジェットのイベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="e90e2-176">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="e90e2-177">次のコード行を追加、`Button1_Click`という行を前の手順`mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="e90e2-177">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     <span data-ttu-id="e90e2-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="e90e2-178">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]</span></span>  
  
 <span data-ttu-id="e90e2-179">上記のコードが、新たに作成`Widget`たびにこのボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e90e2-179">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="e90e2-180">すぐに、`LongTask`メソッドが完了するへの参照、`Widget`がリリースされると、`Widget`が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-180">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="e90e2-181">A`WithEvents`変数は、一度に&1; つのオブジェクト参照を含めることができますので、異なるを割り当てる場合`Widget`オブジェクトを`mWidget`、前の`Widget`オブジェクトのイベントを処理できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e90e2-181">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="e90e2-182">場合`mWidget`古いへの参照を含む唯一のオブジェクト変数`Widget`オブジェクトは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="e90e2-182">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="e90e2-183">いくつかのイベントを処理する場合は、`Widget`オブジェクトを使用して、`AddHandler`とは別に各オブジェクトからイベントを処理するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e90e2-183">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e90e2-184">だけを宣言する`WithEvents`変数としてする必要があるの配列が`WithEvents`変数がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e90e2-184">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90e2-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="e90e2-185">See Also</span></span>  
 <span data-ttu-id="e90e2-186">[チュートリアル: 宣言とイベントを発生させる](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span><span class="sxs-lookup"><span data-stu-id="e90e2-186">[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md) </span></span>  
<span data-ttu-id="e90e2-187"> [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="e90e2-187"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
