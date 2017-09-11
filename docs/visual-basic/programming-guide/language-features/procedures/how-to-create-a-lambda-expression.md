---
title: "方法: ラムダ式 (Visual Basic) を作成する |Microsoft ドキュメント"
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
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
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
ms.openlocfilehash: edd475490dce81ff9cca32b5f9a5090d99f4d80d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="a57f8-102">方法: ラムダ式を作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a57f8-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="a57f8-103">A*ラムダ式*関数またはサブルーチンに名前がないです。</span><span class="sxs-lookup"><span data-stu-id="a57f8-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="a57f8-104">ラムダ式は、デリゲート型が有効な場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a57f8-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="a57f8-105">単一行のラムダ式の関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="a57f8-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="a57f8-106">どのような状況にデリゲート型を使用できる場所で、キーワードを入力`Function`次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="a57f8-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="a57f8-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="a57f8-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="a57f8-108">かっこで囲んで直後後`Function`関数のパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="a57f8-109">後の名前を指定しないことに注意してください。`Function`します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="a57f8-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="a57f8-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="a57f8-111">次のパラメーター リストには、関数の本体として&1; つの式を入力します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="a57f8-112">式の評価結果の値は、関数によって返される値です。</span><span class="sxs-lookup"><span data-stu-id="a57f8-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="a57f8-113">使用しない、`As`句を戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="a57f8-114">[!code-vb[VbVbalrLambdas&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-114">[!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span></span>  
  
     <span data-ttu-id="a57f8-115">ラムダ式は、整数の引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="a57f8-116">[!code-vb[VbVbalrLambdas&#2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-116">[!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span></span>  
  
4.  <span data-ttu-id="a57f8-117">また、同じ結果は、次の例で行われます。</span><span class="sxs-lookup"><span data-stu-id="a57f8-117">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     <span data-ttu-id="a57f8-118">[!code-vb[VbVbalrLambdas&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-118">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="a57f8-119">単一行のラムダ式のサブルーチンを作成するには</span><span class="sxs-lookup"><span data-stu-id="a57f8-119">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="a57f8-120">デリゲート型を使用できる場所の状況で、キーワードを入力`Sub`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="a57f8-120">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="a57f8-121">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="a57f8-121">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="a57f8-122">かっこで囲んで直後後`Sub`サブルーチンのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-122">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="a57f8-123">後の名前を指定しないことに注意してください。`Sub`します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-123">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="a57f8-124">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="a57f8-124">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="a57f8-125">次のパラメーター リストには、サブルーチンの本文として&1; つのステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-125">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     <span data-ttu-id="a57f8-126">[!code-vb[VbVbalrLambdas&17;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-126">[!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span></span>  
  
     <span data-ttu-id="a57f8-127">ラムダ式は、文字列引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-127">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="a57f8-128">[!code-vb[VbVbalrLambdas&#18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-128">[!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="a57f8-129">複数行のラムダ式の関数を作成するには</span><span class="sxs-lookup"><span data-stu-id="a57f8-129">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="a57f8-130">デリゲート型を使用できる場所の状況で、キーワードを入力`Function`の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="a57f8-130">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="a57f8-131">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="a57f8-131">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="a57f8-132">かっこで囲んで直後後`Function`関数のパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-132">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="a57f8-133">後の名前を指定しないことに注意してください。`Function`します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-133">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="a57f8-134">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="a57f8-134">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="a57f8-135">ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-135">Press ENTER.</span></span> <span data-ttu-id="a57f8-136">`End Function`ステートメントが自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-136">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="a57f8-137">関数の本体内で式を作成し、値を返すには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-137">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="a57f8-138">使用しない、`As`句を戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-138">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="a57f8-139">[!code-vb[VbVbalrLambdas&#19;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-139">[!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span></span>  
  
     <span data-ttu-id="a57f8-140">ラムダ式は、整数の引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-140">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="a57f8-141">[!code-vb[VbVbalrLambdas&#20;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-141">[!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="a57f8-142">複数行のラムダ式のサブルーチンを作成するには</span><span class="sxs-lookup"><span data-stu-id="a57f8-142">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="a57f8-143">どのような状況にデリゲート型を使用できる場所で、キーワードを入力`Sub`次の例のように。</span><span class="sxs-lookup"><span data-stu-id="a57f8-143">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="a57f8-144">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="a57f8-144">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="a57f8-145">かっこで囲んで直後後`Sub`サブルーチンのパラメーターを入力します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-145">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="a57f8-146">後の名前を指定しないことに注意してください。`Sub`します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-146">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="a57f8-147">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="a57f8-147">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="a57f8-148">ENTER キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-148">Press ENTER.</span></span> <span data-ttu-id="a57f8-149">`End Sub`ステートメントが自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-149">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="a57f8-150">関数の本体内で、サブルーチンが呼び出されたときに実行する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-150">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     <span data-ttu-id="a57f8-151">[!code-vb[VbVbalrLambdas #&21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-151">[!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span></span>  
  
     <span data-ttu-id="a57f8-152">ラムダ式は、文字列引数を渡すことによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-152">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="a57f8-153">[!code-vb[VbVbalrLambdas #&22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-153">[!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a57f8-154">例</span><span class="sxs-lookup"><span data-stu-id="a57f8-154">Example</span></span>  
 <span data-ttu-id="a57f8-155">型を持つパラメーターの引数として渡すことができる関数を定義するラムダ式の一般的な用途は、`Delegate`です。</span><span class="sxs-lookup"><span data-stu-id="a57f8-155">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="a57f8-156">次の例では、<xref:System.Diagnostics.Process.GetProcesses%2A>メソッドは、ローカル コンピューター上で実行されるプロセスの配列を返します</xref:System.Diagnostics.Process.GetProcesses%2A>。</span><span class="sxs-lookup"><span data-stu-id="a57f8-156">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="a57f8-157"><xref:System.Linq.Enumerable.Where%2A>からメソッド、<xref:System.Linq.Enumerable>クラスを必要とする`Boolean`デリゲートの引数として</xref:System.Linq.Enumerable></xref:System.Linq.Enumerable.Where%2A>。</span><span class="sxs-lookup"><span data-stu-id="a57f8-157">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="a57f8-158">ラムダ式の例では、その目的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a57f8-158">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="a57f8-159">返す`True`の各プロセスのスレッドが&1; つだけありで選択されている`filteredList`します。</span><span class="sxs-lookup"><span data-stu-id="a57f8-159">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 <span data-ttu-id="a57f8-160">[!code-vb[VbVbalrLambdas&#10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-160">[!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span></span>  
  
 <span data-ttu-id="a57f8-161">前の例は次のコードで記述された[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]構文。</span><span class="sxs-lookup"><span data-stu-id="a57f8-161">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] syntax:</span></span>  
  
 <span data-ttu-id="a57f8-162">[!code-vb[VbVbalrLambdas&#11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="a57f8-162">[!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57f8-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="a57f8-163">See Also</span></span>  
 <span data-ttu-id="a57f8-164"><xref:System.Linq.Enumerable></xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="a57f8-164"><xref:System.Linq.Enumerable></span></span>   
<span data-ttu-id="a57f8-165"> [ラムダ式](./lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="a57f8-165"> [Lambda Expressions](./lambda-expressions.md) </span></span>  
<span data-ttu-id="a57f8-166"> [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a57f8-166"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="a57f8-167"> [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a57f8-167"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="a57f8-168"> [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="a57f8-168"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="a57f8-169"> [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a57f8-169"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="a57f8-170"> [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a57f8-170"> [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="a57f8-171"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="a57f8-171"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
