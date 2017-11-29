---
title: "Visual Basic の論理演算子とビット処理演算子"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba48f722a11e93f82ae99aa407c3096a964e5ddd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="47e08-102">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="47e08-102">Logical and Bitwise Operators in Visual Basic</span></span>
<span data-ttu-id="47e08-103">論理演算子は、比較`Boolean`式と戻り値、`Boolean`結果。</span><span class="sxs-lookup"><span data-stu-id="47e08-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="47e08-104">`And`、 `Or`、 `AndAlso`、 `OrElse`、および`Xor`演算子は*バイナリ*中に、2 つのオペランドを受け取るため、`Not`演算子は*単項* 1 つのオペランドを受け取るためです。</span><span class="sxs-lookup"><span data-stu-id="47e08-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="47e08-105">整数値のビットごとの論理演算これらの演算子の一部も行えます。</span><span class="sxs-lookup"><span data-stu-id="47e08-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="47e08-106">単項論理演算子</span><span class="sxs-lookup"><span data-stu-id="47e08-106">Unary Logical Operator</span></span>  
 <span data-ttu-id="47e08-107">[演算子ではなく](../../../../visual-basic/language-reference/operators/not-operator.md)論理実行*否定*上、`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="47e08-107">The [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="47e08-108">これには、論理的に反対のオペランドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="47e08-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="47e08-109">式が評価された場合`True`、し`Not`を返します`False`以外の場合は、式に`False`、し、`Not`返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="47e08-110">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="47e08-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="47e08-111">二項論理演算子</span><span class="sxs-lookup"><span data-stu-id="47e08-111">Binary Logical Operators</span></span>  
 <span data-ttu-id="47e08-112">[And 演算子](../../../../visual-basic/language-reference/operators/and-operator.md)論理実行*組み合わせて*2 つの`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="47e08-112">The [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="47e08-113">場合に、両方の式が評価される`True`、し、`And`返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-113">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="47e08-114">少なくとも 1 つの式の評価された場合`False`、し`And`返します`False`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-114">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="47e08-115">[または演算子](../../../../visual-basic/language-reference/operators/or-operator.md)論理実行*和*または*包含*2 つの`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="47e08-115">The [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="47e08-116">いずれかの式が評価された場合`True`、または両方を評価するため`True`、し、`Or`返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-116">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="47e08-117">どちらの式に評価される場合`True`、`Or`返します`False`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-117">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="47e08-118">[Xor 演算子](../../../../visual-basic/language-reference/operators/xor-operator.md)論理実行*除外*2 つの`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="47e08-118">The [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="47e08-119">正確に 1 つの式が評価された場合`True`、両方ではなく、`Xor`返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-119">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="47e08-120">両方の式が評価される場合`True`に評価される両方または`False`、`Xor`返します`False`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-120">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="47e08-121">次の例を示しています、 `And`、 `Or`、および`Xor`演算子。</span><span class="sxs-lookup"><span data-stu-id="47e08-121">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="47e08-122">ショート サーキット論理操作</span><span class="sxs-lookup"><span data-stu-id="47e08-122">Short-Circuiting Logical Operations</span></span>  
 <span data-ttu-id="47e08-123">[AndAlso 演算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)とよく似ていますが、`And`演算子、2 つの論理積を実行するに`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="47e08-123">The [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="47e08-124">2 つの重要な違いは`AndAlso`の欠落を表す*ショート サーキット*動作します。</span><span class="sxs-lookup"><span data-stu-id="47e08-124">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="47e08-125">場合は最初の式で、`AndAlso`式に評価される`False`、最終結果を変更できないために、2 番目の式は評価されませんしと`AndAlso`を返します`False`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-125">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="47e08-126">同様に、 [OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)2 つの論理和の短絡`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="47e08-126">Similarly, the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="47e08-127">場合は最初の式で、`OrElse`式に評価される`True`、最終結果を変更できないために、2 番目の式は評価されませんしと`OrElse`を返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-127">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="47e08-128">ショート サーキットのトレードオフ</span><span class="sxs-lookup"><span data-stu-id="47e08-128">Short-Circuiting Trade-Offs</span></span>  
 <span data-ttu-id="47e08-129">ショート サーキット論理演算の結果を変更することはできません、式を評価されないので、パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="47e08-129">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="47e08-130">ただし、その式は、その他の操作を実行する場合は、これらの操作をスキップ ショート サーキットします。</span><span class="sxs-lookup"><span data-stu-id="47e08-130">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="47e08-131">たとえば、式への呼び出しが含まれている場合、`Function`プロシージャ、式がショート サーキットとに、追加のコードが含まれている場合に、プロシージャが呼び出されません、`Function`は実行されません。</span><span class="sxs-lookup"><span data-stu-id="47e08-131">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="47e08-132">そのため、この関数は、頻度が低い実行可能性があり、正しくテストいない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="47e08-132">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="47e08-133">プログラム ロジックのコードに依存、または、`Function`です。</span><span class="sxs-lookup"><span data-stu-id="47e08-133">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="47e08-134">次の例は、違いを示しています。 `And`、 `Or`、および対応するショート サーキットします。</span><span class="sxs-lookup"><span data-stu-id="47e08-134">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 <span data-ttu-id="47e08-135">上記の例では、ことに注意して内の重要なコード`checkIfValid()`呼び出しがショート サーキットの場合は実行されません。</span><span class="sxs-lookup"><span data-stu-id="47e08-135">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="47e08-136">最初の`If`ステートメントの呼び出し`checkIfValid()`にもかかわらず`12 > 45`返します`False`ので、`And`ショート サーキットはありません。</span><span class="sxs-lookup"><span data-stu-id="47e08-136">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="47e08-137">2 番目`If`ステートメントは呼び出しません`checkIfValid()`ので、ときに`12 > 45`を返します`False`、 `AndAlso` short-circuits 2 番目の式。</span><span class="sxs-lookup"><span data-stu-id="47e08-137">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="47e08-138">3 番目`If`ステートメント呼び出し`checkIfValid()`にもかかわらず`12 < 45`を返します`True`ので、`Or`ショート サーキットはありません。</span><span class="sxs-lookup"><span data-stu-id="47e08-138">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="47e08-139">4 番目`If`ステートメント呼び出されません`checkIfValid()`ため、ときに`12 < 45`返します`True`、 `OrElse` short-circuits 2 番目の式。</span><span class="sxs-lookup"><span data-stu-id="47e08-139">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="47e08-140">ビット処理演算</span><span class="sxs-lookup"><span data-stu-id="47e08-140">Bitwise Operations</span></span>  
 <span data-ttu-id="47e08-141">ビットごとの演算では、(基本 2) のバイナリ形式で 2 つの整数値を評価します。</span><span class="sxs-lookup"><span data-stu-id="47e08-141">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="47e08-142">対応する位置のビットを比較し、比較に基づいて値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="47e08-142">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="47e08-143">次の例を示しています、`And`演算子。</span><span class="sxs-lookup"><span data-stu-id="47e08-143">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 <span data-ttu-id="47e08-144">前の例の値を設定する`x`を 1 にします。</span><span class="sxs-lookup"><span data-stu-id="47e08-144">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="47e08-145">これは、次の理由で発生します。</span><span class="sxs-lookup"><span data-stu-id="47e08-145">This happens for the following reasons:</span></span>  
  
-   <span data-ttu-id="47e08-146">値はバイナリとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="47e08-146">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="47e08-147">バイナリ形式の 3 011 を =</span><span class="sxs-lookup"><span data-stu-id="47e08-147">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="47e08-148">バイナリ形式の 5 101 を =</span><span class="sxs-lookup"><span data-stu-id="47e08-148">5 in binary form = 101</span></span>  
  
-   <span data-ttu-id="47e08-149">`And`演算子は、一度に 1 つのバイナリ位置 (ビット) のバイナリ表現を比較します。</span><span class="sxs-lookup"><span data-stu-id="47e08-149">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="47e08-150">指定した位置にある両方のビットが 1 の場合は、1 は、結果の位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="47e08-150">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="47e08-151">どちらかのビットが 0 の場合、0 は、結果の位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="47e08-151">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="47e08-152">前の例ではこの êaƒnƒ。</span><span class="sxs-lookup"><span data-stu-id="47e08-152">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="47e08-153">011 (バイナリ形式で 3)</span><span class="sxs-lookup"><span data-stu-id="47e08-153">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="47e08-154">101 (バイナリ形式の 5)</span><span class="sxs-lookup"><span data-stu-id="47e08-154">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="47e08-155">001 (バイナリ形式の結果)</span><span class="sxs-lookup"><span data-stu-id="47e08-155">001 (The result, in binary form)</span></span>  
  
-   <span data-ttu-id="47e08-156">結果は、10 進数として扱われます。</span><span class="sxs-lookup"><span data-stu-id="47e08-156">The result is treated as decimal.</span></span> <span data-ttu-id="47e08-157">001 値は 1、バイナリ形式をこのため`x`= 1 です。</span><span class="sxs-lookup"><span data-stu-id="47e08-157">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="47e08-158">ビットごと`Or`操作似ていますが、ビットごとの一方または両方が 1 の場合、結果のビットを 1 が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="47e08-158">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="47e08-159">`Xor`1 つの (両方ではなく)、比較するビットだけが 1 の場合は、1、結果のビットに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="47e08-159">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="47e08-160">`Not`1 つのオペランドを受け取るし、符号ビットを含むすべてのビットを反転結果にその値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="47e08-160">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="47e08-161">これは、正の数値を署名のことを意味`Not`常に負の値を返しますと負の値、`Not`常に正の値または 0 の値を返します。</span><span class="sxs-lookup"><span data-stu-id="47e08-161">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="47e08-162">`AndAlso`と`OrElse`演算子はビットごとの演算をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="47e08-162">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47e08-163">ビットごとの演算は、整数型でのみ実行できます。</span><span class="sxs-lookup"><span data-stu-id="47e08-163">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="47e08-164">ビットごとの演算は続行する前に、浮動小数点値を整数型に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47e08-164">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e08-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="47e08-165">See Also</span></span>  
 [<span data-ttu-id="47e08-166">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47e08-166">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="47e08-167">ブール式</span><span class="sxs-lookup"><span data-stu-id="47e08-167">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="47e08-168">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="47e08-168">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="47e08-169">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="47e08-169">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="47e08-170">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="47e08-170">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="47e08-171">演算子の効率のよい組み合わせ</span><span class="sxs-lookup"><span data-stu-id="47e08-171">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
