---
title: "Function プロシージャ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9520a6555e65fd801a5c40d40748028e04a10739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="87eb3-102">Function プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87eb3-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="87eb3-103">A`Function`プロシージャは、一連の[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]で囲まれたステートメント、`Function`と`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="87eb3-103">A `Function` procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="87eb3-104">`Function`手順がタスクを実行し、呼び出し元のコードにコントロールを返します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="87eb3-105">コントロールが返されたときにも、呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="87eb3-106">プロシージャが呼び出されるたびに、そのステートメントの実行、以降の後に実行可能ファイルの最初のステートメントで、`Function`ステートメントと最初で終了するまで`End Function`、 `Exit Function`、または`Return`ステートメントが発生しました。</span><span class="sxs-lookup"><span data-stu-id="87eb3-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="87eb3-107">定義することができます、`Function`モジュール、クラスまたは構造体」の手順です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="87eb3-108">`Public`どこからでも呼び出すことを意味する既定では、モジュール、クラス、またはそれを定義する構造体へのアクセス権を持つアプリケーションでします。</span><span class="sxs-lookup"><span data-stu-id="87eb3-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="87eb3-109">A`Function`プロシージャは、定数、変数、または式で、呼び出し元のコードに渡されるなどの引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="87eb3-110">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="87eb3-110">Declaration Syntax</span></span>  
 <span data-ttu-id="87eb3-111">宣言の構文、`Function`手順のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87eb3-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="87eb3-112">*修飾子*アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="87eb3-113">詳細については、次を参照してください。[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="87eb3-114">各パラメーターを宣言すると、同様の操作を行う[Sub プロシージャ](./sub-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="87eb3-115">データの種類</span><span class="sxs-lookup"><span data-stu-id="87eb3-115">Data Type</span></span>  
 <span data-ttu-id="87eb3-116">各`Function`手順では、データ型か、単にすべての変数です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="87eb3-117">このデータ型がで指定された、`As`句、`Function`ステートメント、およびその呼び出し元のコードに関数が返す値のデータ型が決まります。</span><span class="sxs-lookup"><span data-stu-id="87eb3-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="87eb3-118">次の宣言の例では、この問題を説明します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="87eb3-119">詳細についてを参照してください「部分」[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="87eb3-120">値を返す</span><span class="sxs-lookup"><span data-stu-id="87eb3-120">Returning Values</span></span>  
 <span data-ttu-id="87eb3-121">値、`Function`プロシージャが呼び出し元のコードには、戻り値と呼ばれるを送信します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="87eb3-122">プロシージャは、2 つの方法のいずれかでこの値を返します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="87eb3-123">使用して、`Return`を返し、戻り値を指定するステートメントを呼び出し元のプログラムをすぐに制御します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="87eb3-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="87eb3-125">プロシージャの 1 つまたは複数のステートメントで独自の関数名に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="87eb3-126">までの呼び出し元のプログラムに制御を返さない、`Exit Function`または`End Function`ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="87eb3-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="87eb3-128">関数名 に戻り値を割り当てることの利点は、コントロールを返さないプロシージャから検出するまで、`Exit Function`または`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="87eb3-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="87eb3-129">これにより、一時的な値を割り当てるし、必要に応じて後で調整することができます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="87eb3-130">値を取得する方法の詳細については、次を参照してください。[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="87eb3-131">配列を取得する方法については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="87eb3-132">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="87eb3-132">Calling Syntax</span></span>  
 <span data-ttu-id="87eb3-133">呼び出す、`Function`名前と右側にある、式または代入ステートメントのいずれかの引数を含めることによってプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="87eb3-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="87eb3-134">省略可能ではないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="87eb3-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="87eb3-135">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="87eb3-136">呼び出しの構文、`Function`手順のとおりです。</span><span class="sxs-lookup"><span data-stu-id="87eb3-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="87eb3-137">*左辺値*`=`*functionname* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="87eb3-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="87eb3-138">`If ((`*functionname* `[(` *argumentlist* `)] / 3) <=`*式*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="87eb3-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="87eb3-139">呼び出すと、`Function`手順がありません、戻り値を使用します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="87eb3-140">そうしないと場合、は、関数のすべてのアクションが実行されますが、戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="87eb3-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>多くの場合、この方法で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="87eb3-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="87eb3-142">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="87eb3-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="87eb3-143">次`Function`最長側では、やの他の 2 つの辺の値を指定、直角三角形の斜辺を計算します。</span><span class="sxs-lookup"><span data-stu-id="87eb3-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 <span data-ttu-id="87eb3-144">次の例では、一般的な呼び出しを`hypotenuse`です。</span><span class="sxs-lookup"><span data-stu-id="87eb3-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="87eb3-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="87eb3-145">See Also</span></span>  
 [<span data-ttu-id="87eb3-146">手順</span><span class="sxs-lookup"><span data-stu-id="87eb3-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="87eb3-147">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="87eb3-147">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="87eb3-148">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="87eb3-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="87eb3-149">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="87eb3-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="87eb3-150">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="87eb3-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="87eb3-151">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="87eb3-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="87eb3-152">方法 : 値を返すプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="87eb3-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="87eb3-153">方法 : プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="87eb3-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="87eb3-154">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="87eb3-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
