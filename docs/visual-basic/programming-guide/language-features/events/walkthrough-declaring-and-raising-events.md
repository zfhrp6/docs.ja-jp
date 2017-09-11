---
title: "宣言と発生 (Visual Basic) のイベント |Microsoft ドキュメント"
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
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
ms.openlocfilehash: eca112aca39bd998697d379a1705845e8f607367
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="ac01c-102">チュートリアル: イベントの宣言と発生 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac01c-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="ac01c-103">このチュートリアルを宣言してという名前のクラスのイベントを発生させる方法について説明`Widget`します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="ac01c-104">手順を完了すると後、は、関連トピックを確認することができます[チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)からのイベントを使用する方法を説明`Widget`アプリケーションで、状態情報を入力するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="ac01c-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="ac01c-105">Widget クラス</span><span class="sxs-lookup"><span data-stu-id="ac01c-105">The Widget Class</span></span>  
 <span data-ttu-id="ac01c-106">想定した、`Widget`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="ac01c-107">`Widget`クラスに実行するには時間が長くなるメソッドとする場合、アプリケーションが何らかの完了のインジケーターを配置することです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="ac01c-108">もちろん、行うことができます、`Widget`オブジェクト % 完了ダイアログ ボックスの表示が、そのダイアログ ボックスを使用するすべてのプロジェクトで使用するスタックするし、`Widget`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="ac01c-109">オブジェクト設計の原則は、オブジェクト ハンドル ユーザー インターフェイスを使用して、アプリケーションは、オブジェクトの全体の目的は、フォームまたはダイアログ ボックスを管理する場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="ac01c-110">目的は、`Widget`を追加することが、その他のタスクを実行することです、`PercentDone`イベントおよび let を呼び出すプロシージャ`Widget`メソッド処理がイベントと表示の状態を更新します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="ac01c-111">`PercentDone`イベントは、タスクのキャンセル メカニズムも提供できます。</span><span class="sxs-lookup"><span data-stu-id="ac01c-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="ac01c-112">このトピックのコード例をビルドするには</span><span class="sxs-lookup"><span data-stu-id="ac01c-112">To build the code example for this topic</span></span>  
  
