---
title: + 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: ccf79c700cf852c0febb9c3f3464cbacdd39296e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4417b-102">+ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4417b-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="4417b-103">2 つの数値を加算または数値式の正の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4417b-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="4417b-104">2 つの文字列式を連結するも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4417b-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4417b-105">構文</span><span class="sxs-lookup"><span data-stu-id="4417b-105">Syntax</span></span>  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="4417b-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="4417b-106">Parts</span></span>  
  
|<span data-ttu-id="4417b-107">用語</span><span class="sxs-lookup"><span data-stu-id="4417b-107">Term</span></span>|<span data-ttu-id="4417b-108">定義</span><span class="sxs-lookup"><span data-stu-id="4417b-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="4417b-109">必須。</span><span class="sxs-lookup"><span data-stu-id="4417b-109">Required.</span></span> <span data-ttu-id="4417b-110">任意の数値または文字列式です。</span><span class="sxs-lookup"><span data-stu-id="4417b-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="4417b-111">いない限り、必須、`+`演算子が負の値を計算します。</span><span class="sxs-lookup"><span data-stu-id="4417b-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="4417b-112">任意の数値または文字列式です。</span><span class="sxs-lookup"><span data-stu-id="4417b-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="4417b-113">結果</span><span class="sxs-lookup"><span data-stu-id="4417b-113">Result</span></span>  
 <span data-ttu-id="4417b-114">場合`expression1`と`expression2`が両方とも数値、算術、合計になります。</span><span class="sxs-lookup"><span data-stu-id="4417b-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="4417b-115">場合`expression2`失われている、`+`演算子は、*単項*恒等演算子式の値は変わりません。</span><span class="sxs-lookup"><span data-stu-id="4417b-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="4417b-116">この意味で、操作ではのサインインを維持した`expression1`ので、結果は負の値が、場合`expression1`が負の値。</span><span class="sxs-lookup"><span data-stu-id="4417b-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="4417b-117">場合`expression1`と`expression2`、両方の文字列は、結果は、それらの値を連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="4417b-118">場合`expression1`と`expression2`が実行されるアクションが、型、内容、およびの設定に依存、混合型の[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="4417b-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="4417b-119">詳細については、「解説」表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4417b-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="4417b-120">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="4417b-120">Supported Types</span></span>  
 <span data-ttu-id="4417b-121">符号なしと浮動小数点型を含むすべての数値型と`Decimal`、および`String`です。</span><span class="sxs-lookup"><span data-stu-id="4417b-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4417b-122">コメント</span><span class="sxs-lookup"><span data-stu-id="4417b-122">Remarks</span></span>  
 <span data-ttu-id="4417b-123">一般に、`+`可能であれば、算術加算を実行し、両方の式が文字列が場合にのみを連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="4417b-124">どちらの式の場合、 `Object`、Visual Basic は、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="4417b-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="4417b-125">式のデータ型</span><span class="sxs-lookup"><span data-stu-id="4417b-125">Data types of expressions</span></span>|<span data-ttu-id="4417b-126">コンパイラによる処理</span><span class="sxs-lookup"><span data-stu-id="4417b-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="4417b-127">両方の式が数値データ型 (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、または`Double`)</span><span class="sxs-lookup"><span data-stu-id="4417b-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="4417b-128">追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-128">Add.</span></span> <span data-ttu-id="4417b-129">結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="4417b-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="4417b-130">「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="4417b-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="4417b-131">型の両方の式は、します。 `String`</span><span class="sxs-lookup"><span data-stu-id="4417b-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="4417b-132">連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-132">Concatenate.</span></span>|  
