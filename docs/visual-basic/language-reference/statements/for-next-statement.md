---
title: "For...Next ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: "64"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a50f44a167952c735c6ed2830ca87105413401b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="b43fa-102">For...Next ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b43fa-102">For...Next Statement (Visual Basic)</span></span>
<span data-ttu-id="b43fa-103">ステートメントのグループを指定した回数だけ繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="b43fa-103">Repeats a group of statements a specified number of times.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b43fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="b43fa-104">Syntax</span></span>  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b43fa-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="b43fa-105">Parts</span></span>  
  
|<span data-ttu-id="b43fa-106">パーツ</span><span class="sxs-lookup"><span data-stu-id="b43fa-106">Part</span></span>|<span data-ttu-id="b43fa-107">説明</span><span class="sxs-lookup"><span data-stu-id="b43fa-107">Description</span></span>|  
|----------|-----------------|  
|`counter`|<span data-ttu-id="b43fa-108">必要な`For`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-108">Required in the `For` statement.</span></span> <span data-ttu-id="b43fa-109">数値型の変数です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-109">Numeric variable.</span></span> <span data-ttu-id="b43fa-110">ループの制御変数。</span><span class="sxs-lookup"><span data-stu-id="b43fa-110">The control variable for the loop.</span></span> <span data-ttu-id="b43fa-111">詳細については、次を参照してください。[カウンター引数](#BKMK_Counter)このトピックで後述します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|  
|`datatype`|<span data-ttu-id="b43fa-112">任意。</span><span class="sxs-lookup"><span data-stu-id="b43fa-112">Optional.</span></span> <span data-ttu-id="b43fa-113">データ型`counter`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-113">Data type of `counter`.</span></span> <span data-ttu-id="b43fa-114">詳細については、次を参照してください。[カウンター引数](#BKMK_Counter)このトピックで後述します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|  
|`start`|<span data-ttu-id="b43fa-115">必須。</span><span class="sxs-lookup"><span data-stu-id="b43fa-115">Required.</span></span> <span data-ttu-id="b43fa-116">数値式です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-116">Numeric expression.</span></span> <span data-ttu-id="b43fa-117">`counter` の初期値になります。</span><span class="sxs-lookup"><span data-stu-id="b43fa-117">The initial value of `counter`.</span></span>|  
|`end`|<span data-ttu-id="b43fa-118">必須。</span><span class="sxs-lookup"><span data-stu-id="b43fa-118">Required.</span></span> <span data-ttu-id="b43fa-119">数値式です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-119">Numeric expression.</span></span> <span data-ttu-id="b43fa-120">最終値`counter`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-120">The final value of `counter`.</span></span>|  
|`step`|<span data-ttu-id="b43fa-121">任意。</span><span class="sxs-lookup"><span data-stu-id="b43fa-121">Optional.</span></span> <span data-ttu-id="b43fa-122">数値式です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-122">Numeric expression.</span></span> <span data-ttu-id="b43fa-123">量`counter`ループのたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="b43fa-123">The amount by which `counter` is incremented each time through the loop.</span></span>|  
|`statements`|<span data-ttu-id="b43fa-124">任意。</span><span class="sxs-lookup"><span data-stu-id="b43fa-124">Optional.</span></span> <span data-ttu-id="b43fa-125">1 つまたは複数のステートメントの間で`For`と`Next`一定の回数を実行します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|  
|`Continue For`|<span data-ttu-id="b43fa-126">任意。</span><span class="sxs-lookup"><span data-stu-id="b43fa-126">Optional.</span></span> <span data-ttu-id="b43fa-127">次のループ反復に制御を転送します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-127">Transfers control to the next loop iteration.</span></span>|  
|`Exit For`|<span data-ttu-id="b43fa-128">任意。</span><span class="sxs-lookup"><span data-stu-id="b43fa-128">Optional.</span></span> <span data-ttu-id="b43fa-129">うちの制御を転送、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-129">Transfers control out of the `For` loop.</span></span>|  
|`Next`|<span data-ttu-id="b43fa-130">必須。</span><span class="sxs-lookup"><span data-stu-id="b43fa-130">Required.</span></span> <span data-ttu-id="b43fa-131">定義を終了、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-131">Terminates the definition of the `For` loop.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b43fa-132">`To`キーワードは、カウンターの範囲を指定する次のステートメントで使用します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="b43fa-133">このキーワードを使用することも、[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)および配列の宣言。</span><span class="sxs-lookup"><span data-stu-id="b43fa-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="b43fa-134">配列の宣言の詳細については、次を参照してください。 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="simple-examples"></a><span data-ttu-id="b43fa-135">簡単な例</span><span class="sxs-lookup"><span data-stu-id="b43fa-135">Simple Examples</span></span>  
 <span data-ttu-id="b43fa-136">使用する、`For`しています.`Next`ステートメントのセットに指定された回数だけを繰り返し使用するときにします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>  
  
 <span data-ttu-id="b43fa-137">次の例で、`index`変数が 1 の値から開始して、終了の値の後に、ループの反復するたびにインクリメントされます`index`5 に到達します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 <span data-ttu-id="b43fa-138">次の例で、`number`変数が 2 から開始され、終了の値の後に、ループの反復ごとに 0.25 で高い縮小効果が`number`0 に到達します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="b43fa-139">`Step`の引数`-.25`ループの反復ごとに 0.25 で値が減少します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  <span data-ttu-id="b43fa-140">A[中.While ステートメント終了](../../../visual-basic/language-reference/statements/while-end-while-statement.md)または[操作を行います.Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)しないわかっている場合に事前に、ループでステートメントを実行する回数をうまく動作します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="b43fa-141">ただし、特定回数、ループを実行しようとする`For`しています.`Next`ループをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="b43fa-142">ループを最初に入力したときに、イテレーションの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-142">You determine the number of iterations when you first enter the loop.</span></span>  
  
## <a name="nesting-loops"></a><span data-ttu-id="b43fa-143">ループの入れ子</span><span class="sxs-lookup"><span data-stu-id="b43fa-143">Nesting Loops</span></span>  
 <span data-ttu-id="b43fa-144">入れ子にすることができます`For`別内で 1 つのループを記述することによってループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="b43fa-145">次の例で入れ子になった`For`しています.`Next`異なるステップ値を持つ構造体。</span><span class="sxs-lookup"><span data-stu-id="b43fa-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="b43fa-146">外側のループでは、ループのイテレーションごとに文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="b43fa-147">内部では、ループのイテレーションごとにループ カウンター変数をデクリメントをループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 <span data-ttu-id="b43fa-148">ループを入れ子にする場合は、各ループが一意な必要があります`counter`変数。</span><span class="sxs-lookup"><span data-stu-id="b43fa-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>  
  
 <span data-ttu-id="b43fa-149">互いにさまざまな種類の制御構造を入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b43fa-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="b43fa-150">詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-for-and-continue-for"></a><span data-ttu-id="b43fa-151">終了し、続行</span><span class="sxs-lookup"><span data-stu-id="b43fa-151">Exit For and Continue For</span></span>  
 <span data-ttu-id="b43fa-152">`Exit For`ステートメントがすぐに終了させる、`For`しています.`Next`</span><span class="sxs-lookup"><span data-stu-id="b43fa-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="b43fa-153">これに続くステートメントにループと転送の制御、`Next`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>  
  
 <span data-ttu-id="b43fa-154">`Continue For`ステートメントに制御を移しますすぐに、ループの次の反復処理します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="b43fa-155">詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
 <span data-ttu-id="b43fa-156">次の例では、使用、`Continue For`と`Exit For`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 <span data-ttu-id="b43fa-157">任意の数を配置する`Exit For`内のステートメント、`For`しています.`Next`</span><span class="sxs-lookup"><span data-stu-id="b43fa-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="b43fa-158">ループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-158">loop.</span></span> <span data-ttu-id="b43fa-159">使用すると内で入れ子になった`For`しています.`Next`</span><span class="sxs-lookup"><span data-stu-id="b43fa-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="b43fa-160">ループ、`Exit For`最も内側のループを終了し、入れ子の上位のレベルに制御を移します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="b43fa-161">`Exit For`いくつかの条件を評価した後は、よく使用 (たとえば、 `If`.`Then`...`Else`構造体)。</span><span class="sxs-lookup"><span data-stu-id="b43fa-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="b43fa-162">使用することができます`Exit For`次の条件。</span><span class="sxs-lookup"><span data-stu-id="b43fa-162">You might want to use `Exit For` for the following conditions:</span></span>  
  
-   <span data-ttu-id="b43fa-163">反復処理を続行するは、不要なまたは不可能です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="b43fa-164">値が間違っているか、終了要求は、この状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b43fa-164">An erroneous value or a termination request might create this condition.</span></span>  
  
-   <span data-ttu-id="b43fa-165">A`Try`しています.`Catch`...`Finally`ステートメントは、例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="b43fa-166">使用する場合があります`Exit For`の最後に、`Finally`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-166">You might use `Exit For` at the end of the `Finally` block.</span></span>  
  
-   <span data-ttu-id="b43fa-167">これは、大規模なまたは無限も可能回数だけ実行できるループ、無限ループがあります。</span><span class="sxs-lookup"><span data-stu-id="b43fa-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="b43fa-168">このような条件を検出した場合を使用できます`Exit For`ループをエスケープするためにします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="b43fa-169">詳細については、次を参照してください[操作を行います.。ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="b43fa-170">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="b43fa-170">Technical Implementation</span></span>  
 <span data-ttu-id="b43fa-171">ときに、`For`しています.`Next`ループが開始、Visual Basic の評価`start`、 `end`、および`step`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="b43fa-172">Visual Basic では、この時間とし、割り当てにのみこれらの値を評価`start`に`counter`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="b43fa-173">ステートメントの前にブロックが実行される Visual Basic 比較`counter`に`end`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="b43fa-174">場合`counter`よりも大きいは既に、`end`値 (より小さい場合、または`step`が負の値)、`For`終了をループし、これに続くステートメントにパスを制御、`Next`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="b43fa-175">それ以外の場合、ステートメント ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="b43fa-175">Otherwise, the statement block runs.</span></span>  
  
 <span data-ttu-id="b43fa-176">Visual Basic が発生するたびに、`Next`ステートメントでは、インクリメント`counter`によって`step`を返すと、`For`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="b43fa-177">もう一度比較`counter`に`end`、もう一度、ブロックが実行か、結果に応じて、ループを終了するとします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="b43fa-178">までこの処理を続けます`counter`渡します`end`または`Exit For`ステートメントが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="b43fa-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>  
  
 <span data-ttu-id="b43fa-179">まで、ループが停止しない`counter`経過`end`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="b43fa-180">場合`counter`と等しい`end`ループを続行します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="b43fa-181">ブロックを実行するかどうかを判断する比較では、 `counter`  <=  `end`場合`step`が正の値と`counter`  >=  `end`場合`step`が負の値。</span><span class="sxs-lookup"><span data-stu-id="b43fa-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>  
  
 <span data-ttu-id="b43fa-182">値を変更する場合`counter`ループ内は、コードを読み取りやデバッグが困難にする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b43fa-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="b43fa-183">値を変更する`start`、 `end`、または`step`ループが最初に入力されたときに決定されたイテレーション値には影響しません。</span><span class="sxs-lookup"><span data-stu-id="b43fa-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>  
  
 <span data-ttu-id="b43fa-184">ループを入れ子にする場合、コンパイラはエラーが発生するか、`Next`する前に外部の入れ子レベルのステートメント、`Next`内部レベルのステートメント。</span><span class="sxs-lookup"><span data-stu-id="b43fa-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="b43fa-185">ただし、コンパイラが検出できるこれを指定する場合にのみ、エラーを重複`counter`ですべて`Next`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>  
  
### <a name="step-argument"></a><span data-ttu-id="b43fa-186">Step</span><span class="sxs-lookup"><span data-stu-id="b43fa-186">Step Argument</span></span>  
 <span data-ttu-id="b43fa-187">値`step`正または負の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b43fa-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="b43fa-188">このパラメーターは、次の表に従ってループ処理を決定します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-188">This parameter determines loop processing according to the following table:</span></span>  
  
|<span data-ttu-id="b43fa-189">**ステップ値**</span><span class="sxs-lookup"><span data-stu-id="b43fa-189">**Step value**</span></span>|<span data-ttu-id="b43fa-190">**場合に、ループが実行されます。**</span><span class="sxs-lookup"><span data-stu-id="b43fa-190">**Loop executes if**</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="b43fa-191">正またはゼロ</span><span class="sxs-lookup"><span data-stu-id="b43fa-191">Positive or zero</span></span>|`counter` <= `end`|  
|<span data-ttu-id="b43fa-192">負</span><span class="sxs-lookup"><span data-stu-id="b43fa-192">Negative</span></span>|`counter` >= `end`|  
  
 <span data-ttu-id="b43fa-193">既定値の`step`は 1 です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-193">The default value of `step` is 1.</span></span>  
  
###  <a name="BKMK_Counter"></a><span data-ttu-id="b43fa-194">カウンターの引数</span><span class="sxs-lookup"><span data-stu-id="b43fa-194">Counter Argument</span></span>  
 <span data-ttu-id="b43fa-195">次の表に示すかどうか`counter`全体を対象とする新しいローカル変数を定義`For…Next`ループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="b43fa-196">この決定によって異なるかどうか`datatype`が存在かどうかおよび`counter`は既に定義されています。</span><span class="sxs-lookup"><span data-stu-id="b43fa-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>  
  
|<span data-ttu-id="b43fa-197">`datatype`存在しますか?</span><span class="sxs-lookup"><span data-stu-id="b43fa-197">Is `datatype` present?</span></span>|<span data-ttu-id="b43fa-198">`counter`既に定義されていますか。</span><span class="sxs-lookup"><span data-stu-id="b43fa-198">Is `counter` already defined?</span></span>|<span data-ttu-id="b43fa-199">結果 (かどうか`counter`全体を対象とする新しいローカル変数を定義`For...Next`ループ)</span><span class="sxs-lookup"><span data-stu-id="b43fa-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="b43fa-200">いいえ</span><span class="sxs-lookup"><span data-stu-id="b43fa-200">No</span></span>|<span data-ttu-id="b43fa-201">はい</span><span class="sxs-lookup"><span data-stu-id="b43fa-201">Yes</span></span>|<span data-ttu-id="b43fa-202">いいえ、ため`counter`は既に定義されています。</span><span class="sxs-lookup"><span data-stu-id="b43fa-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="b43fa-203">場合のスコープ`counter`コンパイル警告が発生した、プロシージャに対してローカルにないです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|  
|<span data-ttu-id="b43fa-204">いいえ</span><span class="sxs-lookup"><span data-stu-id="b43fa-204">No</span></span>|<span data-ttu-id="b43fa-205">いいえ</span><span class="sxs-lookup"><span data-stu-id="b43fa-205">No</span></span>|<span data-ttu-id="b43fa-206">はい。</span><span class="sxs-lookup"><span data-stu-id="b43fa-206">Yes.</span></span> <span data-ttu-id="b43fa-207">データ型から推論されます、 `start`、 `end`、および`step`式。</span><span class="sxs-lookup"><span data-stu-id="b43fa-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="b43fa-208">型の推定については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|  
|<span data-ttu-id="b43fa-209">[はい]</span><span class="sxs-lookup"><span data-stu-id="b43fa-209">Yes</span></span>|<span data-ttu-id="b43fa-210">はい</span><span class="sxs-lookup"><span data-stu-id="b43fa-210">Yes</span></span>|<span data-ttu-id="b43fa-211">場合に限り、[はい]、既存の`counter`プロシージャの外部から変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="b43fa-212">その変数は別に維持します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-212">That variable remains separate.</span></span> <span data-ttu-id="b43fa-213">場合、既存のスコープ`counter`変数は、プロシージャに対してローカルに、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="b43fa-214">はい</span><span class="sxs-lookup"><span data-stu-id="b43fa-214">Yes</span></span>|<span data-ttu-id="b43fa-215">いいえ</span><span class="sxs-lookup"><span data-stu-id="b43fa-215">No</span></span>|<span data-ttu-id="b43fa-216">はい。</span><span class="sxs-lookup"><span data-stu-id="b43fa-216">Yes.</span></span>|  
  
 <span data-ttu-id="b43fa-217">データ型`counter`イテレーションでは、次の種類のいずれかを指定する必要がありますの種類を決定します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>  
  
-   <span data-ttu-id="b43fa-218">A `Byte`、 `SByte`、 `UShort`、 `Short`、 `UInteger`、 `Integer`、 `ULong`、 `Long`、 `Decimal`、 `Single`、または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>  
  
-   <span data-ttu-id="b43fa-219">使用して宣言された列挙型、 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
-   <span data-ttu-id="b43fa-220">`Object`。</span><span class="sxs-lookup"><span data-stu-id="b43fa-220">An `Object`.</span></span>  
  
-   <span data-ttu-id="b43fa-221">型`T`、次の演算子を持つ場所`B`型で使用できるは、`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="b43fa-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 <span data-ttu-id="b43fa-222">必要に応じて指定することができます、`counter`に変数が、`Next`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="b43fa-223">入れ子にしていない場合は特に、この構文は、プログラムの読みやすさを向上`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="b43fa-224">対応する表示される変数を指定する必要があります`For`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b43fa-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>  
  
 <span data-ttu-id="b43fa-225">`start`、 `end`、および`step`の型に拡大する任意のデータ型に式が評価される`counter`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="b43fa-226">ユーザー定義型を使用する場合`counter`を定義する必要があります、`CType`変換演算子の型に変換する`start`、 `end`、または`step`の型に`counter`です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b43fa-227">例</span><span class="sxs-lookup"><span data-stu-id="b43fa-227">Example</span></span>  
 <span data-ttu-id="b43fa-228">次の例では、ジェネリック リストからすべての要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="b43fa-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="b43fa-229">代わりに、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)の例に示す、`For`しています.`Next`降順に反復処理するステートメント。</span><span class="sxs-lookup"><span data-stu-id="b43fa-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="b43fa-230">この例は、ためにこの手法を使用して、`removeAt`メソッドが低いインデックス値を持つ削除された要素の後に要素をによりします。</span><span class="sxs-lookup"><span data-stu-id="b43fa-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="b43fa-231">例</span><span class="sxs-lookup"><span data-stu-id="b43fa-231">Example</span></span>  
 <span data-ttu-id="b43fa-232">次の例を使用して宣言されている列挙型を反復処理する[Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="b43fa-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="b43fa-233">例</span><span class="sxs-lookup"><span data-stu-id="b43fa-233">Example</span></span>  
 <span data-ttu-id="b43fa-234">次の例では、ステートメントのパラメーターが演算子のオーバー ロードを持つクラスを使用して、 `+`、 `-`、 `>=`、および`<=`演算子。</span><span class="sxs-lookup"><span data-stu-id="b43fa-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b43fa-235">参照</span><span class="sxs-lookup"><span data-stu-id="b43fa-235">See Also</span></span>  
 <xref:System.Collections.Generic.List%601>  
 [<span data-ttu-id="b43fa-236">ループ構造</span><span class="sxs-lookup"><span data-stu-id="b43fa-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="b43fa-237">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="b43fa-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="b43fa-238">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="b43fa-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="b43fa-239">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="b43fa-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="b43fa-240">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="b43fa-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="b43fa-241">コレクション</span><span class="sxs-lookup"><span data-stu-id="b43fa-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