1.  <span data-ttu-id="ac01c-113">新しい[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows アプリケーション プロジェクトし、という名前のフォームを作成する`Form1`です。</span><span class="sxs-lookup"><span data-stu-id="ac01c-113">Open a new [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] Windows Application project and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="ac01c-114">2 つのボタンとラベルを追加`Form1`します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-114">Add two buttons and a label to `Form1`.</span></span>  
  
3.  <span data-ttu-id="ac01c-115">次の表に示すように、オブジェクトの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="ac01c-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="ac01c-116">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ac01c-116">Object</span></span>|<span data-ttu-id="ac01c-117">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ac01c-117">Property</span></span>|<span data-ttu-id="ac01c-118">設定</span><span class="sxs-lookup"><span data-stu-id="ac01c-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="ac01c-119">開始タスク</span><span class="sxs-lookup"><span data-stu-id="ac01c-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="ac01c-120">キャンセル</span><span class="sxs-lookup"><span data-stu-id="ac01c-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="ac01c-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="ac01c-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="ac01c-122">lblPercentDone 0</span><span class="sxs-lookup"><span data-stu-id="ac01c-122">lblPercentDone, 0</span></span>|  
  
4.  <span data-ttu-id="ac01c-123">**プロジェクト**] メニューの [選択**クラスの追加**という名前のクラスを追加する`Widget.vb`をプロジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="ac01c-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="ac01c-124">ウィジェット クラスのイベントを宣言するには</span><span class="sxs-lookup"><span data-stu-id="ac01c-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="ac01c-125">使用して、`Event`でイベントを宣言するキーワード、`Widget`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="ac01c-126">イベントがあることに注意してください`ByVal`と`ByRef`、引数として`Widget`の`PercentDone`イベントを示しています。</span><span class="sxs-lookup"><span data-stu-id="ac01c-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     <span data-ttu-id="ac01c-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac01c-127">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]</span></span>  
  
 <span data-ttu-id="ac01c-128">呼び出し元のオブジェクトを受信すると、 `PercentDone` 、イベント、`Percent`引数には、タスクが完了の割合が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ac01c-128">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="ac01c-129">`Cancel`引数に設定することができます`True`イベントを発生させたメソッドをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="ac01c-129">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac01c-130">イベント引数を宣言するには、次の例外を除き、プロシージャ引数の場合と同様。 イベントを使用できない`Optional`または`ParamArray`引数、およびイベントには戻り値がないです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-130">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="ac01c-131">`PercentDone`によってイベントが発生した、`LongTask`のメソッド、`Widget`クラスです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-131">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="ac01c-132">`LongTask`2 つの引数: 時間の長さメソッドが行う作業、および前に最小の時間間隔を装う`LongTask`させる一時停止、`PercentDone`イベントです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-132">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="ac01c-133">ですイベントを生成するには</span><span class="sxs-lookup"><span data-stu-id="ac01c-133">To raise the PercentDone event</span></span>  
  
1.  <span data-ttu-id="ac01c-134">アクセスを簡略化する、`Timer`このクラスによって使用されるプロパティを追加、`Imports`ステートメントをクラス モジュールの宣言セクションの上部に上、`Class Widget`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-134">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     <span data-ttu-id="ac01c-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac01c-135">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]</span></span>  
  
2.  <span data-ttu-id="ac01c-136">`Widget` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-136">Add the following code to the `Widget` class:</span></span>  
  
     <span data-ttu-id="ac01c-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac01c-137">[!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]</span></span>  
  
 <span data-ttu-id="ac01c-138">アプリケーションを呼び出すと、 `LongTask` 、メソッド、`Widget`クラスが生成、`PercentDone`イベントすべて`MinimumInterval`秒です。</span><span class="sxs-lookup"><span data-stu-id="ac01c-138">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="ac01c-139">イベントが返されるときに`LongTask`かどうかをチェック、`Cancel`引数に設定された`True`します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-139">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="ac01c-140">いくつかの免責事項は、ここで必要です。</span><span class="sxs-lookup"><span data-stu-id="ac01c-140">A few disclaimers are necessary here.</span></span> <span data-ttu-id="ac01c-141">簡略化のため、`LongTask`手順では、事前にわかってタスクにかかるものとします。</span><span class="sxs-lookup"><span data-stu-id="ac01c-141">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="ac01c-142">これは、ケースではほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="ac01c-142">This is almost never the case.</span></span> <span data-ttu-id="ac01c-143">何かが起こっているかを示す値を取得するまでに経過する時間数だけでは、多くの場合、最も重要な要素をユーザーに、タスクを均等なサイズのチャンクに分割することは困難ですが、できます。</span><span class="sxs-lookup"><span data-stu-id="ac01c-143">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="ac01c-144">このサンプルでは別の問題を見つけられたら可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac01c-144">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="ac01c-145">`Timer`プロパティには、午前&0; 時から経過した秒数が返されます。 そのため、アプリケーションから抜け出せなく直前の午前&0; 時に起動された場合。</span><span class="sxs-lookup"><span data-stu-id="ac01c-145">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="ac01c-146">時間の計測をより慎重な方法はこのなどを考慮に入れるの境界条件に入れるかなどのプロパティを使用して`Now`します。</span><span class="sxs-lookup"><span data-stu-id="ac01c-146">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="ac01c-147">これで、`Widget`クラスには、イベントを発生させて、次のように次のチュートリアルに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="ac01c-147">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="ac01c-148">[チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)を使用する方法を示します`WithEvents`に、イベント ハンドラーを関連付けるには、`PercentDone`イベントです。</span><span class="sxs-lookup"><span data-stu-id="ac01c-148">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac01c-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac01c-149">See Also</span></span>  
 <span data-ttu-id="ac01c-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span><span class="sxs-lookup"><span data-stu-id="ac01c-150"><xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></span></span>   
 <span data-ttu-id="ac01c-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="ac01c-151"><xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span></span>   
<span data-ttu-id="ac01c-152"> [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span><span class="sxs-lookup"><span data-stu-id="ac01c-152"> [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) </span></span>  
<span data-ttu-id="ac01c-153"> [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="ac01c-153"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
