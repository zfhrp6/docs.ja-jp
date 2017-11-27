---
title: "Do...Loop ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- "conditional statements [Visual Basic], Do�Loop"
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- "loop structures [Visual Basic], Do�Loop statements"
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79d25dce963f383a84b56ce2c9b600fc2d5a7937
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="c2226-102">Do...Loop ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2226-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="c2226-103">ときにステートメント ブロックを繰り返します、`Boolean`条件が`True`、条件になるまで、または`True`です。</span><span class="sxs-lookup"><span data-stu-id="c2226-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2226-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2226-104">Syntax</span></span>  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="c2226-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c2226-105">Parts</span></span>  
  
|<span data-ttu-id="c2226-106">用語</span><span class="sxs-lookup"><span data-stu-id="c2226-106">Term</span></span>|<span data-ttu-id="c2226-107">定義</span><span class="sxs-lookup"><span data-stu-id="c2226-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="c2226-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="c2226-108">Required.</span></span> <span data-ttu-id="c2226-109">定義を開始、`Do`ループします。</span><span class="sxs-lookup"><span data-stu-id="c2226-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="c2226-110">`Until` を使用しない場合に、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="c2226-110">Required unless `Until` is used.</span></span> <span data-ttu-id="c2226-111">までループを繰り返す`condition`は`False`します。</span><span class="sxs-lookup"><span data-stu-id="c2226-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="c2226-112">`While` を使用しない場合に、必ず指定します。</span><span class="sxs-lookup"><span data-stu-id="c2226-112">Required unless `While` is used.</span></span> <span data-ttu-id="c2226-113">までループを繰り返す`condition`は`True`します。</span><span class="sxs-lookup"><span data-stu-id="c2226-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="c2226-114">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c2226-114">Optional.</span></span> <span data-ttu-id="c2226-115">`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="c2226-115">`Boolean` expression.</span></span> <span data-ttu-id="c2226-116">場合`condition`は`Nothing`、Visual Basic として扱います`False`です。</span><span class="sxs-lookup"><span data-stu-id="c2226-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="c2226-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c2226-117">Optional.</span></span> <span data-ttu-id="c2226-118">1 つ以上のステートメント、または、まで繰り返される`condition`は`True`します。</span><span class="sxs-lookup"><span data-stu-id="c2226-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="c2226-119">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c2226-119">Optional.</span></span> <span data-ttu-id="c2226-120">次のイテレーションに制御を転送、`Do`ループします。</span><span class="sxs-lookup"><span data-stu-id="c2226-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="c2226-121">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c2226-121">Optional.</span></span> <span data-ttu-id="c2226-122">うちの制御を転送、`Do`ループします。</span><span class="sxs-lookup"><span data-stu-id="c2226-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="c2226-123">必須です。</span><span class="sxs-lookup"><span data-stu-id="c2226-123">Required.</span></span> <span data-ttu-id="c2226-124">定義を終了、`Do`ループします。</span><span class="sxs-lookup"><span data-stu-id="c2226-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2226-125">コメント</span><span class="sxs-lookup"><span data-stu-id="c2226-125">Remarks</span></span>  
 <span data-ttu-id="c2226-126">使用して、`Do...Loop`一連の条件が満たされるまで何度で不特定数のステートメントを繰り返し使用するときにします。</span><span class="sxs-lookup"><span data-stu-id="c2226-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="c2226-127">セット回数だけ、ステートメントを繰り返し使用する場合、[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)は通常、ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2226-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="c2226-128">いずれかを使用する`While`または`Until`を指定する`condition`、両方は使用しません。</span><span class="sxs-lookup"><span data-stu-id="c2226-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="c2226-129">テストすることができます`condition`先頭またはループの終了のいずれか 1 つだけの時間。</span><span class="sxs-lookup"><span data-stu-id="c2226-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="c2226-130">テストする場合は`condition`、ループの開始時 (で、`Do`ステートメント)、ループが 1 つでも時間が実行されません。</span><span class="sxs-lookup"><span data-stu-id="c2226-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="c2226-131">ループの最後にテストする場合 (で、`Loop`ステートメント)、ループは、少なくとも 1 つの時間を常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c2226-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="c2226-132">条件は、通常 2 つの値の比較から結果します、に評価される任意の式であることができます、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。</span><span class="sxs-lookup"><span data-stu-id="c2226-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="c2226-133">これには、数値型に変換されているなどの他のデータ型の値が含まれます`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="c2226-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="c2226-134">入れ子にすることができます`Do`別内で 1 つのループを記述することによってループします。</span><span class="sxs-lookup"><span data-stu-id="c2226-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="c2226-135">さまざまな種類の他の制御構造を入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c2226-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="c2226-136">詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2226-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2226-137">`Do...Loop`構造体より高い柔軟性を提供する、[中.End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)ループを終了するかどうかを決定することができるためとき`condition`停止されている`True`最初になったときまたは`True`です。</span><span class="sxs-lookup"><span data-stu-id="c2226-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="c2226-138">テストすることもできます`condition`先頭またはループの終了のいずれか。</span><span class="sxs-lookup"><span data-stu-id="c2226-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="c2226-139">操作を終了します。</span><span class="sxs-lookup"><span data-stu-id="c2226-139">Exit Do</span></span>  
 <span data-ttu-id="c2226-140">[Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する代替方法を提供できる、`Do…Loop`です。</span><span class="sxs-lookup"><span data-stu-id="c2226-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="c2226-141">`Exit Do`続くステートメントに直ちに制御を移します、`Loop`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c2226-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="c2226-142">`Exit Do`たとえば、いくつかの条件が評価された後は、よく使用、`If...Then...Else`構造体。</span><span class="sxs-lookup"><span data-stu-id="c2226-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="c2226-143">不要な値が間違っているか、終了要求など、繰り返し処理を続行不可能になったりする条件を検出した場合、ループを終了する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2226-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="c2226-144">用途の 1 つ`Exit Do`を引き起こす可能性のある条件をテストするには、*無限ループ*、これは、大規模なまたは無限も可能回数だけ実行できるループします。</span><span class="sxs-lookup"><span data-stu-id="c2226-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="c2226-145">使用することができます`Exit Do`ループをエスケープするためにします。</span><span class="sxs-lookup"><span data-stu-id="c2226-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="c2226-146">任意の数を含めることができます`Exit Do`内の任意の場所のステートメント、`Do…Loop`です。</span><span class="sxs-lookup"><span data-stu-id="c2226-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="c2226-147">使用すると内で入れ子になった`Do`ループ、`Exit Do`最も内側のループ外と入れ子の上位のレベルに制御を転送します。</span><span class="sxs-lookup"><span data-stu-id="c2226-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2226-148">例</span><span class="sxs-lookup"><span data-stu-id="c2226-148">Example</span></span>  
 <span data-ttu-id="c2226-149">次の例では、ループ内のステートメントするまで引き続き実行、`index`変数が 10 より大きくします。</span><span class="sxs-lookup"><span data-stu-id="c2226-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="c2226-150">`Until`句は、ループの最後にします。</span><span class="sxs-lookup"><span data-stu-id="c2226-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2226-151">例</span><span class="sxs-lookup"><span data-stu-id="c2226-151">Example</span></span>  
 <span data-ttu-id="c2226-152">次の例では、`While`句の代わりに、`Until`句、および`condition`最後の代わりに、ループの開始時にテストします。</span><span class="sxs-lookup"><span data-stu-id="c2226-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2226-153">例</span><span class="sxs-lookup"><span data-stu-id="c2226-153">Example</span></span>  
 <span data-ttu-id="c2226-154">次の例では、`condition`ループを停止するときに、`index`変数が 100 より大きい。</span><span class="sxs-lookup"><span data-stu-id="c2226-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="c2226-155">`If` 、ループ内のステートメントがただし、により、`Exit Do`インデックス変数が 10 よりも大きい場合に、ループを停止するステートメント。</span><span class="sxs-lookup"><span data-stu-id="c2226-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2226-156">例</span><span class="sxs-lookup"><span data-stu-id="c2226-156">Example</span></span>  
 <span data-ttu-id="c2226-157">次の例では、テキスト ファイルのすべての行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="c2226-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="c2226-158"><xref:System.IO.File.OpenText%2A>メソッドは、ファイルを開きを返します、<xref:System.IO.StreamReader>文字を読み取る。</span><span class="sxs-lookup"><span data-stu-id="c2226-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="c2226-159">`Do...Loop`条件、<xref:System.IO.StreamReader.Peek%2A>のメソッド、`StreamReader`を超える文字数があるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c2226-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c2226-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2226-160">See Also</span></span>  
 [<span data-ttu-id="c2226-161">ループ構造</span><span class="sxs-lookup"><span data-stu-id="c2226-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="c2226-162">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="c2226-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="c2226-163">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="c2226-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="c2226-164">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="c2226-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="c2226-165">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="c2226-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="c2226-166">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="c2226-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
