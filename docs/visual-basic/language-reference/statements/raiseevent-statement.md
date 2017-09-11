---
title: "RaiseEvent ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
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
ms.openlocfilehash: 6a0cf1c5635335f22fddd57c7dd2baaeca6ddd23
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="raiseevent-statement"></a><span data-ttu-id="9c768-102">RaiseEvent ステートメント</span><span class="sxs-lookup"><span data-stu-id="9c768-102">RaiseEvent Statement</span></span>
<span data-ttu-id="9c768-103">クラス、フォーム、またはドキュメント内のモジュール レベルで宣言されているイベントをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="9c768-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c768-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c768-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="9c768-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9c768-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="9c768-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="9c768-106">Required.</span></span> <span data-ttu-id="9c768-107">トリガーするイベントの名前です。</span><span class="sxs-lookup"><span data-stu-id="9c768-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="9c768-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9c768-108">Optional.</span></span> <span data-ttu-id="9c768-109">変数、配列、または式のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="9c768-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="9c768-110">`argumentlist`引数をかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c768-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="9c768-111">引数がない場合は、かっこを省略する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c768-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c768-112">コメント</span><span class="sxs-lookup"><span data-stu-id="9c768-112">Remarks</span></span>  
 <span data-ttu-id="9c768-113">必要な`eventname`は、モジュール内で宣言されたイベントの名前。</span><span class="sxs-lookup"><span data-stu-id="9c768-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="9c768-114">これは、Visual Basic 変数の名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="9c768-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="9c768-115">イベントは発生のモジュール内で宣言されていない、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9c768-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="9c768-116">次のコード フラグメントでは、イベントの宣言と、イベントが発生する手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c768-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 <span data-ttu-id="9c768-117">[!code-vb[VbVbalrEvents #&37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c768-117">[!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="9c768-118">使用することはできません`RaiseEvent`モジュールで明示的に宣言されていないイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="9c768-118">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="9c768-119">たとえば、すべてのフォームの継承、<xref:System.Windows.Forms.Control.Click>からイベントを<xref:System.Windows.Forms.Form?displayProperty=fullName>を使用すると発生することはできません`RaiseEvent`派生フォームで</xref:System.Windows.Forms.Form?displayProperty=fullName></xref:System.Windows.Forms.Control.Click>。</span><span class="sxs-lookup"><span data-stu-id="9c768-119">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=fullName>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="9c768-120">宣言する場合、`Click`イベント モジュールでは、フォーム、フォーム自体のシャドウ<xref:System.Windows.Forms.Control.Click>イベント</xref:System.Windows.Forms.Control.Click>。</span><span class="sxs-lookup"><span data-stu-id="9c768-120">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="9c768-121">フォームを引き続き呼び出すことができます<xref:System.Windows.Forms.Control.Click>イベントを呼び出して、<xref:System.Windows.Forms.Control.OnClick%2A>メソッド</xref:System.Windows.Forms.Control.OnClick%2A></xref:System.Windows.Forms.Control.Click>。</span><span class="sxs-lookup"><span data-stu-id="9c768-121">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="9c768-122">既定では、Visual Basic で定義されたイベントは、接続が確立されている順序では、そのイベント ハンドラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="9c768-122">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="9c768-123">イベントがあるため`ByRef`パラメーター、接続するプロセスは以前のイベント ハンドラーによって変更されているパラメーターを受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="9c768-123">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="9c768-124">イベント ハンドラーの実行後は、イベントを発生させたサブルーチンに制御が返されます。</span><span class="sxs-lookup"><span data-stu-id="9c768-124">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c768-125">非共有イベントが宣言されているクラスのコンス トラクター内で発生しない必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c768-125">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="9c768-126">このようなイベントでは、実行時エラーが発生しない、関連付けられたイベント ハンドラーでキャッチできる、されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c768-126">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="9c768-127">使用して、`Shared`修飾子をコンス トラクターからイベントを発生させる必要がある場合は、共有のイベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9c768-127">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c768-128">イベントの既定の動作を変更するには、カスタム イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="9c768-128">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="9c768-129">カスタム イベントの場合、`RaiseEvent`ステートメントで呼び出されるイベントの`RaiseEvent`アクセサー。</span><span class="sxs-lookup"><span data-stu-id="9c768-129">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="9c768-130">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="9c768-130">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c768-131">例</span><span class="sxs-lookup"><span data-stu-id="9c768-131">Example</span></span>  
 <span data-ttu-id="9c768-132">次の例では、イベントを使用して 10 秒から 0 秒までカウント ダウンします。</span><span class="sxs-lookup"><span data-stu-id="9c768-132">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="9c768-133">コードに示すいくつかのイベントに関連するメソッド、プロパティ、およびなど、ステートメント、`RaiseEvent`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="9c768-133">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="9c768-134">イベントを発生させるクラスをイベント ソース、イベントを処理するメソッドをイベント ハンドラーと呼びます。</span><span class="sxs-lookup"><span data-stu-id="9c768-134">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="9c768-135">イベント ソースでは、生成されるイベントに対して複数のイベント ハンドラーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="9c768-135">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="9c768-136">クラスでイベントが発生すると、そのイベントは、オブジェクトのインスタンスに対するイベントを処理するために選択されたすべてのクラスで発生します。</span><span class="sxs-lookup"><span data-stu-id="9c768-136">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="9c768-137">また、この例では、ボタン (`Button1`) とテキスト ボックス (`TextBox1`) を含んだフォーム (`Form1`) も使用しています。</span><span class="sxs-lookup"><span data-stu-id="9c768-137">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="9c768-138">ボタンをクリックすると、1 つ目のテキスト ボックスに 10 秒から 0 秒までのカウントダウンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c768-138">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="9c768-139">カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c768-139">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="9c768-140">`Form1` のコードでは、フォームの初期状態と終了状態を指定しています。</span><span class="sxs-lookup"><span data-stu-id="9c768-140">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="9c768-141">イベント発生時に実行されるコードも含まれています。</span><span class="sxs-lookup"><span data-stu-id="9c768-141">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="9c768-142">この例を使用する新しい Windows アプリケーション プロジェクトを開き、という名前のボタンを追加`Button1`とという名前のテキスト ボックス`TextBox1`という名前のメイン フォームに`Form1`します。</span><span class="sxs-lookup"><span data-stu-id="9c768-142">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="9c768-143">フォームを右クリックし、をクリックし、**コードの表示**コード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="9c768-143">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="9c768-144">追加、`WithEvents`変数の宣言セクションに、`Form1`クラスです。</span><span class="sxs-lookup"><span data-stu-id="9c768-144">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 <span data-ttu-id="9c768-145">[!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c768-145">[!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c768-146">例</span><span class="sxs-lookup"><span data-stu-id="9c768-146">Example</span></span>  
 <span data-ttu-id="9c768-147">`Form1` のコードに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9c768-147">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="9c768-148">など、存在するすべての重複するプロシージャを置き換える`Form_Load`、または`Button_Click`です。</span><span class="sxs-lookup"><span data-stu-id="9c768-148">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 <span data-ttu-id="9c768-149">[!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="9c768-149">[!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="9c768-150">前の例を実行 ボタンをクリックして f5 キーを押して**開始**します。</span><span class="sxs-lookup"><span data-stu-id="9c768-150">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="9c768-151">最初のテキスト ボックスで、秒のカウント ダウンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="9c768-151">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="9c768-152">カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c768-152">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c768-153">`My.Application.DoEvents`フォームは、メソッドがまったく同じ方法でイベントを処理できません。</span><span class="sxs-lookup"><span data-stu-id="9c768-153">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="9c768-154">使用できるイベントを直接処理するためのフォームを許可するようにマルチ スレッドです。</span><span class="sxs-lookup"><span data-stu-id="9c768-154">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="9c768-155">詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)します。</span><span class="sxs-lookup"><span data-stu-id="9c768-155">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c768-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c768-156">See Also</span></span>  
 <span data-ttu-id="9c768-157">[イベント](../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="9c768-157">[Events](../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="9c768-158"> [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c768-158"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="9c768-159"> [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c768-159"> [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="9c768-160"> [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9c768-160"> [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="9c768-161"> [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md)</span><span class="sxs-lookup"><span data-stu-id="9c768-161"> [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)</span></span>
