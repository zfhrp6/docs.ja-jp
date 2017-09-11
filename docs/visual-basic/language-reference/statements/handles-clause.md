---
title: "Handles 句 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
dev_langs:
- VB
helpviewer_keywords:
- Handles keyword
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: cd5dec12312e05242551d5aff112028a8e1ff8b3
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="5144b-102">Handles 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5144b-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="5144b-103">プロシージャが指定されたイベントを処理することを宣言します。</span><span class="sxs-lookup"><span data-stu-id="5144b-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5144b-104">構文</span><span class="sxs-lookup"><span data-stu-id="5144b-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="5144b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="5144b-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="5144b-106">イベントを処理するプロシージャの `Sub` プロシージャ宣言。</span><span class="sxs-lookup"><span data-stu-id="5144b-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="5144b-107">コンマで区切られた、`proceduredeclaration` が処理するイベントの一覧。</span><span class="sxs-lookup"><span data-stu-id="5144b-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="5144b-108">イベントは、現在のクラスの基底クラス、または `WithEvents` キーワードを使用して宣言されたオブジェクトによって発生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5144b-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5144b-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5144b-109">Remarks</span></span>  
 <span data-ttu-id="5144b-110">プロシージャ宣言の最後で `Handles` キーワードを使用すると、 `WithEvents` キーワードで宣言されたオブジェクト変数によって発生したイベントが処理されるようになります。</span><span class="sxs-lookup"><span data-stu-id="5144b-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="5144b-111">また、`Handles` キーワードを派生クラスで使用すると、基底クラスからのイベントを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="5144b-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="5144b-112">`Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。</span><span class="sxs-lookup"><span data-stu-id="5144b-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="5144b-113">`Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="5144b-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="5144b-114">`AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。</span><span class="sxs-lookup"><span data-stu-id="5144b-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="5144b-115">詳細については、次を参照してください。 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="5144b-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="5144b-116">カスタム イベントの場合、アプリケーションは、プロシージャをイベント ハンドラーとして追加するときにイベントの `AddHandler` アクセサーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5144b-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="5144b-117">カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="5144b-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5144b-118">例</span><span class="sxs-lookup"><span data-stu-id="5144b-118">Example</span></span>  
 <span data-ttu-id="5144b-119">[!code-vb[VbVbalrEvents&#2;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5144b-119">[!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]</span></span>  
  
 <span data-ttu-id="5144b-120">派生クラスで `Handles` ステートメントを使用して基底クラスからのイベントを処理する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5144b-120">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 <span data-ttu-id="5144b-121">[!code-vb[VbVbalrEvents&#3;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5144b-121">[!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5144b-122">例</span><span class="sxs-lookup"><span data-stu-id="5144b-122">Example</span></span>  
 <span data-ttu-id="5144b-123">次の例は、2 つのボタンのイベント ハンドラーの**WPF アプリケーション**プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="5144b-123">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 <span data-ttu-id="5144b-124">[!code-vb[VbVbalrEvents #&41;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5144b-124">[!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5144b-125">例</span><span class="sxs-lookup"><span data-stu-id="5144b-125">Example</span></span>  
 <span data-ttu-id="5144b-126">次の例は、前の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="5144b-126">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="5144b-127">`Handles` 句の `eventlist` には&2; つのボタンのイベントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5144b-127">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 <span data-ttu-id="5144b-128">[!code-vb[VbVbalrEvents #&42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5144b-128">[!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5144b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5144b-129">See Also</span></span>  
 <span data-ttu-id="5144b-130">[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) </span><span class="sxs-lookup"><span data-stu-id="5144b-130">[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) </span></span>  
<span data-ttu-id="5144b-131"> [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5144b-131"> [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) </span></span>  
<span data-ttu-id="5144b-132"> [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5144b-132"> [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) </span></span>  
<span data-ttu-id="5144b-133"> [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5144b-133"> [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md) </span></span>  
<span data-ttu-id="5144b-134"> [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5144b-134"> [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md) </span></span>  
<span data-ttu-id="5144b-135"> [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="5144b-135"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>

