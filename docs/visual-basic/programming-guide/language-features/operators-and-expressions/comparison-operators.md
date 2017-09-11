---
title: "Visual Basic における比較演算子 |Microsoft ドキュメント"
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
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
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
ms.openlocfilehash: a958481fa04cb1a9abde69c5215dccd6dbbe4a14
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="113b4-102">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="113b4-102">Comparison Operators in Visual Basic</span></span>
<span data-ttu-id="113b4-103">比較演算子は&2; つの式を比較し、`Boolean`これらの値のリレーションシップを表す値。</span><span class="sxs-lookup"><span data-stu-id="113b4-103">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="113b4-104">数値、文字列を比較するための演算子、およびオブジェクトを比較する演算子を比較するための演算子があります。</span><span class="sxs-lookup"><span data-stu-id="113b4-104">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="113b4-105">ここでは、すべての&3; 種類の演算子を説明します。</span><span class="sxs-lookup"><span data-stu-id="113b4-105">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="113b4-106">数値の比較</span><span class="sxs-lookup"><span data-stu-id="113b4-106">Comparing Numeric Values</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="113b4-107">6 つの数値の比較演算子を使用して、数値を比較します。</span><span class="sxs-lookup"><span data-stu-id="113b4-107"> compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="113b4-108">各演算子は、オペランドとして数値に評価される&2; つの式を取得します。</span><span class="sxs-lookup"><span data-stu-id="113b4-108">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="113b4-109">次の表は、演算子の一覧し、それぞれの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="113b4-109">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="113b4-110">演算子</span><span class="sxs-lookup"><span data-stu-id="113b4-110">Operator</span></span>|<span data-ttu-id="113b4-111">テスト条件</span><span class="sxs-lookup"><span data-stu-id="113b4-111">Condition tested</span></span>|<span data-ttu-id="113b4-112">例</span><span class="sxs-lookup"><span data-stu-id="113b4-112">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="113b4-113">`=`(等値)</span><span class="sxs-lookup"><span data-stu-id="113b4-113">`=` (Equality)</span></span>|<span data-ttu-id="113b4-114">最初の式と等しい値を&2; 番目の値とは</span><span class="sxs-lookup"><span data-stu-id="113b4-114">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="113b4-115">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-115">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="113b4-116">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-116">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="113b4-117">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-117">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="113b4-118">`<>`(非等値)</span><span class="sxs-lookup"><span data-stu-id="113b4-118">`<>` (Inequality)</span></span>|<span data-ttu-id="113b4-119">値ではない最初の式の&2; つ目の値と等しいか。</span><span class="sxs-lookup"><span data-stu-id="113b4-119">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="113b4-120">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-120">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="113b4-121">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-121">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="113b4-122">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-122">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="113b4-123">`<`(より小さい)</span><span class="sxs-lookup"><span data-stu-id="113b4-123">`<` (Less than)</span></span>|<span data-ttu-id="113b4-124">最初の式の値未満、2 番目の値とは</span><span class="sxs-lookup"><span data-stu-id="113b4-124">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="113b4-125">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-125">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="113b4-126">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-126">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="113b4-127">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-127">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="113b4-128">`>`(より大きい)</span><span class="sxs-lookup"><span data-stu-id="113b4-128">`>` (Greater than)</span></span>|<span data-ttu-id="113b4-129">最初の式の値は、2 番目の値よりも大きいですか</span><span class="sxs-lookup"><span data-stu-id="113b4-129">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="113b4-130">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-130">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="113b4-131">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-131">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="113b4-132">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-132">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="113b4-133">`<=`(より小さいまたは等しい)</span><span class="sxs-lookup"><span data-stu-id="113b4-133">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="113b4-134">最初の式の値を&2; 番目の値以下ですか。</span><span class="sxs-lookup"><span data-stu-id="113b4-134">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="113b4-135">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-135">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="113b4-136">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-136">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="113b4-137">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-137">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="113b4-138">`>=`(より大きいまたは等しい)</span><span class="sxs-lookup"><span data-stu-id="113b4-138">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="113b4-139">最初の式の値は、2 番目の値以下でしょうか。</span><span class="sxs-lookup"><span data-stu-id="113b4-139">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="113b4-140">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="113b4-140">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="113b4-141">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-141">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="113b4-142">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="113b4-142">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="113b4-143">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="113b4-143">Comparing Strings</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="113b4-144">使用して文字列を比較し、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)だけでなく、数値比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="113b4-144"> compares strings using the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="113b4-145">`Like`演算子では、パターンを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="113b4-145">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="113b4-146">文字列は、比較、パターンと一致した場合、結果は`True`です。</span><span class="sxs-lookup"><span data-stu-id="113b4-146">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="113b4-147">それ以外の場合、結果は`False`です。</span><span class="sxs-lookup"><span data-stu-id="113b4-147">Otherwise, the result is `False`.</span></span> <span data-ttu-id="113b4-148">数値演算子で比較を使用する`String`値は次の例のように、並べ替え順序に基づいています。</span><span class="sxs-lookup"><span data-stu-id="113b4-148">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="113b4-149">前の例では、結果は`True`最初の文字列の最初の文字が&2; 番目の文字列の最初の文字の前になるためです。</span><span class="sxs-lookup"><span data-stu-id="113b4-149">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="113b4-150">最初の文字と等しい場合は、比較を両方の文字列では、次の文字を続行しにします。</span><span class="sxs-lookup"><span data-stu-id="113b4-150">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="113b4-151">次の例のように、等値演算子を使用して文字列の等価性をテストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="113b4-151">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="113b4-152">1 つの文字列が"aa"や"aaa"など、別のプレフィックスである場合より長い文字列は短いほうの文字列よりも大きくすると見なされます。</span><span class="sxs-lookup"><span data-stu-id="113b4-152">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="113b4-153">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="113b4-153">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="113b4-154">並べ替え順序が、バイナリの比較またはテキストの比較の設定に応じてに基づいて`Option Compare`します。</span><span class="sxs-lookup"><span data-stu-id="113b4-154">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="113b4-155">詳細については、次を参照してください。 [Option Compare ステートメント](../../../../visual-basic/language-reference/statements/option-compare-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="113b4-155">For more information see [Option Compare Statement](../../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="113b4-156">オブジェクトを比較します。</span><span class="sxs-lookup"><span data-stu-id="113b4-156">Comparing Objects</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="113b4-157">2 つの比較はオブジェクト参照変数と、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)と[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)します。</span><span class="sxs-lookup"><span data-stu-id="113b4-157"> compares two object reference variables with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="113b4-158">これらの演算子のいずれかを使用して、2 つの参照変数が同じオブジェクト インスタンスを参照している場合を判断します。</span><span class="sxs-lookup"><span data-stu-id="113b4-158">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="113b4-159">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="113b4-159">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="113b4-160">[!code-vb[VbVbalrOperators #&65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="113b4-160">[!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="113b4-161">前の例で`x Is y`に評価`True`、両方の変数が同じインスタンスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="113b4-161">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="113b4-162">次の例では、この結果を比較してください。</span><span class="sxs-lookup"><span data-stu-id="113b4-162">Contrast this result with the following example.</span></span>  
  
 <span data-ttu-id="113b4-163">[!code-vb[VbVbalrOperators #&66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="113b4-163">[!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="113b4-164">前の例で`x Is y`に評価`False`、その種類の異なるインスタンス変数を同じ型のオブジェクト、参照が表しているためです。</span><span class="sxs-lookup"><span data-stu-id="113b4-164">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="113b4-165">同じインスタンスを指していない&2; つのオブジェクトをテストするときに、`IsNot`演算子の文法的に不器用な組み合わせを回避できます。`Not`と`Is`です。</span><span class="sxs-lookup"><span data-stu-id="113b4-165">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="113b4-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="113b4-166">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="113b4-167">[!code-vb[VbVbalrOperators #&67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="113b4-167">[!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]</span></span>  
  
 <span data-ttu-id="113b4-168">前の例で`If a IsNot b`は`If Not a Is b`です。</span><span class="sxs-lookup"><span data-stu-id="113b4-168">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="113b4-169">オブジェクトの種類を比較します。</span><span class="sxs-lookup"><span data-stu-id="113b4-169">Comparing Object Type</span></span>  
 <span data-ttu-id="113b4-170">オブジェクトが特定の型にするかどうかをテストする、 `TypeOf`.`Is`式です。</span><span class="sxs-lookup"><span data-stu-id="113b4-170">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="113b4-171">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="113b4-171">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="113b4-172">`typename`インターフェイスの種類を指定し、 `TypeOf`.`Is`式を返します。`True`オブジェクトは、インターフェイス型を実装している場合。</span><span class="sxs-lookup"><span data-stu-id="113b4-172">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="113b4-173">`typename` 、式から返されるクラス型が`True`場合は、オブジェクトは、指定したクラスのまたは指定したクラスから派生したクラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="113b4-173">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="113b4-174">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="113b4-174">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="113b4-175">[!code-vb[VbVbalrOperators #&68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="113b4-175">[!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]</span></span>  
  
 <span data-ttu-id="113b4-176">前の例で、`TypeOf x Is Control`式に評価される`True`ための型`x`は`Button`から継承される`Control`します。</span><span class="sxs-lookup"><span data-stu-id="113b4-176">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="113b4-177">詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)します。</span><span class="sxs-lookup"><span data-stu-id="113b4-177">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113b4-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="113b4-178">See Also</span></span>  
 <span data-ttu-id="113b4-179">[値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="113b4-179">[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="113b4-180"> [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="113b4-180"> [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="113b4-181"> [演算子](../../../../visual-basic/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="113b4-181"> [Operators](../../../../visual-basic/language-reference/operators/index.md) </span></span>  
<span data-ttu-id="113b4-182"> [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="113b4-182"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="113b4-183"> [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="113b4-183"> [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span></span>  
<span data-ttu-id="113b4-184"> [Visual Basic での論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="113b4-184"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
