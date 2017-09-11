---
title: "Sub プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Sub procedures, about Sub procedures
- statement blocks
- Sub procedures, calling
- procedures, calling
- Sub procedures, syntax
- Sub procedures
- procedures, Sub
- syntax, Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
caps.latest.revision: 21
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
ms.openlocfilehash: 83f0a16498accf383da96d702c4e3a4b7de1c861
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="6e23c-102">Sub プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e23c-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="6e23c-103">A`Sub`プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]で囲まれたステートメント、`Sub`と`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6e23c-103">A `Sub` procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="6e23c-104">`Sub`呼び出し元のコードに値を返すことはできませんが、プロシージャは、タスクを実行し、呼び出し元のコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="6e23c-105">そのステートメントで実行されるプロシージャが呼び出されるたびに後の最初の実行可能ステートメントで始まる、`Sub`ステートメントおよび&1; つ目で終了するまで`End Sub`、 `Exit Sub`、または`Return`ステートメントが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6e23c-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="6e23c-106">定義する、`Sub`モジュール、クラス、および構造体のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="6e23c-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="6e23c-107">既定では`Public`、することができるから呼び出せる任意の場所をモジュール、クラス、または、定義された構造体へのアクセスを持つアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="6e23c-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="6e23c-108">この言葉を*メソッド*、について説明します、`Sub`または`Function`プロシージャの定義の外部からアクセスされるモジュール、クラスまたは構造体。</span><span class="sxs-lookup"><span data-stu-id="6e23c-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="6e23c-109">詳細については、次を参照してください。[プロシージャ](./index.md)します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="6e23c-110">A`Sub`プロシージャは、定数、変数、または、呼び出し元のコードに渡される式などの引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="6e23c-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="6e23c-111">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="6e23c-111">Declaration Syntax</span></span>  
 <span data-ttu-id="6e23c-112">宣言の構文、`Sub`手順は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="6e23c-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="6e23c-113">`[`*modifiers* `] Sub`*subname* `[(` *parameterlist*  `)]`</span><span class="sxs-lookup"><span data-stu-id="6e23c-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="6e23c-114">`modifiers`アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6e23c-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="6e23c-115">詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="6e23c-116">パラメーターの宣言</span><span class="sxs-lookup"><span data-stu-id="6e23c-116">Parameter Declaration</span></span>  
 <span data-ttu-id="6e23c-117">同様にどのように変数を宣言する、パラメーター名とデータ型を指定するには、各プロシージャ パラメーターを宣言するとします。</span><span class="sxs-lookup"><span data-stu-id="6e23c-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="6e23c-118">引数渡しの方法を指定することも、パラメーターは省略可能かどうかや、パラメーター配列。</span><span class="sxs-lookup"><span data-stu-id="6e23c-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="6e23c-119">パラメーター リスト内の各パラメーターの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e23c-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="6e23c-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*`As`*データ型    *</span><span class="sxs-lookup"><span data-stu-id="6e23c-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="6e23c-121">パラメーターが省略可能な場合も、その宣言の一部として既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e23c-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="6e23c-122">既定値を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e23c-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="6e23c-123">`Optional [ByVal | ByRef]`  *parametername*`As`*datatype*`=`*defaultvalue        *</span><span class="sxs-lookup"><span data-stu-id="6e23c-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="6e23c-124">ローカル変数とパラメーター</span><span class="sxs-lookup"><span data-stu-id="6e23c-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="6e23c-125">コントロール、プロシージャに渡すと、各パラメーターは、ローカル変数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="6e23c-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="6e23c-126">これは、そのスコープは、プロシージャ全体をその有効期間は、プロシージャのと同じことを意味します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="6e23c-127">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="6e23c-127">Calling Syntax</span></span>  
 <span data-ttu-id="6e23c-128">呼び出す、`Sub`プロシージャ スタンドアロン呼び出し元のステートメントを明示的にします。</span><span class="sxs-lookup"><span data-stu-id="6e23c-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="6e23c-129">式の中でその名前を使用して呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="6e23c-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="6e23c-130">省略可能でないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e23c-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="6e23c-131">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="6e23c-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="6e23c-132">使用、`Call`キーワードは任意ですがないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e23c-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="6e23c-133">呼び出しの構文、`Sub`手順は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="6e23c-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="6e23c-134">`[Call]`  *subname* `[(` *argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="6e23c-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="6e23c-135">呼び出すことができます、`Sub`からこれを定義するクラスの外側のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="6e23c-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="6e23c-136">最初に、使用する必要がある、`New`キーワードをクラスのインスタンスを作成またはメソッドを呼び出すには、クラスのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="6e23c-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="6e23c-137">詳細については、次を参照してください。 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="6e23c-138">呼び出す次の構文を使用し、`Sub`インスタンス オブジェクトのメソッド。</span><span class="sxs-lookup"><span data-stu-id="6e23c-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="6e23c-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="6e23c-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="6e23c-140">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="6e23c-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="6e23c-141">次`Sub`手順で実行しようとしてタスク、アプリケーション コンピューター演算子を説明し、タイムスタンプを表示します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="6e23c-142">アプリケーションのすべてのタスクの開始時に、このコードを複製するのではなくはだけ`tellOperator`さまざまな場所からです。</span><span class="sxs-lookup"><span data-stu-id="6e23c-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="6e23c-143">各呼び出しで文字列を渡して、`task`開始されているタスクを識別する引数。</span><span class="sxs-lookup"><span data-stu-id="6e23c-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 <span data-ttu-id="6e23c-144">[!code-vb[VbVbcnProcedures&#2;](./codesnippet/VisualBasic/sub-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e23c-144">[!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="6e23c-145">次の例では、一般的な呼び出しを`tellOperator`します。</span><span class="sxs-lookup"><span data-stu-id="6e23c-145">The following example shows a typical call to `tellOperator`.</span></span>  
  
 <span data-ttu-id="6e23c-146">[!code-vb[VbVbcnProcedures&#3;](./codesnippet/VisualBasic/sub-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6e23c-146">[!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e23c-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e23c-147">See Also</span></span>  
 <span data-ttu-id="6e23c-148">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-148">[Procedures](./index.md) </span></span>  
<span data-ttu-id="6e23c-149"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-149"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="6e23c-150"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-150"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="6e23c-151"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-151"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="6e23c-152"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="6e23c-153"> [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-153"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="6e23c-154"> [方法: 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="6e23c-154"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md) </span></span>  
<span data-ttu-id="6e23c-155"> [方法: Visual Basic でイベント ハンドラーを呼び出す](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="6e23c-155"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
