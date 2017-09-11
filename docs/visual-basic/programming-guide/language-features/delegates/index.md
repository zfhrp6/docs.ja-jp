---
title: "デリゲート (Visual Basic)"
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
- delegates [Visual Basic]
- Visual Basic code, delegates
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0b65f2d74064542177790e513eb2452274743b51
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="delegates-visual-basic"></a><span data-ttu-id="f15e7-102">デリゲート (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15e7-102">Delegates (Visual Basic)</span></span>
<span data-ttu-id="f15e7-103">デリゲートは、メソッドを参照するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="f15e7-103">Delegates are objects that refer to methods.</span></span> <span data-ttu-id="f15e7-104">デリゲートは他のプログラミング言語で使用される関数ポインターに似ているため、"*タイプ セーフ関数ポインター*" と説明されることがあります。</span><span class="sxs-lookup"><span data-stu-id="f15e7-104">They are sometimes described as *type-safe function pointers* because they are similar to function pointers used in other programming languages.</span></span> <span data-ttu-id="f15e7-105">しかし、関数ポインターとは異なり、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] のデリゲートは、<xref:System.Delegate?displayProperty=fullName> クラスに基づく参照型です。</span><span class="sxs-lookup"><span data-stu-id="f15e7-105">But unlike function pointers, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] delegates are a reference type based on the class <xref:System.Delegate?displayProperty=fullName>.</span></span> <span data-ttu-id="f15e7-106">デリゲートは、共有メソッド (特定のクラスのインスタンスがなくても呼び出すことのできるメソッド) とインスタンス メソッドの両方を参照できます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-106">Delegates can reference both shared methods — methods that can be called without a specific instance of a class — and instance methods.</span></span>  
  
