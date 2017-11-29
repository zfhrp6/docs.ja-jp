---
title: "Visual Basic における比較演算子"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8bf37ad30f410251f18aea6747734fc24d42cd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="638f8-102">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="638f8-103">比較演算子は 2 つの式を比較し、`Boolean`これらの値のリレーションシップを表す値です。</span><span class="sxs-lookup"><span data-stu-id="638f8-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="638f8-104">数値、文字列、比較演算子とオブジェクトの比較演算子を比較するための演算子があります。</span><span class="sxs-lookup"><span data-stu-id="638f8-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="638f8-105">すべての 3 種類の演算子は、ここで説明します。</span><span class="sxs-lookup"><span data-stu-id="638f8-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="638f8-106">数値の値を比較します。</span><span class="sxs-lookup"><span data-stu-id="638f8-106">Comparing Numeric Values</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="638f8-107">6 つの数値の比較演算子を使用して、数値を比較します。</span><span class="sxs-lookup"><span data-stu-id="638f8-107"> compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="638f8-108">各演算子はオペランドとして数値に評価される 2 つの式を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="638f8-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="638f8-109">次の表は、演算子の一覧し、それぞれの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="638f8-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="638f8-110">演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-110">Operator</span></span>|<span data-ttu-id="638f8-111">テスト条件</span><span class="sxs-lookup"><span data-stu-id="638f8-111">Condition tested</span></span>|<span data-ttu-id="638f8-112">例</span><span class="sxs-lookup"><span data-stu-id="638f8-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="638f8-113">`=`(等価)</span><span class="sxs-lookup"><span data-stu-id="638f8-113">`=` (Equality)</span></span>|<span data-ttu-id="638f8-114">最初の式等しいかどうかの値と 2 番目の値には</span><span class="sxs-lookup"><span data-stu-id="638f8-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="638f8-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="638f8-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="638f8-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="638f8-118">`<>`(非等値)</span><span class="sxs-lookup"><span data-stu-id="638f8-118">`<>` (Inequality)</span></span>|<span data-ttu-id="638f8-119">最初の式の値と等しくない 2 番目の値にしますか。</span><span class="sxs-lookup"><span data-stu-id="638f8-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="638f8-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="638f8-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="638f8-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="638f8-123">`<`(より小さい)</span><span class="sxs-lookup"><span data-stu-id="638f8-123">`<` (Less than)</span></span>|<span data-ttu-id="638f8-124">最初の式の値よりも小さいか、2 番目の値とは</span><span class="sxs-lookup"><span data-stu-id="638f8-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="638f8-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="638f8-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="638f8-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="638f8-128">`>`(より大きい)</span><span class="sxs-lookup"><span data-stu-id="638f8-128">`>` (Greater than)</span></span>|<span data-ttu-id="638f8-129">最初の式の値が 2 番目の値より大きいですか。</span><span class="sxs-lookup"><span data-stu-id="638f8-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="638f8-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="638f8-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="638f8-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="638f8-133">`<=`(以下を)</span><span class="sxs-lookup"><span data-stu-id="638f8-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="638f8-134">最初の式の値を 2 番目の値未満ですか。</span><span class="sxs-lookup"><span data-stu-id="638f8-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="638f8-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="638f8-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="638f8-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="638f8-138">`>=`(より大きいまたは等しい)</span><span class="sxs-lookup"><span data-stu-id="638f8-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="638f8-139">最初の式の値をより大きいか等しい 2 つ目の値には</span><span class="sxs-lookup"><span data-stu-id="638f8-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="638f8-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="638f8-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="638f8-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="638f8-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="638f8-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="638f8-143">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="638f8-143">Comparing Strings</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="638f8-144">使用して文字列を比較し、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)だけでなく、数値比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="638f8-144"> compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="638f8-145">`Like`演算子では、パターンを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="638f8-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="638f8-146">文字列を比較し、パターンと一致した場合、結果は`True`します。</span><span class="sxs-lookup"><span data-stu-id="638f8-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="638f8-147">それ以外の場合、結果は`False`します。</span><span class="sxs-lookup"><span data-stu-id="638f8-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="638f8-148">比較することは数値演算子`String`値が次の例のように、並べ替え順序に基づいています。</span><span class="sxs-lookup"><span data-stu-id="638f8-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="638f8-149">前の例で、結果は`True`のため、2 番目の文字列の最初の文字の前に、最初の文字列の最初の文字を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="638f8-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="638f8-150">最初の文字と等しい場合は、比較は、両方の文字列の次の文字は引き続きし、などです。</span><span class="sxs-lookup"><span data-stu-id="638f8-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="638f8-151">次の例のように、等値演算子を使用して文字列の等価性をテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="638f8-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="638f8-152">1 つの文字列が、別のプレフィックス"aa"と"aaa"などの場合、長い文字列が短い文字列より大きいと見なされます。</span><span class="sxs-lookup"><span data-stu-id="638f8-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="638f8-153">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="638f8-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="638f8-154">並べ替え順序が、バイナリの比較またはテキストの比較の設定に応じてに基づいて`Option Compare`です。</span><span class="sxs-lookup"><span data-stu-id="638f8-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="638f8-155">詳細については、次を参照してください。 [Option Compare ステートメント](../../../../visual-basic/language-reference/statements/option-compare-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="638f8-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="638f8-156">オブジェクトを比較します。</span><span class="sxs-lookup"><span data-stu-id="638f8-156">Comparing Objects</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="638f8-157">2 つの比較はオブジェクト参照変数と、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)と[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="638f8-157"> compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="638f8-158">これらの演算子のいずれかを使用して、2 つの参照変数が同じオブジェクト インスタンスを参照している場合を判断します。</span><span class="sxs-lookup"><span data-stu-id="638f8-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="638f8-159">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="638f8-159">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="638f8-160">この例では、`x Is y`に評価される`True`両方の変数が同じインスタンスを参照しているため、します。</span><span class="sxs-lookup"><span data-stu-id="638f8-160">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="638f8-161">次の例では、この結果を比較してください。</span><span class="sxs-lookup"><span data-stu-id="638f8-161">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 <span data-ttu-id="638f8-162">前の例で`x Is y`に評価される`False`その種類の異なるインスタンスを参照して、変数は、同じ種類のオブジェクトを参照して、ですが、します。</span><span class="sxs-lookup"><span data-stu-id="638f8-162">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="638f8-163">同一のインスタンスを指していない 2 つのオブジェクトをテストするときに、`IsNot`演算子の文法的に面倒な組み合わせを回避できます。`Not`と`Is`です。</span><span class="sxs-lookup"><span data-stu-id="638f8-163">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="638f8-164">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="638f8-164">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 <span data-ttu-id="638f8-165">この例では、`If a IsNot b`は等価`If Not a Is b`です。</span><span class="sxs-lookup"><span data-stu-id="638f8-165">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="638f8-166">オブジェクトの型の比較</span><span class="sxs-lookup"><span data-stu-id="638f8-166">Comparing Object Type</span></span>  
 <span data-ttu-id="638f8-167">オブジェクトが特定の型ではあるかどうかをテストすることができます、`TypeOf`しています.`Is`式。</span><span class="sxs-lookup"><span data-stu-id="638f8-167">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="638f8-168">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="638f8-168">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="638f8-169">ときに`typename`インターフェイスの型が指定、`TypeOf`しています.`Is`式を返します`True`オブジェクトには、インターフェイスの型が実装されている場合。</span><span class="sxs-lookup"><span data-stu-id="638f8-169">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="638f8-170">ときに`typename`式を返しますが、クラス型`True`場合は、オブジェクトは、指定したクラスのまたは指定したクラスから派生したクラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="638f8-170">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="638f8-171">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="638f8-171">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 <span data-ttu-id="638f8-172">前の例で、`TypeOf x Is Control`式に評価される`True`ための型`x`は`Button`から継承される`Control`です。</span><span class="sxs-lookup"><span data-stu-id="638f8-172">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="638f8-173">詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="638f8-173">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638f8-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="638f8-174">See Also</span></span>  
 [<span data-ttu-id="638f8-175">値の比較</span><span class="sxs-lookup"><span data-stu-id="638f8-175">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="638f8-176">比較演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-176">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="638f8-177">演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-177">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)  
 [<span data-ttu-id="638f8-178">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-178">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="638f8-179">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-179">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="638f8-180">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="638f8-180">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