|<span data-ttu-id="4417b-133">1 つの式は数値データ型で、もう一方の文字列</span><span class="sxs-lookup"><span data-stu-id="4417b-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="4417b-134">場合`Option Strict`は`On`、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="4417b-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="4417b-135">場合`Option Strict`は`Off`、暗黙的に変換、`String`に`Double`を追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="4417b-136">場合、`String`に変換できない`Double`、スロー、<xref:System.InvalidCastException>例外。</span><span class="sxs-lookup"><span data-stu-id="4417b-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="4417b-137">1 つの式が数値データ型では、もう一方は[何も行われません](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="4417b-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="4417b-138">追加すると`Nothing`値 0 にします。</span><span class="sxs-lookup"><span data-stu-id="4417b-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="4417b-139">1 つの式は、文字列であり、もう一方は `Nothing`</span><span class="sxs-lookup"><span data-stu-id="4417b-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="4417b-140">連結`Nothing`として値を持つ""です。</span><span class="sxs-lookup"><span data-stu-id="4417b-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="4417b-141">1 つの式がある場合、`Object`式では、Visual Basic は次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="4417b-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="4417b-142">式のデータ型</span><span class="sxs-lookup"><span data-stu-id="4417b-142">Data types of expressions</span></span>|<span data-ttu-id="4417b-143">コンパイラによる処理</span><span class="sxs-lookup"><span data-stu-id="4417b-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="4417b-144">`Object` 式は数値の値を保持し、もう一方の数値データ型</span><span class="sxs-lookup"><span data-stu-id="4417b-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="4417b-145">場合`Option Strict`は`On`、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="4417b-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="4417b-146">場合`Option Strict`は`Off`、しを追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="4417b-147">`Object` 式は数値の値を保持し、もう一方の型の `String`</span><span class="sxs-lookup"><span data-stu-id="4417b-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="4417b-148">場合`Option Strict`は`On`、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="4417b-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="4417b-149">場合`Option Strict`は`Off`、暗黙的に変換、`String`に`Double`を追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="4417b-150">場合、`String`に変換できない`Double`、スロー、<xref:System.InvalidCastException>例外。</span><span class="sxs-lookup"><span data-stu-id="4417b-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="4417b-151">`Object` 式が文字列を保持し、もう一方の数値データ型</span><span class="sxs-lookup"><span data-stu-id="4417b-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="4417b-152">場合`Option Strict`は`On`、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="4417b-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="4417b-153">場合`Option Strict`は`Off`、文字列を暗黙的に変換`Object`に`Double`を追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="4417b-154">場合、文字列`Object`に変換できません`Double`、スロー、<xref:System.InvalidCastException>例外。</span><span class="sxs-lookup"><span data-stu-id="4417b-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="4417b-155">`Object` 式が文字列を保持し、もう一方の型の `String`</span><span class="sxs-lookup"><span data-stu-id="4417b-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="4417b-156">場合`Option Strict`は`On`、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="4417b-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="4417b-157">場合`Option Strict`は`Off`、暗黙的に変換`Object`に`String`連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="4417b-158">両方の式が場合`Object`式、Visual Basic は、次のアクション (`Option Strict Off`のみ)。</span><span class="sxs-lookup"><span data-stu-id="4417b-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="4417b-159">式のデータ型</span><span class="sxs-lookup"><span data-stu-id="4417b-159">Data types of expressions</span></span>|<span data-ttu-id="4417b-160">コンパイラによる処理</span><span class="sxs-lookup"><span data-stu-id="4417b-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="4417b-161">両方`Object`式は数値を保持</span><span class="sxs-lookup"><span data-stu-id="4417b-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="4417b-162">追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-162">Add.</span></span>|  
|<span data-ttu-id="4417b-163">両方`Object`型の式は、 `String`</span><span class="sxs-lookup"><span data-stu-id="4417b-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="4417b-164">連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-164">Concatenate.</span></span>|  
|<span data-ttu-id="4417b-165">1 つ`Object`式は数値の値を保持し、文字列を保持して、他の</span><span class="sxs-lookup"><span data-stu-id="4417b-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="4417b-166">文字列に暗黙的に変換`Object`に`Double`を追加します。</span><span class="sxs-lookup"><span data-stu-id="4417b-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="4417b-167">場合、文字列`Object`値を数値に変換することはできませんし、スロー、<xref:System.InvalidCastException>例外。</span><span class="sxs-lookup"><span data-stu-id="4417b-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="4417b-168">いずれか`Object`式に評価される[何も](../../../visual-basic/language-reference/nothing.md)または<xref:System.DBNull>、`+`演算子として扱われます、`String`値は""です。</span><span class="sxs-lookup"><span data-stu-id="4417b-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4417b-169">使用すると、`+`演算子ができないことがありますを追加または文字列の連結が発生するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="4417b-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="4417b-170">使用して、`&`演算子の連結のあいまいさを排除し、自己文書化コードを提供します。</span><span class="sxs-lookup"><span data-stu-id="4417b-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4417b-171">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="4417b-171">Overloading</span></span>  
 <span data-ttu-id="4417b-172">`+`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="4417b-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4417b-173">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="4417b-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4417b-174">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="4417b-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4417b-175">例</span><span class="sxs-lookup"><span data-stu-id="4417b-175">Example</span></span>  
 <span data-ttu-id="4417b-176">次の例では、`+`番号を追加する演算子です。</span><span class="sxs-lookup"><span data-stu-id="4417b-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="4417b-177">オペランドが両方の数値の場合は、Visual Basic は、算術演算の結果を計算します。</span><span class="sxs-lookup"><span data-stu-id="4417b-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="4417b-178">算術演算の結果では、2 つのオペランドの合計を表します。</span><span class="sxs-lookup"><span data-stu-id="4417b-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 <span data-ttu-id="4417b-179">使用することも、`+`文字列を連結する演算子です。</span><span class="sxs-lookup"><span data-stu-id="4417b-179">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="4417b-180">オペランドが両方とも文字列である場合は、Visual Basic では、それらを連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-180">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="4417b-181">文字列連結の結果では、他の後に、2 つのオペランドの内容から成る 1 つの文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="4417b-181">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="4417b-182">混合型のオペランドがある場合、結果の設定によって異なります、 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="4417b-182">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="4417b-183">次の例は、結果を示しています。 ときに`Option Strict`は`On`します。</span><span class="sxs-lookup"><span data-stu-id="4417b-183">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 <span data-ttu-id="4417b-184">次の例は、結果を示しています。 ときに`Option Strict`は`Off`します。</span><span class="sxs-lookup"><span data-stu-id="4417b-184">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 <span data-ttu-id="4417b-185">あいまいさをなくすため、使用する必要があります、`&`演算子の代わりに`+`連結します。</span><span class="sxs-lookup"><span data-stu-id="4417b-185">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4417b-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="4417b-186">See Also</span></span>  
 [<span data-ttu-id="4417b-187">& 演算子</span><span class="sxs-lookup"><span data-stu-id="4417b-187">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="4417b-188">連結演算子</span><span class="sxs-lookup"><span data-stu-id="4417b-188">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="4417b-189">算術演算子</span><span class="sxs-lookup"><span data-stu-id="4417b-189">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="4417b-190">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="4417b-190">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="4417b-191">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="4417b-191">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="4417b-192">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="4417b-192">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="4417b-193">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="4417b-193">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