## <a name="delegates-and-events"></a><span data-ttu-id="f15e7-107">デリゲートとイベント</span><span class="sxs-lookup"><span data-stu-id="f15e7-107">Delegates and Events</span></span>  
 <span data-ttu-id="f15e7-108">デリゲートは、呼び出し側プロシージャと呼び出されるプロシージャの間の媒介手段が必要な状況で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-108">Delegates are useful in situations where you need an intermediary between a calling procedure and the procedure being called.</span></span> <span data-ttu-id="f15e7-109">たとえば、イベントを発生させるオブジェクトが、異なる状況で別個のイベント ハンドラーを呼び出せるようにする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="f15e7-109">For example, you might want an object that raises events to be able to call different event handlers under different circumstances.</span></span> <span data-ttu-id="f15e7-110">しかし、イベントを発生させるオブジェクトは、どのイベント ハンドラーが特定のイベントを処理するかをあらかじめ把握できません。</span><span class="sxs-lookup"><span data-stu-id="f15e7-110">Unfortunately, the object raising the events cannot know ahead of time which event handler is handling a specific event.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="f15e7-111"> で `AddHandler` ステートメントを使用すると、デリゲートを作成して、イベント ハンドラーをイベントに動的に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-111"> lets you dynamically associate event handlers with events by creating a delegate for you when you use the `AddHandler` statement.</span></span> <span data-ttu-id="f15e7-112">実行時に、デリゲートによって適切なイベント ハンドラーに呼び出しが転送されます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-112">At run time, the delegate forwards calls to the appropriate event handler.</span></span>  
  
 <span data-ttu-id="f15e7-113">独自のデリゲートを作成することもできますが、ほとんどの場合、デリゲートの作成と詳細の管理は [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] によって自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-113">Although you can create your own delegates, in most cases [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates the delegate and takes care of the details for you.</span></span> <span data-ttu-id="f15e7-114">たとえば、`Event` ステートメントは、`Event` ステートメントを含むクラスの入れ子のクラスとして、`<EventName>EventHandler` という名前のデリゲート クラスをイベントと同じシグネチャを使用して暗黙的に定義します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-114">For example, an `Event` statement implicitly defines a delegate class named `<EventName>EventHandler` as a nested class of the class containing the `Event` statement, and with the same signature as the event.</span></span> <span data-ttu-id="f15e7-115">`AddressOf` ステートメントは、特定のプロシージャを参照するデリゲートのインスタンスを暗黙的に作成します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-115">The `AddressOf` statement implicitly creates an instance of a delegate that refers to a specific procedure.</span></span> <span data-ttu-id="f15e7-116">次の 2 つのコード行は同等です。</span><span class="sxs-lookup"><span data-stu-id="f15e7-116">The following two lines of code are equivalent.</span></span> <span data-ttu-id="f15e7-117">最初の行では、`Eventhandler` のインスタンスが明示的に作成され、メソッド `Button1_Click` への参照が引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-117">In the first line, you see the explicit creation of an instance of `Eventhandler`, with a reference to method `Button1_Click` sent as the argument.</span></span> <span data-ttu-id="f15e7-118">2 番目の行は、より便利な方法で同じことを実行します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-118">The second line is a more convenient way to do the same thing.</span></span>  
  
 <span data-ttu-id="f15e7-119">[!code-vb[VbVbalrDelegates 6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f15e7-119">[!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_1.vb)]</span></span>  
  
 <span data-ttu-id="f15e7-120">コンパイラがデリゲートの種類をコンテキストから判断できる場合は、デリゲートの簡単な作成方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-120">You can use the shorthand way of creating delegates anywhere the compiler can determine the delegate's type by the context.</span></span>  
  
## <a name="declaring-events-that-use-an-existing-delegate-type"></a><span data-ttu-id="f15e7-121">既存の種類のデリゲートを使用するイベントの宣言</span><span class="sxs-lookup"><span data-stu-id="f15e7-121">Declaring Events that Use an Existing Delegate Type</span></span>  
 <span data-ttu-id="f15e7-122">状況によっては、基になるデリゲートとして既存のデリゲートを使用するイベントを宣言する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="f15e7-122">In some situations, you may want to declare an event to use an existing delegate type as its underlying delegate.</span></span> <span data-ttu-id="f15e7-123">その方法を次の構文に示します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-123">The following syntax demonstrates how:</span></span>  
  
 <span data-ttu-id="f15e7-124">[!code-vb[VbVbalrDelegates #7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f15e7-124">[!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_2.vb)]</span></span>  
  
 <span data-ttu-id="f15e7-125">これは、同じハンドラーに複数のイベントをルーティングする場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-125">This is useful when you want to route multiple events to the same handler.</span></span>  
  
## <a name="delegate-variables-and-parameters"></a><span data-ttu-id="f15e7-126">デリゲート変数とパラメーター</span><span class="sxs-lookup"><span data-stu-id="f15e7-126">Delegate Variables and Parameters</span></span>  
 <span data-ttu-id="f15e7-127">デリゲートは、フリースレッド処理や、実行時に異なるバージョンの関数を呼び出す必要があるプロシージャなど、イベントに関連しない他のタスクにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-127">You can use delegates for other, non-event related tasks, such as free threading or with procedures that need to call different versions of functions at run time.</span></span>  
  
 <span data-ttu-id="f15e7-128">たとえば、自動車の名前のリスト ボックスを含む、項目別広告のアプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="f15e7-128">For example, suppose you have a classified-ad application that includes a list box with the names of cars.</span></span> <span data-ttu-id="f15e7-129">広告はタイトル(通常は自動車の型式) で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-129">The ads are sorted by title, which is normally the make of the car.</span></span> <span data-ttu-id="f15e7-130">問題が発生する可能性があるのは、型式の前に年式が含まれている自動車があるときです。</span><span class="sxs-lookup"><span data-stu-id="f15e7-130">A problem you may face occurs when some cars include the year of the car before the make.</span></span> <span data-ttu-id="f15e7-131">問題になるのは、リスト ボックスに組み込まれた並べ替え機能の並べ替えの基準が文字コードだけであることです。このため、日付で始まるすべての広告が最初に配置され、その後に型式で始まる広告が配置されます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-131">The problem is that the built-in sort functionality of the list box sorts only by character codes; it places all the ads starting with dates first, followed by the ads starting with the make.</span></span>  
  
 <span data-ttu-id="f15e7-132">この問題を解決するために、クラスに並べ替えプロシージャを作成できます。このプロシージャは、ほとんどのリスト ボックスに対応する標準的なアルファベット順の並べ替えを使用しますが、実行時に自動車広告用のカスタム並べ替えプロシージャに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-132">To fix this, you can create a sort procedure in a class that uses the standard alphabetic sort on most list boxes, but is able to switch at run time to the custom sort procedure for car ads.</span></span> <span data-ttu-id="f15e7-133">このプロシージャを作成するには、デリゲートを使用して実行時にカスタム並べ替えプロシージャを並べ替えクラスに渡します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-133">To do this, you pass the custom sort procedure to the sort class at run time, using delegates.</span></span>  
  
## <a name="addressof-and-lambda-expressions"></a><span data-ttu-id="f15e7-134">AddressOf とラムダ式</span><span class="sxs-lookup"><span data-stu-id="f15e7-134">AddressOf and Lambda Expressions</span></span>  
 <span data-ttu-id="f15e7-135">各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-135">Each delegate class defines a constructor that is passed the specification of an object method.</span></span> <span data-ttu-id="f15e7-136">デリゲート コンス トラクターに渡す引数は、メソッドへの参照、またはラムダ式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f15e7-136">An argument to a delegate constructor must be a reference to a method, or a lambda expression.</span></span>  
  
 <span data-ttu-id="f15e7-137">メソッドへの参照を指定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-137">To specify a reference to a method, use the following syntax:</span></span>  
  
 <span data-ttu-id="f15e7-138">`AddressOf` [`expression`.]`methodName`</span><span class="sxs-lookup"><span data-stu-id="f15e7-138">`AddressOf` [`expression`.]`methodName`</span></span>  
  
 <span data-ttu-id="f15e7-139">コンパイル時の `expression` の型は、シグネチャがデリゲート クラスのシグネチャと同じで、指定された名前のメソッドを持つクラスまたはインターフェイスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f15e7-139">The compile-time type of the `expression` must be the name of a class or an interface that contains a method of the specified name whose signature matches the signature of the delegate class.</span></span> <span data-ttu-id="f15e7-140">`methodName` は、共有メソッドまたはインスタンス メソッドのいずれかにできます。</span><span class="sxs-lookup"><span data-stu-id="f15e7-140">The `methodName` can be either a shared method or an instance method.</span></span> <span data-ttu-id="f15e7-141">クラスの既定メソッドに対してデリゲートを作成する場合も、`methodName` は省略できません。</span><span class="sxs-lookup"><span data-stu-id="f15e7-141">The `methodName` is not optional, even if you create a delegate for the default method of the class.</span></span>  
  
 <span data-ttu-id="f15e7-142">ラムダ式を指定するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-142">To specify a lambda expression, use the following syntax:</span></span>  
  
 <span data-ttu-id="f15e7-143">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span><span class="sxs-lookup"><span data-stu-id="f15e7-143">`Function` ([`parm` As `type`, `parm2` As `type2`, ...]) `expression`</span></span>  
  
 <span data-ttu-id="f15e7-144">次の例では、デリゲートの参照を指定するために使用される `AddressOf` 式とラムダ式を示します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-144">The following example shows both `AddressOf` and lambda expressions used to specify the reference for a delegate.</span></span>  
  
 <span data-ttu-id="f15e7-145">[!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f15e7-145">[!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegates_3.vb)]</span></span>  
  
 <span data-ttu-id="f15e7-146">関数のシグネチャは、デリゲート型のシグネチャと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f15e7-146">The signature of the function must match that of the delegate type.</span></span> <span data-ttu-id="f15e7-147">ラムダ式について詳しくは、「[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f15e7-147">For more information about lambda expressions, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span> <span data-ttu-id="f15e7-148">ラムダ式のその他の例と `AddressOf` のデリゲートへの代入については、「[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f15e7-148">For more examples of lambda expression and `AddressOf` assignments to delegates, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="f15e7-149">関連トピック</span><span class="sxs-lookup"><span data-stu-id="f15e7-149">Related Topics</span></span>  
  
|<span data-ttu-id="f15e7-150">タイトル</span><span class="sxs-lookup"><span data-stu-id="f15e7-150">Title</span></span>|<span data-ttu-id="f15e7-151">説明</span><span class="sxs-lookup"><span data-stu-id="f15e7-151">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f15e7-152">方法: デリゲート メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="f15e7-152">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|<span data-ttu-id="f15e7-153">メソッドをデリゲートに関連付け、デリゲートからそのメソッドを呼び出す方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-153">Provides an example that shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>|  
|<span data-ttu-id="f15e7-154">方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="f15e7-154">[How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span></span>|<span data-ttu-id="f15e7-155">デリゲートを使用してプロシージャを別のプロシージャに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-155">Demonstrates how to use delegates to pass one procedure to another procedure.</span></span>|  
|[<span data-ttu-id="f15e7-156">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="f15e7-156">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|<span data-ttu-id="f15e7-157">シグネチャが同じでない場合でも Sub や関数をデリゲートやハンドラーに割り当てる方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-157">Describes how you can assign subs and functions to delegates or handlers even when their signatures are not identical</span></span>|  
|[<span data-ttu-id="f15e7-158">イベント</span><span class="sxs-lookup"><span data-stu-id="f15e7-158">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)|<span data-ttu-id="f15e7-159">Visual Basic のデリゲートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="f15e7-159">Provides an overview of events in Visual Basic.</span></span>|

