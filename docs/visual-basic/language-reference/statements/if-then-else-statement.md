---
title: If...Then...Else ステートメント (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: 08d51326ee0c9f91eec02467ebcb116354b5033f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604992"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="1089e-102">If...Then...Else ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1089e-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="1089e-103">式の値に応じてステートメント グループを条件付きで実行します。</span><span class="sxs-lookup"><span data-stu-id="1089e-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1089e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1089e-104">Syntax</span></span>  
  
```  
' Multiline syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  

## <a name="quick-links-to-example-code"></a><span data-ttu-id="1089e-105">コード例へのクイック リンク</span><span class="sxs-lookup"><span data-stu-id="1089e-105">Quick links to example code</span></span>

<span data-ttu-id="1089e-106">この記事には使用方法を説明する例いくつかにはが含まれています、`If`しています.`Then`...`Else`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="1089e-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

* [<span data-ttu-id="1089e-107">複数行の構文例</span><span class="sxs-lookup"><span data-stu-id="1089e-107">Multiline syntax example</span></span>](#multi-line)
* [<span data-ttu-id="1089e-108">入れ子になった構文の例</span><span class="sxs-lookup"><span data-stu-id="1089e-108">Nested syntax example</span></span>](#nested)
* [<span data-ttu-id="1089e-109">単一行の構文例</span><span class="sxs-lookup"><span data-stu-id="1089e-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="1089e-110">指定項目</span><span class="sxs-lookup"><span data-stu-id="1089e-110">Parts</span></span>  
 `condition`  
 <span data-ttu-id="1089e-111">必須。</span><span class="sxs-lookup"><span data-stu-id="1089e-111">Required.</span></span> <span data-ttu-id="1089e-112">式。</span><span class="sxs-lookup"><span data-stu-id="1089e-112">Expression.</span></span> <span data-ttu-id="1089e-113">評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="1089e-114">式の場合、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)、条件として扱われます、式が`False`と`Else`ブロックが実行します。</span><span class="sxs-lookup"><span data-stu-id="1089e-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False` and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="1089e-115">単一行の構文では必須複数行の構文でオプションです。</span><span class="sxs-lookup"><span data-stu-id="1089e-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="1089e-116">任意。</span><span class="sxs-lookup"><span data-stu-id="1089e-116">Optional.</span></span> <span data-ttu-id="1089e-117">1 つまたは複数のステートメント次`If`しています.`Then`場合に実行されている`condition`に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="1089e-118">場合は必須`ElseIf`が存在します。</span><span class="sxs-lookup"><span data-stu-id="1089e-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="1089e-119">式。</span><span class="sxs-lookup"><span data-stu-id="1089e-119">Expression.</span></span> <span data-ttu-id="1089e-120">評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="1089e-121">任意。</span><span class="sxs-lookup"><span data-stu-id="1089e-121">Optional.</span></span> <span data-ttu-id="1089e-122">1 つまたは複数のステートメント次`ElseIf`しています.`Then`場合に実行されている`elseifcondition`に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="1089e-123">任意。</span><span class="sxs-lookup"><span data-stu-id="1089e-123">Optional.</span></span> <span data-ttu-id="1089e-124">ない場合に実行される 1 つまたは複数のステートメント`condition`または`elseifcondition`式に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="1089e-125">複数行のバージョンを終了する`If`しています.`Then`...`Else`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1089e-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1089e-126">コメント</span><span class="sxs-lookup"><span data-stu-id="1089e-126">Remarks</span></span>  
  
### <a name="multiline-syntax"></a><span data-ttu-id="1089e-127">複数行の構文</span><span class="sxs-lookup"><span data-stu-id="1089e-127">Multiline syntax</span></span>  
 <span data-ttu-id="1089e-128">ときに、`If`しています.`Then`...`Else`ステートメントが見つかりましたが、`condition`をテストします。</span><span class="sxs-lookup"><span data-stu-id="1089e-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="1089e-129">場合`condition`は`True`、次のステートメント`Then`実行されます。</span><span class="sxs-lookup"><span data-stu-id="1089e-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="1089e-130">場合`condition`は`False`、各`ElseIf`ステートメント (存在する場合) が順番に評価します。</span><span class="sxs-lookup"><span data-stu-id="1089e-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="1089e-131">ときに、 `True` `elseifcondition`が見つかると、すぐに、関連付けられている次のステートメント`ElseIf`実行されます。</span><span class="sxs-lookup"><span data-stu-id="1089e-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="1089e-132">ない場合は`elseifcondition`に評価`True`がある場合、またはなし`ElseIf`ステートメント、次のステートメント`Else`実行されます。</span><span class="sxs-lookup"><span data-stu-id="1089e-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="1089e-133">次のステートメントを実行した後`Then`、 `ElseIf`、または`Else`、ステートメントに次の実行が続行`End If`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="1089e-134">`ElseIf`と`Else`句は、どちらも省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1089e-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="1089e-135">多くとして持つことができます`ElseIf`で必要なときと句、`If`しています.`Then`...`Else`ステートメントがない`ElseIf`句の後に、`Else`句。</span><span class="sxs-lookup"><span data-stu-id="1089e-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="1089e-136">`If`...`Then`...`Else`ステートメントは互いに入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1089e-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="1089e-137">複数行の構文では、`If`ステートメントは、最初の行で唯一のステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1089e-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="1089e-138">`ElseIf`、 `Else`、および`End If`ステートメントの前の行ラベルにのみです。</span><span class="sxs-lookup"><span data-stu-id="1089e-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="1089e-139">`If`しています.`Then`...`Else`ブロックがで終了する必要があります、`End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1089e-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="1089e-140">[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)をいくつかの値を持つ 1 つの式を評価する際に役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="1089e-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
### <a name="single-line-syntax"></a><span data-ttu-id="1089e-141">単一行の構文</span><span class="sxs-lookup"><span data-stu-id="1089e-141">Single-Line syntax</span></span>  
 <span data-ttu-id="1089e-142">True の場合に実行するコードを 1 つの条件の単一行構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1089e-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="1089e-143">ただし、複数行の構文は詳細の構造と柔軟性を提供、読み取り、保守、およびデバッグする方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="1089e-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="1089e-144">次のようにどのような`Then`キーワードが単一行、ステートメントがあるかどうかを調べて確認`If`です。</span><span class="sxs-lookup"><span data-stu-id="1089e-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="1089e-145">後にコメント以外の何かが表示された場合`Then`、同じ行には、ステートメントは単一行として扱われます`If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1089e-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="1089e-146">場合`Then`が存在しない場合は、複数行の開始をする必要があります`If`しています.`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="1089e-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="1089e-147">単一行の構文では、複数のステートメントの結果として実行することが、`If`しています.`Then`意思決定します。</span><span class="sxs-lookup"><span data-stu-id="1089e-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="1089e-148">すべてのステートメントでは、同じ行にある必要があり、コロンで区切っています。</span><span class="sxs-lookup"><span data-stu-id="1089e-148">All statements must be on the same line and be separated by colons.</span></span>  

## <a name="multiline-syntax-example"></a><span data-ttu-id="1089e-149">複数行の構文例</span><span class="sxs-lookup"><span data-stu-id="1089e-149">Multiline syntax example</span></span>

<a name="multi-line"></a>
 
 <span data-ttu-id="1089e-150">次の例では、複数行の構文を使用して、`If`しています.`Then`...`Else`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1089e-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb?highlight=11,14,17,19)]

## <a name="nested-syntax-example"></a><span data-ttu-id="1089e-151">入れ子になった構文の例</span><span class="sxs-lookup"><span data-stu-id="1089e-151">Nested syntax example</span></span>

<a name="nested"></a>

 <span data-ttu-id="1089e-152">次の例を含む入れ子になった`If`しています.`Then`...`Else`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1089e-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb?highlight=14,15,17,19,20,21,23,25,26,28)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="1089e-153">単一行の構文例</span><span class="sxs-lookup"><span data-stu-id="1089e-153">Single-Line syntax example</span></span>
  
<a name="single-line"></a> <span data-ttu-id="1089e-154">次の例では、単一行の構文の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="1089e-154">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb?highlight=18)]
  
## <a name="see-also"></a><span data-ttu-id="1089e-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="1089e-155">See also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="1089e-156">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1089e-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="1089e-157">Select...Case ステートメント</span><span class="sxs-lookup"><span data-stu-id="1089e-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="1089e-158">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="1089e-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="1089e-159">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="1089e-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="1089e-160">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="1089e-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="1089e-161">If 演算子</span><span class="sxs-lookup"><span data-stu-id="1089e-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
