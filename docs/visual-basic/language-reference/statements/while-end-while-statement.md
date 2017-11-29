---
title: "While...End While ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5f831f233eaa4f1c38d56f3a89bda9b0cf1bccaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="584cf-102">While...End While ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="584cf-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="584cf-103">指定された条件が限りは、一連のステートメントを実行`True`です。</span><span class="sxs-lookup"><span data-stu-id="584cf-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="584cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="584cf-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="584cf-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="584cf-105">Parts</span></span>  
  
|<span data-ttu-id="584cf-106">用語</span><span class="sxs-lookup"><span data-stu-id="584cf-106">Term</span></span>|<span data-ttu-id="584cf-107">定義</span><span class="sxs-lookup"><span data-stu-id="584cf-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="584cf-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="584cf-108">Required.</span></span> <span data-ttu-id="584cf-109">`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="584cf-109">`Boolean` expression.</span></span> <span data-ttu-id="584cf-110">場合`condition`は`Nothing`、Visual Basic として扱います`False`です。</span><span class="sxs-lookup"><span data-stu-id="584cf-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="584cf-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="584cf-111">Optional.</span></span> <span data-ttu-id="584cf-112">1 つまたは複数のステートメント次`While`、たびに実行される`condition`は`True`します。</span><span class="sxs-lookup"><span data-stu-id="584cf-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="584cf-113">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="584cf-113">Optional.</span></span> <span data-ttu-id="584cf-114">次のイテレーションに制御を転送、`While`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="584cf-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="584cf-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="584cf-115">Optional.</span></span> <span data-ttu-id="584cf-116">うちの制御を転送、`While`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="584cf-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="584cf-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="584cf-117">Required.</span></span> <span data-ttu-id="584cf-118">`While` ブロックの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="584cf-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="584cf-119">コメント</span><span class="sxs-lookup"><span data-stu-id="584cf-119">Remarks</span></span>  
 <span data-ttu-id="584cf-120">使用して、`While...End While`条件が限り回数、不特定数のステートメントのセットを繰り返したいときに`True`です。</span><span class="sxs-lookup"><span data-stu-id="584cf-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="584cf-121">方がよい場合に、その条件をテストするか、結果の判定をより柔軟にテストする場合、[操作を行います.ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="584cf-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="584cf-122">セット回数だけ、ステートメントを繰り返し使用する場合、[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)は通常、ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="584cf-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="584cf-123">`While`キーワードでも使用、[操作を行います.ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)、 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)と[Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="584cf-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="584cf-124">場合`condition`は`True`、すべての`statements`まで実行、`End While`ステートメントが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="584cf-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="584cf-125">制御を返します、`While`ステートメント、および`condition`が再度チェックします。</span><span class="sxs-lookup"><span data-stu-id="584cf-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="584cf-126">場合`condition`まだ`True`プロセスが繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="584cf-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="584cf-127">`False`、これに続くステートメントにパスを制御、`End While`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="584cf-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="584cf-128">`While`ステートメントは常には、ループを開始する前に、条件をチェックします。</span><span class="sxs-lookup"><span data-stu-id="584cf-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="584cf-129">条件がループが継続`True`です。</span><span class="sxs-lookup"><span data-stu-id="584cf-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="584cf-130">場合`condition`は`False`一度も実行しない、ループを最初に入力したときにします。</span><span class="sxs-lookup"><span data-stu-id="584cf-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="584cf-131">`condition`が 2 つの値の比較からの結果に評価される任意の式は、通常、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値 (`True`または`False`)。</span><span class="sxs-lookup"><span data-stu-id="584cf-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="584cf-132">この式は、数値型に変換されているなどの別のデータ型の値を含めることができます`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="584cf-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="584cf-133">入れ子にすることができます`While`別内で 1 つのループを配置することでループします。</span><span class="sxs-lookup"><span data-stu-id="584cf-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="584cf-134">さまざまな種類の制御構造を入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="584cf-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="584cf-135">詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。</span><span class="sxs-lookup"><span data-stu-id="584cf-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="584cf-136">中に終了</span><span class="sxs-lookup"><span data-stu-id="584cf-136">Exit While</span></span>  
 <span data-ttu-id="584cf-137">[終了中に](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントが終了する別の方法を提供できます、`While`ループします。</span><span class="sxs-lookup"><span data-stu-id="584cf-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="584cf-138">`Exit While`すぐに続くステートメントに制御を転送、`End While`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="584cf-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="584cf-139">通常使用`Exit While`いくつかの条件が評価された後 (たとえば、`If...Then...Else`構造) です。</span><span class="sxs-lookup"><span data-stu-id="584cf-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="584cf-140">不要な値が間違っているか、終了要求など、繰り返し処理を続行不可能になったりする条件を検出した場合、ループを終了する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="584cf-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="584cf-141">使用することができます`Exit While`原因となる条件をテストするとき、*無限ループ*、これは、非常に大規模なまたは無限も可能回数だけ実行できるループします。</span><span class="sxs-lookup"><span data-stu-id="584cf-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="584cf-142">使用してできます`Exit While`ループをエスケープするためにします。</span><span class="sxs-lookup"><span data-stu-id="584cf-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="584cf-143">任意の数を配置する`Exit While`内の任意の場所のステートメント、`While`ループします。</span><span class="sxs-lookup"><span data-stu-id="584cf-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="584cf-144">使用すると内で入れ子になった`While`ループ、`Exit While`最も内側のループ外と入れ子の上位のレベルに制御を転送します。</span><span class="sxs-lookup"><span data-stu-id="584cf-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="584cf-145">`Continue While`ステートメントはすぐに、ループの次のイテレーションに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="584cf-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="584cf-146">詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="584cf-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="584cf-147">例</span><span class="sxs-lookup"><span data-stu-id="584cf-147">Example</span></span>  
 <span data-ttu-id="584cf-148">次の例では、ループ内のステートメントするまで引き続き実行、`index`変数が 10 より大きくします。</span><span class="sxs-lookup"><span data-stu-id="584cf-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="584cf-149">例</span><span class="sxs-lookup"><span data-stu-id="584cf-149">Example</span></span>  
 <span data-ttu-id="584cf-150">次の例では、使用、`Continue While`と`Exit While`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="584cf-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="584cf-151">例</span><span class="sxs-lookup"><span data-stu-id="584cf-151">Example</span></span>  
 <span data-ttu-id="584cf-152">次の例では、テキスト ファイルのすべての行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="584cf-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="584cf-153"><xref:System.IO.File.OpenText%2A>メソッドは、ファイルを開きを返します、<xref:System.IO.StreamReader>文字を読み取る。</span><span class="sxs-lookup"><span data-stu-id="584cf-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="584cf-154">`While`条件、<xref:System.IO.StreamReader.Peek%2A>のメソッド、`StreamReader`ファイルに追加の文字が含まれるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="584cf-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="584cf-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="584cf-155">See Also</span></span>  
 [<span data-ttu-id="584cf-156">ループ構造</span><span class="sxs-lookup"><span data-stu-id="584cf-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="584cf-157">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="584cf-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="584cf-158">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="584cf-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="584cf-159">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="584cf-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="584cf-160">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="584cf-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="584cf-161">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="584cf-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="584cf-162">Continue ステートメント</span><span class="sxs-lookup"><span data-stu-id="584cf-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
