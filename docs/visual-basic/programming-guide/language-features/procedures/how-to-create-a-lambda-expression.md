---
title: "方法: ラムダ式を作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16365b64e5430be61c113ac7601154df260e4ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="fc553-102">方法: ラムダ式を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc553-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="fc553-103">A*ラムダ式*は関数またはサブルーチンに名前がないです。</span><span class="sxs-lookup"><span data-stu-id="fc553-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="fc553-104">ラムダ式は、デリゲート型が有効な場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc553-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="fc553-105">単一行のラムダ式の関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="fc553-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="fc553-106">どのような状況はデリゲート型を使用できる場所をキーワードを入力`Function`次の例のように、します。</span><span class="sxs-lookup"><span data-stu-id="fc553-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="fc553-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="fc553-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="fc553-108">かっこ内のすぐ後に`Function`関数のパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="fc553-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="fc553-109">後に名前が指定されていないことに注意してください。`Function`です。</span><span class="sxs-lookup"><span data-stu-id="fc553-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="fc553-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="fc553-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="fc553-111">次のパラメーター リストには、関数の本体として 1 つの式を入力します。</span><span class="sxs-lookup"><span data-stu-id="fc553-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="fc553-112">式に評価される値は、関数によって返される値です。</span><span class="sxs-lookup"><span data-stu-id="fc553-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="fc553-113">使用しない、`As`句を戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc553-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="fc553-114">ラムダ式は、整数の引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc553-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="fc553-115">代わりに、同じ結果には、次の例。</span><span class="sxs-lookup"><span data-stu-id="fc553-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="fc553-116">単一行のラムダ式のサブルーチンを作成するには</span><span class="sxs-lookup"><span data-stu-id="fc553-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="fc553-117">デリゲート型を使用できる場所の場合、キーワードを入力`Sub`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="fc553-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="fc553-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="fc553-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="fc553-119">かっこ内のすぐ後に`Sub`サブルーチンのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="fc553-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="fc553-120">後に名前が指定されていないことに注意してください。`Sub`です。</span><span class="sxs-lookup"><span data-stu-id="fc553-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="fc553-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="fc553-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="fc553-122">次のパラメーター リストには、サブルーチンの本文として 1 つのステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="fc553-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="fc553-123">ラムダ式は、文字列引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc553-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="fc553-124">複数行のラムダ式の関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="fc553-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="fc553-125">デリゲート型を使用できる場所の場合、キーワードを入力`Function`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="fc553-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="fc553-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="fc553-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="fc553-127">かっこ内のすぐ後に`Function`関数のパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="fc553-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="fc553-128">後に名前が指定されていないことに注意してください。`Function`です。</span><span class="sxs-lookup"><span data-stu-id="fc553-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="fc553-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="fc553-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="fc553-130">ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fc553-130">Press ENTER.</span></span> <span data-ttu-id="fc553-131">`End Function`ステートメントが自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="fc553-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="fc553-132">関数の本体内では、式を作成して値を返すには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fc553-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="fc553-133">使用しない、`As`句を戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc553-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="fc553-134">ラムダ式は、整数の引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc553-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="fc553-135">複数行のラムダ式のサブルーチンを作成するには</span><span class="sxs-lookup"><span data-stu-id="fc553-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="fc553-136">どのような状況はデリゲート型を使用できる場所をキーワードを入力`Sub`次の例のように。</span><span class="sxs-lookup"><span data-stu-id="fc553-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="fc553-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="fc553-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="fc553-138">かっこ内のすぐ後に`Sub`サブルーチンのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="fc553-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="fc553-139">後に名前が指定されていないことに注意してください。`Sub`です。</span><span class="sxs-lookup"><span data-stu-id="fc553-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="fc553-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="fc553-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="fc553-141">ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="fc553-141">Press ENTER.</span></span> <span data-ttu-id="fc553-142">`End Sub`ステートメントが自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="fc553-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="fc553-143">関数の本体内では、サブルーチンが呼び出されるときに実行する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fc553-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="fc553-144">ラムダ式は、文字列引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fc553-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="fc553-145">例</span><span class="sxs-lookup"><span data-stu-id="fc553-145">Example</span></span>  
 <span data-ttu-id="fc553-146">型を持つパラメーターの引数として渡すことができる関数を定義するラムダ式の一般的な用途は、`Delegate`です。</span><span class="sxs-lookup"><span data-stu-id="fc553-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="fc553-147">次の例で、<xref:System.Diagnostics.Process.GetProcesses%2A>メソッド、ローカル コンピューターで実行中のプロセスの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="fc553-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="fc553-148"><xref:System.Linq.Enumerable.Where%2A>メソッドから、<xref:System.Linq.Enumerable>クラス必要があります、`Boolean`デリゲートの引数として。</span><span class="sxs-lookup"><span data-stu-id="fc553-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="fc553-149">ラムダ式の例では、そのような目的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc553-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="fc553-150">返します`True`各プロセスのスレッドの 1 つだけ持ちで選択されている`filteredList`です。</span><span class="sxs-lookup"><span data-stu-id="fc553-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="fc553-151">前の例は、次のコードで記述された[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]構文。</span><span class="sxs-lookup"><span data-stu-id="fc553-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fc553-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc553-152">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 [<span data-ttu-id="fc553-153">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="fc553-153">Lambda Expressions</span></span>](./lambda-expressions.md)  
 [<span data-ttu-id="fc553-154">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="fc553-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="fc553-155">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="fc553-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="fc553-156">デリゲート</span><span class="sxs-lookup"><span data-stu-id="fc553-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="fc553-157">方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="fc553-157">[How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span></span>  
 [<span data-ttu-id="fc553-158">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="fc553-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="fc553-159">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="fc553-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
