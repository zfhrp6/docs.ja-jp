---
title: "If 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c553da5abf5453ba881671806b976125355c1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="42a94-102">If 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42a94-102">If Operator (Visual Basic)</span></span>
<span data-ttu-id="42a94-103">ショート サーキット評価を条件に応じて 2 つの値を返しますを使用します。</span><span class="sxs-lookup"><span data-stu-id="42a94-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="42a94-104">`If`演算子は、3 つの引数、または 2 つの引数を指定して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="42a94-104">The `If` operator can be called with three arguments or with two arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42a94-105">構文</span><span class="sxs-lookup"><span data-stu-id="42a94-105">Syntax</span></span>  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="42a94-106">演算子は、3 つの引数で呼び出された場合</span><span class="sxs-lookup"><span data-stu-id="42a94-106">If Operator Called with Three Arguments</span></span>  
 <span data-ttu-id="42a94-107">ときに`If`が呼び出された 3 つの引数を使用すると、最初の引数としてキャスト可能な値に評価する必要があります、`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="42a94-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="42a94-108">ある`Boolean`が評価され、返されるその他の 2 つの引数の値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="42a94-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="42a94-109">次のリストの適用される場合にのみ、`If`演算子が 3 つの引数を使用して呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="42a94-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="42a94-110">指定項目</span><span class="sxs-lookup"><span data-stu-id="42a94-110">Parts</span></span>  
  
|<span data-ttu-id="42a94-111">用語</span><span class="sxs-lookup"><span data-stu-id="42a94-111">Term</span></span>|<span data-ttu-id="42a94-112">定義</span><span class="sxs-lookup"><span data-stu-id="42a94-112">Definition</span></span>|  
|---|---|  
|`argument1`|<span data-ttu-id="42a94-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="42a94-113">Required.</span></span> <span data-ttu-id="42a94-114">`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="42a94-114">`Boolean`.</span></span> <span data-ttu-id="42a94-115">その他の引数を評価し、返すを決定します。</span><span class="sxs-lookup"><span data-stu-id="42a94-115">Determines which of the other arguments to evaluate and return.</span></span>|  
|`argument2`|<span data-ttu-id="42a94-116">必須です。</span><span class="sxs-lookup"><span data-stu-id="42a94-116">Required.</span></span> <span data-ttu-id="42a94-117">`Object`。</span><span class="sxs-lookup"><span data-stu-id="42a94-117">`Object`.</span></span> <span data-ttu-id="42a94-118">評価されると返される場合`argument1`に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="42a94-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|  
|`argument3`|<span data-ttu-id="42a94-119">必須です。</span><span class="sxs-lookup"><span data-stu-id="42a94-119">Required.</span></span> <span data-ttu-id="42a94-120">`Object`。</span><span class="sxs-lookup"><span data-stu-id="42a94-120">`Object`.</span></span> <span data-ttu-id="42a94-121">評価されると返される場合`argument1`に評価`False`場合`argument1`は、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="42a94-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|  
  
 <span data-ttu-id="42a94-122">`If`が 3 つの引数で呼び出される演算子の動作と同様に、`IIf`関数を使用する点を除いてショート サーキット評価します。</span><span class="sxs-lookup"><span data-stu-id="42a94-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="42a94-123">`IIf`関数評価は常に 3 つすべての引数の一方、`If`を 3 つの引数を持つ演算子が評価される 2 つのみです。</span><span class="sxs-lookup"><span data-stu-id="42a94-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="42a94-124">最初の`If`引数が評価され、結果としてキャスト、`Boolean`値、`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="42a94-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="42a94-125">値が場合`True`、`argument2`が評価され、その値が返されますが、`argument3`は評価されません。</span><span class="sxs-lookup"><span data-stu-id="42a94-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="42a94-126">場合の値、`Boolean`式が`False`、`argument3`が評価され、その値が返されますが、`argument2`は評価されません。</span><span class="sxs-lookup"><span data-stu-id="42a94-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="42a94-127">次の例では、使用する`If`3 つの引数を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="42a94-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 <span data-ttu-id="42a94-128">次の例は、の値を示しています。 ショート サーキット評価します。</span><span class="sxs-lookup"><span data-stu-id="42a94-128">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="42a94-129">例では、変数に分割する 2 つの試行を示しています。`number`変数によって`divisor`場合を除きます`divisor`は 0 です。</span><span class="sxs-lookup"><span data-stu-id="42a94-129">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="42a94-130">その場合は、0 を返す必要があるし、は行われません、実行時エラーになるため、除算を実行します。</span><span class="sxs-lookup"><span data-stu-id="42a94-130">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="42a94-131">`If`ショート サーキット評価の式の使用、2 番目または最初の引数の値に応じて、3 番目の引数のいずれかを評価します。</span><span class="sxs-lookup"><span data-stu-id="42a94-131">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="42a94-132">最初の引数が true の場合は、除数 0 ではないと 2 番目の引数を評価し、除算を実行しても安全です。</span><span class="sxs-lookup"><span data-stu-id="42a94-132">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="42a94-133">最初の引数が false の場合は、3 番目の引数のみが評価され、0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="42a94-133">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="42a94-134">そのため、除数が 0 の場合は行われません、除算とエラーは発生しませんを実行します。</span><span class="sxs-lookup"><span data-stu-id="42a94-134">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="42a94-135">ただし、ため`IIf`使用しないショート サーキット評価、最初の引数が false の場合も、2 番目の引数が評価されます。</span><span class="sxs-lookup"><span data-stu-id="42a94-135">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="42a94-136">これにより、実行時に 0 除算エラーです。</span><span class="sxs-lookup"><span data-stu-id="42a94-136">This causes a run-time divide-by-zero error.</span></span>  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="42a94-137">演算子が 2 つの引数で呼び出された場合</span><span class="sxs-lookup"><span data-stu-id="42a94-137">If Operator Called with Two Arguments</span></span>  
 <span data-ttu-id="42a94-138">1 番目の引数`If`を省略できます。</span><span class="sxs-lookup"><span data-stu-id="42a94-138">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="42a94-139">これにより、2 つの引数を使用して呼び出される演算子です。</span><span class="sxs-lookup"><span data-stu-id="42a94-139">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="42a94-140">次のリストの適用される場合にのみ、`If`演算子が 2 つの引数と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="42a94-140">The following list applies only when the `If` operator is called with two arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="42a94-141">指定項目</span><span class="sxs-lookup"><span data-stu-id="42a94-141">Parts</span></span>  
  
|<span data-ttu-id="42a94-142">用語</span><span class="sxs-lookup"><span data-stu-id="42a94-142">Term</span></span>|<span data-ttu-id="42a94-143">定義</span><span class="sxs-lookup"><span data-stu-id="42a94-143">Definition</span></span>|  
|---|---|  
|`argument2`|<span data-ttu-id="42a94-144">必須です。</span><span class="sxs-lookup"><span data-stu-id="42a94-144">Required.</span></span> <span data-ttu-id="42a94-145">`Object`。</span><span class="sxs-lookup"><span data-stu-id="42a94-145">`Object`.</span></span> <span data-ttu-id="42a94-146">参照または null 許容型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="42a94-146">Must be a reference or nullable type.</span></span> <span data-ttu-id="42a94-147">評価され、以外の値に評価された場合に返される`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="42a94-147">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|  
|`argument3`|<span data-ttu-id="42a94-148">必須です。</span><span class="sxs-lookup"><span data-stu-id="42a94-148">Required.</span></span> <span data-ttu-id="42a94-149">`Object`。</span><span class="sxs-lookup"><span data-stu-id="42a94-149">`Object`.</span></span> <span data-ttu-id="42a94-150">評価されると返される場合`argument2`に評価される`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="42a94-150">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|  
  
 <span data-ttu-id="42a94-151">ときに、`Boolean`引数を省略すると、最初の引数が参照または null 許容型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="42a94-151">When the `Boolean` argument is omitted, the first argument must be a reference or nullable type.</span></span> <span data-ttu-id="42a94-152">最初の引数が評価された場合`Nothing`、2 番目の引数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="42a94-152">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="42a94-153">それ以外の場合は、最初の引数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="42a94-153">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="42a94-154">次の例では、この評価のしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="42a94-154">The following example illustrates how this evaluation works.</span></span>  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="42a94-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="42a94-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [<span data-ttu-id="42a94-156">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="42a94-156">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="42a94-157">Nothing</span><span class="sxs-lookup"><span data-stu-id="42a94-157">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
