---
title: 比較演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 4e37f55b4c873c3dbea22a8edf0e5e2b58824720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604927"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="a9bd7-102">比較演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="a9bd7-103">Visual Basic で定義されている比較演算子を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-103">The following are the comparison operators defined in Visual Basic.</span></span>  
  
 <span data-ttu-id="a9bd7-104">`<` 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-104">`<` operator</span></span>  
  
 <span data-ttu-id="a9bd7-105">`<=` 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-105">`<=` operator</span></span>  
  
 <span data-ttu-id="a9bd7-106">`>` 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-106">`>` operator</span></span>  
  
 <span data-ttu-id="a9bd7-107">`>=` 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-107">`>=` operator</span></span>  
  
 <span data-ttu-id="a9bd7-108">`=` 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-108">`=` operator</span></span>  
  
 <span data-ttu-id="a9bd7-109">`<>` 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-109">`<>` operator</span></span>  
  
 [<span data-ttu-id="a9bd7-110">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [<span data-ttu-id="a9bd7-111">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [<span data-ttu-id="a9bd7-112">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 <span data-ttu-id="a9bd7-113">これらの演算子は、それらが等しいか、およびいない場合は、どのように異なるかどうかを決定する 2 つの式を比較します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="a9bd7-114">`Is`、 `IsNot`、および`Like`は別々 のヘルプ ページに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="a9bd7-115">比較演算子は、このページで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-115">The relational comparison operators are discussed in detail on this page.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bd7-116">構文</span><span class="sxs-lookup"><span data-stu-id="a9bd7-116">Syntax</span></span>  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="a9bd7-117">指定項目</span><span class="sxs-lookup"><span data-stu-id="a9bd7-117">Parts</span></span>  
 `result`  
 <span data-ttu-id="a9bd7-118">必須。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-118">Required.</span></span> <span data-ttu-id="a9bd7-119">A`Boolean`比較の結果を表す値です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-119">A `Boolean` value representing the result of the comparison.</span></span>  
  
 `expression`  
 <span data-ttu-id="a9bd7-120">必須。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-120">Required.</span></span> <span data-ttu-id="a9bd7-121">任意の式。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-121">Any expression.</span></span>  
  
 `comparisonoperator`  
 <span data-ttu-id="a9bd7-122">必須。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-122">Required.</span></span> <span data-ttu-id="a9bd7-123">任意の比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-123">Any relational comparison operator.</span></span>  
  
 <span data-ttu-id="a9bd7-124">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="a9bd7-124">`object1`, `object2`</span></span>  
 <span data-ttu-id="a9bd7-125">必須。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-125">Required.</span></span> <span data-ttu-id="a9bd7-126">いずれかは、オブジェクト名を参照します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-126">Any reference object names.</span></span>  
  
 `string`  
 <span data-ttu-id="a9bd7-127">必須。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-127">Required.</span></span> <span data-ttu-id="a9bd7-128">任意のブール型 (`String`) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-128">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="a9bd7-129">必須。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-129">Required.</span></span> <span data-ttu-id="a9bd7-130">どの`String`式または文字の範囲です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-130">Any `String` expression or range of characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9bd7-131">コメント</span><span class="sxs-lookup"><span data-stu-id="a9bd7-131">Remarks</span></span>  
 <span data-ttu-id="a9bd7-132">次の表は、比較演算子と判断する条件の一覧を含むかどうか`result`は`True`または`False`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-132">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>  
  
|<span data-ttu-id="a9bd7-133">演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-133">Operator</span></span>|<span data-ttu-id="a9bd7-134">`True` もし</span><span class="sxs-lookup"><span data-stu-id="a9bd7-134">`True` if</span></span>|<span data-ttu-id="a9bd7-135">`False` もし</span><span class="sxs-lookup"><span data-stu-id="a9bd7-135">`False` if</span></span>|  
|--------------|---------------|----------------|  
|<span data-ttu-id="a9bd7-136">`<` (より小さい)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-136">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|  
|<span data-ttu-id="a9bd7-137">`<=` (以下を)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-137">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|  
|<span data-ttu-id="a9bd7-138">`>` (より大きい)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-138">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|  
|<span data-ttu-id="a9bd7-139">`>=` (より大きいまたは等しい)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-139">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|  
|<span data-ttu-id="a9bd7-140">`=` (等しい)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-140">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|  
|<span data-ttu-id="a9bd7-141">`<>` (等しくない)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-141">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  <span data-ttu-id="a9bd7-142">[演算子を =](../../../visual-basic/language-reference/operators/assignment-operator.md)代入演算子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-142">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>  
  
 <span data-ttu-id="a9bd7-143">`Is` 、演算子、`IsNot`演算子、および`Like`演算子が前の表に、演算子とは異なる特定の比較機能があります。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-143">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>  
  
## <a name="comparing-numbers"></a><span data-ttu-id="a9bd7-144">数値を比較します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-144">Comparing Numbers</span></span>  
 <span data-ttu-id="a9bd7-145">型の式を比較するときに`Single`型のいずれかに`Double`、`Single`式に変換されます`Double`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-145">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="a9bd7-146">この動作は、Visual Basic 6 で動作するので、します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-146">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>  
  
 <span data-ttu-id="a9bd7-147">同様に、型の式を比較するときに`Decimal`型の式を`Single`または`Double`、`Decimal`式に変換されます`Single`または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-147">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="a9bd7-148">`Decimal`式、小数部の値より小さい 1E 28 は失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-148">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="a9bd7-149">このような小数部の値が失われるがいない場合、等しいと比較する 2 つの値があります。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-149">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="a9bd7-150">このため、注意してください等しいかどうかを使用する場合 (`=`) 2 つの浮動小数点変数を比較します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-150">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="a9bd7-151">2 つの数値の差の絶対値が許容差より小さいかどうかをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-151">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>  
  
### <a name="floating-point-imprecision"></a><span data-ttu-id="a9bd7-152">浮動小数点は誤差</span><span class="sxs-lookup"><span data-stu-id="a9bd7-152">Floating-point Imprecision</span></span>  
 <span data-ttu-id="a9bd7-153">浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに留意してください。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-153">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="a9bd7-154">これにより予期しない結果を比較値などの特定の操作から、 [Mod 演算子](../../../visual-basic/language-reference/operators/mod-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-154">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="a9bd7-155">詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-155">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="comparing-strings"></a><span data-ttu-id="a9bd7-156">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="a9bd7-156">Comparing Strings</span></span>  
 <span data-ttu-id="a9bd7-157">依存する、アルファベット順の並べ替え順序に基づいて、文字列式を評価する文字列を比較するときに、`Option Compare`設定します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-157">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>  
  
 <span data-ttu-id="a9bd7-158">`Option Compare Binary` ベース文字列の文字の内部バイナリ表現から派生した並べ替え順序で比較します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-158">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="a9bd7-159">並べ替え順序は、コード ページによって決まります。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-159">The sort order is determined by the code page.</span></span> <span data-ttu-id="a9bd7-160">次の例では、一般的なバイナリ並べ替え順序を示します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-160">The following example shows a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="a9bd7-161">`Option Compare Text` ベースでは、アプリケーションのロケールによって決まる、大文字と小文字、テキストの並べ替え順序での比較を文字列です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-161">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="a9bd7-162">設定すると`Option Compare Text`前の例での文字を並べ替えると、次のテキストの並べ替え順序が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-162">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a><span data-ttu-id="a9bd7-163">ロケール依存性</span><span class="sxs-lookup"><span data-stu-id="a9bd7-163">Locale Dependence</span></span>  
 <span data-ttu-id="a9bd7-164">設定すると`Option Compare Text`、文字列比較の結果が、アプリケーションが実行されている、ロケールに依存することができます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-164">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="a9bd7-165">2 つの文字は、等しいと評価別ではなく 1 つのロケールで比較可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-165">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="a9bd7-166">ログオンを許可するかどうかなど、重要な意思決定を行う、文字列の比較を使用している場合は、ロケールと小文字の区別にアラートがあります。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-166">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="a9bd7-167">いずれかの設定を検討してください`Option Compare Binary`または呼び出して、<xref:Microsoft.VisualBasic.Strings.StrComp%2A>ロケールにが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-167">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="a9bd7-168">リレーショナル比較演算子を省略したプログラミング</span><span class="sxs-lookup"><span data-stu-id="a9bd7-168">Typeless Programming with Relational Comparison Operators</span></span>  
 <span data-ttu-id="a9bd7-169">リレーショナル比較演算子の使用`Object`で式が許可されていません`Option Strict On`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-169">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="a9bd7-170">ときに`Option Strict`は`Off`、いずれかと`expression1`または`expression2`は、`Object`式では、実行時の型は、それらを比較する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-170">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="a9bd7-171">次の表は、式を比較する方法と、ランタイムのオペランドの型に応じて、比較の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-171">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>  
  
|<span data-ttu-id="a9bd7-172">オペランドの場合</span><span class="sxs-lookup"><span data-stu-id="a9bd7-172">If operands are</span></span>|<span data-ttu-id="a9bd7-173">比較では、</span><span class="sxs-lookup"><span data-stu-id="a9bd7-173">Comparison is</span></span>|  
|---------------------|-------------------|  
|<span data-ttu-id="a9bd7-174">両方とも `String`</span><span class="sxs-lookup"><span data-stu-id="a9bd7-174">Both `String`</span></span>|<span data-ttu-id="a9bd7-175">文字列の並べ替え特性に基づく比較を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-175">Sort comparison based on string sorting characteristics.</span></span>|  
|<span data-ttu-id="a9bd7-176">両方の数値</span><span class="sxs-lookup"><span data-stu-id="a9bd7-176">Both numeric</span></span>|<span data-ttu-id="a9bd7-177">オブジェクトに変換されます`Double`、数値比較します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-177">Objects converted to `Double`, numeric comparison.</span></span>|  
|<span data-ttu-id="a9bd7-178">1 つの数値型と 1 つ `String`</span><span class="sxs-lookup"><span data-stu-id="a9bd7-178">One numeric and one `String`</span></span>|<span data-ttu-id="a9bd7-179">`String`に変換されますが、`Double`数値比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-179">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="a9bd7-180">場合、`String`に変換できない`Double`、<xref:System.InvalidCastException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-180">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|  
|<span data-ttu-id="a9bd7-181">一方または両方が以外の参照型です。 `String`</span><span class="sxs-lookup"><span data-stu-id="a9bd7-181">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="a9bd7-182"><xref:System.InvalidCastException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-182">An <xref:System.InvalidCastException> is thrown.</span></span>|  
  
 <span data-ttu-id="a9bd7-183">数値の比較が扱う`Nothing`0 とします。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-183">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="a9bd7-184">文字列比較扱う`Nothing`として`""`(空の文字列)。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-184">String comparisons treat `Nothing` as `""` (an empty string).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a9bd7-185">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="a9bd7-185">Overloading</span></span>  
 <span data-ttu-id="a9bd7-186">比較演算子 (`<`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-186">The relational comparison operators (`<`.</span></span> <span data-ttu-id="a9bd7-187">`<=`、 `>`、 `>=`、 `=`、 `<>`) を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体できます動作を再定義オペランドは、そのクラスまたは構造体の型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-187">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a9bd7-188">コードは、このようなクラスまたは構造体で、これらの演算子のいずれかを使用している場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-188">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="a9bd7-189">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-189">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
 <span data-ttu-id="a9bd7-190">注意して、[演算子を =](../../../visual-basic/language-reference/operators/assignment-operator.md)比較演算子としてのみ、代入演算子としてではなく、オーバー ロードされたを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-190">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9bd7-191">例</span><span class="sxs-lookup"><span data-stu-id="a9bd7-191">Example</span></span>  
 <span data-ttu-id="a9bd7-192">次の例では、式の比較に使用するは、リレーショナル比較演算子のさまざまな使用を示します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-192">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="a9bd7-193">リレーショナル比較演算子を返す、`Boolean`を指定した式を評価するかどうかを表す結果`True`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-193">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="a9bd7-194">適用すると、`>`と`<`文字列への演算子、比較を使用して、通常のアルファベット順の文字列の。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-194">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="a9bd7-195">この順序は、ロケールの設定に依存できます。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-195">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="a9bd7-196">かどうか、並べ替えが大文字かによって異なります、 [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)設定します。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-196">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 <span data-ttu-id="a9bd7-197">前の例では、最初に比較を返します`False`し、残りの比較を返します`True`です。</span><span class="sxs-lookup"><span data-stu-id="a9bd7-197">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bd7-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9bd7-198">See Also</span></span>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="a9bd7-199">= 演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-199">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="a9bd7-200">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="a9bd7-200">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="a9bd7-201">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="a9bd7-201">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="a9bd7-202">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="a9bd7-202">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="a9bd7-203">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="a9bd7-203">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
