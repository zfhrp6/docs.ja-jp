---
title: Sub プロシージャ (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7258d57d2677042a2020097893a4f7a0adb35508
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="c48b9-102">Sub プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c48b9-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="c48b9-103">A`Sub`プロシージャは、一連の Visual Basic ステートメントで囲まれた、`Sub`と`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c48b9-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="c48b9-104">`Sub`呼び出しコードに値を返さないが、プロシージャは、タスクを実行し、呼び出し元のコードにコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="c48b9-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="c48b9-105">プロシージャが呼び出されるたびにそのステートメントが実行される後の最初の実行可能ステートメントで始まる、`Sub`ステートメントと最初で終了するまで`End Sub`、 `Exit Sub`、または`Return`ステートメントが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c48b9-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="c48b9-106">定義することができます、`Sub`モジュール、クラス、および構造体」の手順です。</span><span class="sxs-lookup"><span data-stu-id="c48b9-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="c48b9-107">既定では`Public`、することができる呼び出すことができます、どこからでも、モジュール、クラス、またはそれを定義する構造体へのアクセス権を持つアプリケーションでします。</span><span class="sxs-lookup"><span data-stu-id="c48b9-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="c48b9-108">用語、*メソッド*、について説明します、`Sub`または`Function`プロシージャの定義の外部からアクセスされるモジュール、クラスまたは構造体。</span><span class="sxs-lookup"><span data-stu-id="c48b9-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="c48b9-109">詳細については、「[プロシージャ](./index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c48b9-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="c48b9-110">A`Sub`プロシージャは、定数、変数、または式で、呼び出し元のコードに渡されるなどの引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c48b9-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c48b9-111">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="c48b9-111">Declaration Syntax</span></span>  
 <span data-ttu-id="c48b9-112">宣言の構文、`Sub`手順のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c48b9-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="c48b9-113">`[` *修飾子* `] Sub` *subname* `[(` *parameterlist*  `)]`</span><span class="sxs-lookup"><span data-stu-id="c48b9-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="c48b9-114">`modifiers`アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウ処理に関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c48b9-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="c48b9-115">詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="c48b9-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="c48b9-116">パラメーターの宣言</span><span class="sxs-lookup"><span data-stu-id="c48b9-116">Parameter Declaration</span></span>  
 <span data-ttu-id="c48b9-117">同様に宣言する方法、変数、パラメーター名とデータ型を指定するには、各プロシージャ パラメーターを宣言するとします。</span><span class="sxs-lookup"><span data-stu-id="c48b9-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="c48b9-118">引き渡し方法を指定することも、パラメーターは省略可能かどうかや、パラメーター配列。</span><span class="sxs-lookup"><span data-stu-id="c48b9-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="c48b9-119">パラメーター リスト内の各パラメーターの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c48b9-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="c48b9-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*データ型* </span><span class="sxs-lookup"><span data-stu-id="c48b9-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="c48b9-121">パラメーターが省略可能な場合は、宣言の一部として既定値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c48b9-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="c48b9-122">既定値を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c48b9-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="c48b9-123">`Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue* </span><span class="sxs-lookup"><span data-stu-id="c48b9-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="c48b9-124">ローカル変数としてパラメーター</span><span class="sxs-lookup"><span data-stu-id="c48b9-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="c48b9-125">コントロール、プロシージャに渡すと、各パラメーターは、ローカル変数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="c48b9-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="c48b9-126">これは、その有効期間は、プロシージャのと同じことと、そのスコープは、プロシージャ全体を意味します。</span><span class="sxs-lookup"><span data-stu-id="c48b9-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="c48b9-127">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="c48b9-127">Calling Syntax</span></span>  
 <span data-ttu-id="c48b9-128">呼び出す、`Sub`プロシージャ、スタンドアロンの呼び出し元ステートメントを明示的にします。</span><span class="sxs-lookup"><span data-stu-id="c48b9-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="c48b9-129">式の中でその名前を使用して呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c48b9-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="c48b9-130">省略可能ではないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="c48b9-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="c48b9-131">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="c48b9-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="c48b9-132">使用、`Call`キーワードは任意ですがないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c48b9-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="c48b9-133">呼び出しの構文、`Sub`手順のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c48b9-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="c48b9-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="c48b9-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="c48b9-135">呼び出すことができます、`Sub`からそれを定義するクラスの外側のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="c48b9-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="c48b9-136">最初に、使用する必要がある、`New`キーワードをクラスのインスタンスを作成またはメソッドを呼び出すには、クラスのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="c48b9-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="c48b9-137">詳細については、次を参照してください。 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="c48b9-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="c48b9-138">呼び出して、次の構文を使用する、`Sub`インスタンス オブジェクトのメソッド。</span><span class="sxs-lookup"><span data-stu-id="c48b9-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="c48b9-139">*オブジェクト*.*methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="c48b9-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="c48b9-140">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="c48b9-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="c48b9-141">次`Sub`の手順では、コンピューターの演算子、アプリケーションは、実行しようとしているタスクともタイムスタンプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c48b9-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="c48b9-142">すべてのタスクの開始時にこのコードを複製するには、代わりに、アプリケーションだけを呼び出す`tellOperator`さまざまな場所からします。</span><span class="sxs-lookup"><span data-stu-id="c48b9-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="c48b9-143">呼び出しごとに文字列を渡して、`task`開始されているタスクを識別する引数。</span><span class="sxs-lookup"><span data-stu-id="c48b9-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 <span data-ttu-id="c48b9-144">次の例では、一般的な呼び出しを`tellOperator`です。</span><span class="sxs-lookup"><span data-stu-id="c48b9-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c48b9-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c48b9-145">See Also</span></span>  
 [<span data-ttu-id="c48b9-146">手順</span><span class="sxs-lookup"><span data-stu-id="c48b9-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c48b9-147">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="c48b9-147">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="c48b9-148">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="c48b9-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="c48b9-149">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="c48b9-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="c48b9-150">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="c48b9-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c48b9-151">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="c48b9-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="c48b9-152">方法 : 値を返さないプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="c48b9-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [<span data-ttu-id="c48b9-153">方法: Visual Basic では、イベント ハンドラーを呼び出します</span><span class="sxs-lookup"><span data-stu-id="c48b9-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
