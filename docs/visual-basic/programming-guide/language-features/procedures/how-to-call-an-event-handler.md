---
title: '方法 : Visual Basic でイベント ハンドラーを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 4e6aeaee8027e462dcdf80cae34b4b246fd58cf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652683"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="586bd-102">方法 : Visual Basic でイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="586bd-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="586bd-103">*イベント*アクションまたはイベントの発生は、-、マウスなどクリックやクレジットの上限を超えています: 認識によってプログラム コンポーネントによって、コードを記述できます応答します。</span><span class="sxs-lookup"><span data-stu-id="586bd-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="586bd-104">*イベント ハンドラー*イベントに応答を記述するコードです。</span><span class="sxs-lookup"><span data-stu-id="586bd-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="586bd-105">Visual Basic でイベント ハンドラーは、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="586bd-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="586bd-106">ただし、通常呼び出さないことと同じ方法とその他の`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="586bd-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="586bd-107">代わりに、イベントのハンドラーとしてプロシージャを識別します。</span><span class="sxs-lookup"><span data-stu-id="586bd-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="586bd-108">これを行うか、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句と[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)変数、または、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="586bd-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="586bd-109">使用して、`Handles`句は、Visual Basic では、イベント ハンドラーを宣言する既定の方法です。</span><span class="sxs-lookup"><span data-stu-id="586bd-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="586bd-110">これは、統合開発環境 (IDE) でプログラミングするときにイベント ハンドラーが、デザイナーによって書き込まれる方法です。</span><span class="sxs-lookup"><span data-stu-id="586bd-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="586bd-111">`AddHandler`ステートメントが実行時に動的にイベントを発生させるために適しています。</span><span class="sxs-lookup"><span data-stu-id="586bd-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="586bd-112">イベントが発生すると、Visual Basic は自動的にイベント ハンドラーのプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="586bd-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="586bd-113">イベントへのアクセスを持つあらゆるコードそれが原因で実行することによって発生する、 [RaiseEvent ステートメント](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="586bd-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="586bd-114">同じイベントには、1 つ以上のイベント ハンドラーを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="586bd-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="586bd-115">場合によっては、イベントからハンドラーを切り離すこともできます。</span><span class="sxs-lookup"><span data-stu-id="586bd-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="586bd-116">詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="586bd-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="586bd-117">ハンドルおよび WithEvents を使用して、イベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="586bd-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="586bd-118">必ず、イベントが、 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="586bd-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="586bd-119">レベルを使用して、クラス、モジュールまたはオブジェクト変数を宣言、 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="586bd-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="586bd-120">`As`この変数は、イベントを発生させるクラスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="586bd-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="586bd-121">イベント処理の宣言で`Sub`の手順を追加、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句を指定する、`WithEvents`変数、およびイベント名。</span><span class="sxs-lookup"><span data-stu-id="586bd-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="586bd-122">Visual Basic を自動的に呼び出して、イベントの発生時に、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="586bd-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="586bd-123">コードを使用して、`RaiseEvent`ステートメントに発生するイベントです。</span><span class="sxs-lookup"><span data-stu-id="586bd-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="586bd-124">次の例は、イベントを定義し、`WithEvents`イベントを発生させるクラスを参照する変数。</span><span class="sxs-lookup"><span data-stu-id="586bd-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="586bd-125">イベント処理`Sub`プロシージャの使用、`Handles`句をクラスと処理イベントを指定します。</span><span class="sxs-lookup"><span data-stu-id="586bd-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="586bd-126">AddHandler を使用して、イベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="586bd-126">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="586bd-127">必ず、イベントが、`Event`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="586bd-127">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="586bd-128">実行、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)イベント処理を動的に接続する`Sub`イベントを持つプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="586bd-128">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="586bd-129">Visual Basic を自動的に呼び出して、イベントの発生時に、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="586bd-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="586bd-130">コードを使用して、`RaiseEvent`ステートメントに発生するイベントです。</span><span class="sxs-lookup"><span data-stu-id="586bd-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="586bd-131">次の例では定義、`Sub`を処理するプロシージャ、<xref:System.Windows.Forms.Form.Closing>フォームのイベントです。</span><span class="sxs-lookup"><span data-stu-id="586bd-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="586bd-132">次を使用して、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)に関連付けるには、`catchClose`のイベント ハンドラーとプロシージャ<xref:System.Windows.Forms.Form.Closing>です。</span><span class="sxs-lookup"><span data-stu-id="586bd-132">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     <span data-ttu-id="586bd-133">実行することによってイベントからイベント ハンドラーの関連付けを解除することができます、 [RemoveHandler ステートメント](../../../../visual-basic/language-reference/statements/removehandler-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="586bd-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586bd-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="586bd-134">See Also</span></span>  
 [<span data-ttu-id="586bd-135">手順</span><span class="sxs-lookup"><span data-stu-id="586bd-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="586bd-136">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="586bd-136">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="586bd-137">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="586bd-137">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="586bd-138">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="586bd-138">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="586bd-139">方法 : プロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="586bd-139">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="586bd-140">方法 : 値を返さないプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="586bd-140">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
