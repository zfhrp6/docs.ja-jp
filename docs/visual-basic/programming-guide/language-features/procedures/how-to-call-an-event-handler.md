---
title: "方法: Visual Basic でイベント ハンドラーを呼び出す |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- event handlers, calling
- event handlers
- procedures, event handlers
- procedures, calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
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
ms.openlocfilehash: dc0174d50c7b5f5cda9d057bce39960b3e563f4e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="d9859-102">方法 : Visual Basic でイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="d9859-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="d9859-103">*イベント*操作または発生は、-など、マウス クリックするか、与信限度を超えています: 認識コードを記述できる、いくつかのプログラム コンポーネントによって応答します。</span><span class="sxs-lookup"><span data-stu-id="d9859-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="d9859-104">*イベント ハンドラー*イベントに応答を記述するコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d9859-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="d9859-105">イベント ハンドラーに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d9859-105">An event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="d9859-106">ただし、通常呼び出さないことと同じ方法の`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d9859-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="d9859-107">代わりに、イベントのハンドラーとプロシージャを識別します。</span><span class="sxs-lookup"><span data-stu-id="d9859-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="d9859-108">これを行うか、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句と[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)変数、または、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d9859-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="d9859-109">使用して、`Handles`句内のイベント ハンドラーを宣言する既定の方法は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="d9859-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="d9859-110">これは、統合開発環境 (IDE) でプログラミングするときに、デザイナーによって、イベント ハンドラーが書き込まれる方法です。</span><span class="sxs-lookup"><span data-stu-id="d9859-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="d9859-111">`AddHandler`ステートメントが実行時に動的にイベントを発生させるために適しています。</span><span class="sxs-lookup"><span data-stu-id="d9859-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="d9859-112">イベントが発生したときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的にイベント ハンドラーのプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d9859-112">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="d9859-113">イベントにアクセスできる任意のコードは実行することによって発生するようを原因となる、 [RaiseEvent ステートメント](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d9859-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="d9859-114">同じイベントには、1 つ以上のイベント ハンドラーを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d9859-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="d9859-115">場合によっては、イベントからハンドラーを切り離すこともできます。</span><span class="sxs-lookup"><span data-stu-id="d9859-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="d9859-116">詳細については、次を参照してください。[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9859-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="d9859-117">ハンドルおよび WithEvents を使用してイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="d9859-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="d9859-118">で、イベントが宣言されていることを確認、 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d9859-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="d9859-119">レベルを使用して、クラス、モジュールまたはオブジェクト変数を宣言、 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="d9859-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="d9859-120">`As`この変数は、イベントを発生させるクラスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9859-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="d9859-121">イベント処理の宣言で`Sub`の手順を追加、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句を指定する、`WithEvents`変数、およびイベント名。</span><span class="sxs-lookup"><span data-stu-id="d9859-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="d9859-122">イベントが発生したときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を自動的に呼び出して、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d9859-122">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="d9859-123">コードを使用して、`RaiseEvent`ステートメントが発生するイベントをします。</span><span class="sxs-lookup"><span data-stu-id="d9859-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="d9859-124">次の例は、イベントを定義し、`WithEvents`イベントを発生させるクラスを参照する変数。</span><span class="sxs-lookup"><span data-stu-id="d9859-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="d9859-125">イベント処理`Sub`プロシージャは、`Handles`句クラスとイベントの処理を指定します。</span><span class="sxs-lookup"><span data-stu-id="d9859-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     <span data-ttu-id="d9859-126">[!code-vb[VbVbcnProcedures&4;](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d9859-126">[!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]</span></span>  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="d9859-127">AddHandler を使用してイベント ハンドラーを呼び出す</span><span class="sxs-lookup"><span data-stu-id="d9859-127">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="d9859-128">で、イベントが宣言されていることを確認、`Event`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d9859-128">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="d9859-129">実行、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)イベント処理を動的に接続する`Sub`イベントにプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d9859-129">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="d9859-130">イベントが発生したときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を自動的に呼び出して、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d9859-130">When the event occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="d9859-131">コードを使用して、`RaiseEvent`ステートメントが発生するイベントをします。</span><span class="sxs-lookup"><span data-stu-id="d9859-131">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="d9859-132">次の例、`Sub`を処理する手順、<xref:System.Windows.Forms.Form.Closing>フォームのイベント</xref:System.Windows.Forms.Form.Closing>。</span><span class="sxs-lookup"><span data-stu-id="d9859-132">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="d9859-133">次を使用して、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)に関連付けるには、 `catchClose` <xref:System.Windows.Forms.Form.Closing>.</xref:System.Windows.Forms.Form.Closing>のイベント ハンドラーとプロシージャ</span><span class="sxs-lookup"><span data-stu-id="d9859-133">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     <span data-ttu-id="d9859-134">[!code-vb[VbVbcnProcedures&#5;](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d9859-134">[!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]</span></span>  
  
     <span data-ttu-id="d9859-135">実行することによって、イベントからイベント ハンドラーを切り離すこともできます、 [RemoveHandler ステートメント](../../../../visual-basic/language-reference/statements/removehandler-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d9859-135">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9859-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9859-136">See Also</span></span>  
 <span data-ttu-id="d9859-137">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="d9859-137">[Procedures](./index.md) </span></span>  
<span data-ttu-id="d9859-138"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d9859-138"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="d9859-139"> [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d9859-139"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="d9859-140"> [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="d9859-140"> [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="d9859-141"> [方法: プロシージャを作成します。](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d9859-141"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="d9859-142"> [方法 : 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="d9859-142"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md)</span></span>
