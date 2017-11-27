---
title: "If...Then...Else ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="ac779-102">If...Then...Else ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac779-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="ac779-103">式の値に応じてステートメント グループを条件付きで実行します。</span><span class="sxs-lookup"><span data-stu-id="ac779-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac779-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac779-104">Syntax</span></span>  
  
```  
' Multiple-line syntax:  
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
  
## <a name="parts"></a><span data-ttu-id="ac779-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="ac779-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="ac779-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="ac779-106">Required.</span></span> <span data-ttu-id="ac779-107">式。</span><span class="sxs-lookup"><span data-stu-id="ac779-107">Expression.</span></span> <span data-ttu-id="ac779-108">評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-108">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="ac779-109">式の場合、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)、条件として扱われます式ではありません`True`、および`Else`ブロックは、実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac779-109">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is not `True`, and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="ac779-110">単一行の構文では必須複数行の構文でオプションです。</span><span class="sxs-lookup"><span data-stu-id="ac779-110">Required in the single-line syntax; optional in the multiple-line syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="ac779-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ac779-111">Optional.</span></span> <span data-ttu-id="ac779-112">1 つまたは複数のステートメント次`If`しています.`Then`場合に実行されている`condition`に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-112">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="ac779-113">場合は必須`ElseIf`が存在します。</span><span class="sxs-lookup"><span data-stu-id="ac779-113">Required if `ElseIf` is present.</span></span> <span data-ttu-id="ac779-114">式。</span><span class="sxs-lookup"><span data-stu-id="ac779-114">Expression.</span></span> <span data-ttu-id="ac779-115">評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-115">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="ac779-116">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ac779-116">Optional.</span></span> <span data-ttu-id="ac779-117">1 つまたは複数のステートメント次`ElseIf`しています.`Then`場合に実行されている`elseifcondition`に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-117">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="ac779-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ac779-118">Optional.</span></span> <span data-ttu-id="ac779-119">ない場合に実行される 1 つまたは複数のステートメント`condition`または`elseifcondition`式に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-119">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="ac779-120">終了、`If`しています.`Then`...`Else`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="ac779-120">Terminates the `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac779-121">コメント</span><span class="sxs-lookup"><span data-stu-id="ac779-121">Remarks</span></span>  
  
## <a name="multiple-line-syntax"></a><span data-ttu-id="ac779-122">複数行の構文</span><span class="sxs-lookup"><span data-stu-id="ac779-122">Multiple-Line Syntax</span></span>  
 <span data-ttu-id="ac779-123">ときに、`If`しています.`Then`...`Else`ステートメントが見つかりましたが、`condition`をテストします。</span><span class="sxs-lookup"><span data-stu-id="ac779-123">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="ac779-124">場合`condition`は`True`、次のステートメント`Then`実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac779-124">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="ac779-125">場合`condition`は`False`、各`ElseIf`ステートメント (存在する場合) が順番に評価します。</span><span class="sxs-lookup"><span data-stu-id="ac779-125">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="ac779-126">ときに、`True``elseifcondition`が見つかると、すぐに、関連付けられている次のステートメント`ElseIf`実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac779-126">When a `True``elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="ac779-127">ない場合は`elseifcondition`に評価`True`がある場合、またはなし`ElseIf`ステートメント、次のステートメント`Else`実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac779-127">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="ac779-128">次のステートメントを実行した後`Then`、 `ElseIf`、または`Else`、ステートメントに次の実行が続行`End If`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-128">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="ac779-129">`ElseIf`と`Else`句は、どちらも省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ac779-129">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="ac779-130">多くとして持つことができます`ElseIf`で必要なときと句、`If`しています.`Then`...`Else`ステートメントがない`ElseIf`句の後に、`Else`句。</span><span class="sxs-lookup"><span data-stu-id="ac779-130">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="ac779-131">`If`...`Then`...`Else`ステートメントは互いに入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac779-131">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="ac779-132">複数行の構文では、`If`ステートメントは、最初の行で唯一のステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac779-132">In the multiple-line syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="ac779-133">`ElseIf`、 `Else`、および`End If`ステートメントの前の行ラベルにのみです。</span><span class="sxs-lookup"><span data-stu-id="ac779-133">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="ac779-134">`If`しています.`Then`...`Else`ブロックがで終了する必要があります、`End If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ac779-134">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="ac779-135">[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)をいくつかの値を持つ 1 つの式を評価する際に役に立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac779-135">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
## <a name="single-line-syntax"></a><span data-ttu-id="ac779-136">単一行の構文</span><span class="sxs-lookup"><span data-stu-id="ac779-136">Single-Line Syntax</span></span>  
 <span data-ttu-id="ac779-137">Short、単純なテストの単一行構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ac779-137">You can use the single-line syntax for short, simple tests.</span></span> <span data-ttu-id="ac779-138">ただし、複数行の構文詳細の構造と柔軟性を提供され、読み取り、保守、およびデバッグする方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="ac779-138">However, the multiple-line syntax provides more structure and flexibility and is usually easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="ac779-139">次のようにどのような`Then`キーワードが単一行、ステートメントがあるかどうかを調べて確認`If`です。</span><span class="sxs-lookup"><span data-stu-id="ac779-139">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="ac779-140">後にコメント以外の何かが表示された場合`Then`、同じ行には、ステートメントは単一行として扱われます`If`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ac779-140">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="ac779-141">場合`Then`が存在しない場合は、複数行の開始をする必要があります`If`しています.`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="ac779-141">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="ac779-142">単一行の構文では、複数のステートメントの結果として実行することが、`If`しています.`Then`意思決定します。</span><span class="sxs-lookup"><span data-stu-id="ac779-142">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="ac779-143">すべてのステートメントでは、同じ行にある必要があり、コロンで区切っています。</span><span class="sxs-lookup"><span data-stu-id="ac779-143">All statements must be on the same line and be separated by colons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac779-144">例</span><span class="sxs-lookup"><span data-stu-id="ac779-144">Example</span></span>  
 <span data-ttu-id="ac779-145">次の例の複数行の構文の使用方法を示しています、`If`しています.`Then`...`Else`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ac779-145">The following example illustrates the use of the multiple-line syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ac779-146">例</span><span class="sxs-lookup"><span data-stu-id="ac779-146">Example</span></span>  
 <span data-ttu-id="ac779-147">次の例を含む入れ子になった`If`しています.`Then`...`Else`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ac779-147">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="ac779-148">例</span><span class="sxs-lookup"><span data-stu-id="ac779-148">Example</span></span>  
 <span data-ttu-id="ac779-149">次の例では、単一行の構文の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="ac779-149">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ac779-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac779-150">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="ac779-151">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="ac779-151">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="ac779-152">Select...Case ステートメント</span><span class="sxs-lookup"><span data-stu-id="ac779-152">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="ac779-153">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="ac779-153">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="ac779-154">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="ac779-154">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="ac779-155">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="ac779-155">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="ac779-156">If 演算子</span><span class="sxs-lookup"><span data-stu-id="ac779-156">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
