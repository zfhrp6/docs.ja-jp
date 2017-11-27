---
title: "Exit ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="5faff-102">Exit ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5faff-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="5faff-103">プロシージャまたはブロックを終了し、プロシージャ呼び出しまたはブロックの定義を次のステートメントに制御を直ちに転送します。</span><span class="sxs-lookup"><span data-stu-id="5faff-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5faff-104">構文</span><span class="sxs-lookup"><span data-stu-id="5faff-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="5faff-105">ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="5faff-106">すぐに終了させる、`Do`ループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5faff-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="5faff-107">ステートメントに次の実行が続行、`Loop`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="5faff-108">`Exit Do`内でのみ使用できます、`Do`ループします。</span><span class="sxs-lookup"><span data-stu-id="5faff-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="5faff-109">使用すると内で入れ子になった`Do`ループ、`Exit Do`最も内側のループを終了し、入れ子の上位のレベルに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="5faff-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="5faff-110">すぐに終了させる、`For`ループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5faff-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="5faff-111">ステートメントに次の実行が続行、`Next`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="5faff-112">`Exit For`内でのみ使用できます、`For`しています.`Next`または`For Each`しています.`Next`ループします。</span><span class="sxs-lookup"><span data-stu-id="5faff-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="5faff-113">使用すると内で入れ子になった`For`ループ、`Exit For`最も内側のループを終了し、入れ子の上位のレベルに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="5faff-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="5faff-114">すぐに終了させる、`Function`が表示される手順です。</span><span class="sxs-lookup"><span data-stu-id="5faff-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="5faff-115">呼び出したステートメントの次のステートメントと実行が継続、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5faff-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="5faff-116">`Exit Function`内でのみ使用できます、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5faff-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="5faff-117">戻り値を指定するには前に、の行に関数名に値を割り当てることができます、`Exit Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="5faff-118">戻り値を代入し、1 つのステートメント内で、関数の終了、代わりに使用できます、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="5faff-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="5faff-119">すぐに終了させる、`Property`が表示される手順です。</span><span class="sxs-lookup"><span data-stu-id="5faff-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="5faff-120">呼び出したステートメントと実行が継続、`Property`手順、つまり、要求またはプロパティの値を設定するステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="5faff-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="5faff-121">`Exit Property`プロパティの内部でのみ使用できます`Get`または`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5faff-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="5faff-122">戻り値を指定する、`Get`プロシージャ前に、の行に関数名に値を割り当てることができます、`Exit Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="5faff-123">戻り値および終了に割り当てる、 `Get` 1 つのステートメントでプロシージャを使用する、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="5faff-124">`Set`プロシージャ、`Exit Property`ステートメントは等価、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="5faff-125">すぐに終了させる、`Select Case`ブロックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5faff-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="5faff-126">ステートメントに次の実行が続行、`End Select`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="5faff-127">`Exit Select`内でのみ使用できます、`Select Case`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="5faff-128">すぐに終了させる、`Sub`が表示される手順です。</span><span class="sxs-lookup"><span data-stu-id="5faff-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="5faff-129">呼び出したステートメントの次のステートメントと実行が継続、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5faff-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="5faff-130">`Exit Sub`内でのみ使用できます、`Sub`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="5faff-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="5faff-131">`Sub`プロシージャ、`Exit Sub`ステートメントは等価、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="5faff-132">すぐに終了させる、`Try`または`Catch`ブロックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5faff-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="5faff-133">実行が継続、 `Finally` 、1 つを使用する必要がある場合、またはステートメントに次のブロック、`End Try`ステートメントがそれ以外の場合。</span><span class="sxs-lookup"><span data-stu-id="5faff-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="5faff-134">`Exit Try`内でのみ使用できます、`Try`または`Catch`ブロックといない内側、`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="5faff-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="5faff-135">すぐに終了させる、`While`ループが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5faff-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="5faff-136">ステートメントに次の実行が続行、`End While`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="5faff-137">`Exit While`内でのみ使用できます、`While`ループします。</span><span class="sxs-lookup"><span data-stu-id="5faff-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="5faff-138">使用すると内で入れ子になった`While`ループ、`Exit While`ループ ループの 1 つの入れ子になったレベルに制御を移します場所`Exit While`が発生します。</span><span class="sxs-lookup"><span data-stu-id="5faff-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5faff-139">コメント</span><span class="sxs-lookup"><span data-stu-id="5faff-139">Remarks</span></span>  
 <span data-ttu-id="5faff-140">混同しないでください`Exit`ステートメントと`End`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5faff-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="5faff-141">`Exit`ステートメントの末尾を一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="5faff-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5faff-142">例</span><span class="sxs-lookup"><span data-stu-id="5faff-142">Example</span></span>  
 <span data-ttu-id="5faff-143">次の例では、ループの条件は、ループを停止するときに、`index`変数が 100 より大きい。</span><span class="sxs-lookup"><span data-stu-id="5faff-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="5faff-144">`If` 、ループ内のステートメントがただし、により、`Exit Do`インデックス変数が 10 よりも大きい場合に、ループを停止するステートメント。</span><span class="sxs-lookup"><span data-stu-id="5faff-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="5faff-145">例</span><span class="sxs-lookup"><span data-stu-id="5faff-145">Example</span></span>  
 <span data-ttu-id="5faff-146">次の例では、戻り値を割り当てて、関数名に`myFunction`、しを使用して`Exit Function`関数から返される。</span><span class="sxs-lookup"><span data-stu-id="5faff-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="5faff-147">例</span><span class="sxs-lookup"><span data-stu-id="5faff-147">Example</span></span>  
 <span data-ttu-id="5faff-148">次の例では、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)を戻り値を代入し、関数を終了します。</span><span class="sxs-lookup"><span data-stu-id="5faff-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5faff-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="5faff-149">See Also</span></span>  
 [<span data-ttu-id="5faff-150">Continue ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [<span data-ttu-id="5faff-151">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="5faff-152">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="5faff-153">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="5faff-154">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="5faff-155">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="5faff-156">Return ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="5faff-157">Stop ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="5faff-158">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="5faff-159">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="5faff-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
