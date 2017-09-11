---
title: "Function プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Function procedures
- return values, function procedures
- Visual Basic code, procedures
- procedures, calling
- procedures, Function procedures
- syntax, function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fb36ee41e4b53f6e690ce5d48d34bbfc9f86c177
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="d7c13-102">Function プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7c13-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="d7c13-103">A`Function`プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]で囲まれたステートメント、`Function`と`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d7c13-103">A `Function` procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="d7c13-104">`Function`プロシージャは、タスクを実行し、呼び出し元のコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="d7c13-105">制御を戻す場合も、呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="d7c13-106">プロシージャが呼び出されるたび、そのステートメントの実行後の最初の実行可能ステートメントから始まる、`Function`ステートメントおよび&1; つ目で終了するまで`End Function`、 `Exit Function`、または`Return`ステートメントが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d7c13-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="d7c13-107">定義する、`Function`モジュール、クラスまたは構造体のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d7c13-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="d7c13-108">`Public`どこからでも呼び出すことができますが意味を既定では、モジュール、クラス、または、定義された構造体へのアクセス権を持つアプリケーションでします。</span><span class="sxs-lookup"><span data-stu-id="d7c13-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="d7c13-109">A`Function`プロシージャは、定数、変数、または、呼び出し元のコードに渡される式などの引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="d7c13-110">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="d7c13-110">Declaration Syntax</span></span>  
 <span data-ttu-id="d7c13-111">宣言の構文、`Function`手順は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="d7c13-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="d7c13-112">*修飾子*アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="d7c13-113">詳細については、次を参照してください。 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="d7c13-114">各パラメーターのと同じ方法を宣言する[Sub プロシージャ](./sub-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="d7c13-115">データの種類</span><span class="sxs-lookup"><span data-stu-id="d7c13-115">Data Type</span></span>  
 <span data-ttu-id="d7c13-116">各`Function`手順では、データ型、単にすべての変数ではサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="d7c13-117">このデータ型が指定された、`As`句、`Function`ステートメント、およびその呼び出し元のコードに、関数が返す値のデータ型を決定します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="d7c13-118">次の宣言の例では、これを示しています。</span><span class="sxs-lookup"><span data-stu-id="d7c13-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="d7c13-119">詳細については、「部分」を参照してください[Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="d7c13-120">値を返す</span><span class="sxs-lookup"><span data-stu-id="d7c13-120">Returning Values</span></span>  
 <span data-ttu-id="d7c13-121">値、`Function`プロシージャが呼び出し元のコードには、戻り値と呼ばれるを送信します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="d7c13-122">プロシージャは、2 つの方法のいずれかでこの値を返します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="d7c13-123">使用して、`Return`を返します。 戻り値を指定するステートメントを呼び出し元のプログラムをすぐに制御します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="d7c13-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="d7c13-125">プロシージャの&1; つまたは複数のステートメントで独自の関数名 に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="d7c13-126">まで呼び出し元のプログラムに制御が戻らない、`Exit Function`または`End Function`ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="d7c13-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="d7c13-128">関数名 に戻り値を割り当てることの利点は、制御を返さないこと、手順からに到達するまで、`Exit Function`または`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d7c13-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="d7c13-129">これにより、一時的な値を割り当てるし、必要に応じて後で調整することができます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="d7c13-130">値を取得する方法の詳細については、次を参照してください。 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="d7c13-131">配列を取得する方法については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="d7c13-132">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="d7c13-132">Calling Syntax</span></span>  
 <span data-ttu-id="d7c13-133">呼び出す、`Function`名前と、代入ステートメントまたは式の右側にあるいずれかの引数を含めることによってプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d7c13-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="d7c13-134">省略可能でないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7c13-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="d7c13-135">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="d7c13-136">呼び出しの構文、`Function`手順は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="d7c13-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="d7c13-137">*左辺値*`=`*functionname* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="d7c13-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="d7c13-138">`If ((`*functionname* `[(` *argumentlist* `)] / 3) <=`*式*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="d7c13-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="d7c13-139">呼び出すと、`Function`の手順がありません、戻り値を使用します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="d7c13-140">そうしない場合は、関数のすべての動作が実行されますが、戻り値が無視されます。</span><span class="sxs-lookup"><span data-stu-id="d7c13-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="d7c13-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>多くの場合、この方法で呼び出されます。</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="d7c13-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="d7c13-142">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="d7c13-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="d7c13-143">次`Function`プロシージャは、最も長い辺または他の&2; つの値を指定された直角三角形の斜辺を計算します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 <span data-ttu-id="d7c13-144">[!code-vb[VbVbcnProcedures&#1;](./codesnippet/VisualBasic/function-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7c13-144">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="d7c13-145">次の例では、一般的な呼び出しを`hypotenuse`します。</span><span class="sxs-lookup"><span data-stu-id="d7c13-145">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 <span data-ttu-id="d7c13-146">[!code-vb[VbVbcnProcedures&6;](./codesnippet/VisualBasic/function-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d7c13-146">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c13-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7c13-147">See Also</span></span>  
 <span data-ttu-id="d7c13-148">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-148">[Procedures](./index.md) </span></span>  
<span data-ttu-id="d7c13-149"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-149"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="d7c13-150"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-150"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="d7c13-151"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-151"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="d7c13-152"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="d7c13-153"> [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-153"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="d7c13-154"> [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-154"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="d7c13-155"> [方法: プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d7c13-155"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="d7c13-156"> [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="d7c13-156"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
