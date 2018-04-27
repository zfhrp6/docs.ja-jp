---
title: Visual Basic における算術演算子
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cef1e3610d885a0f3a2bae718641f7b8ca1062dc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="arithmetic-operators-in-visual-basic"></a><span data-ttu-id="449ef-102">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="449ef-102">Arithmetic Operators in Visual Basic</span></span>
<span data-ttu-id="449ef-103">算術演算子は、多くのリテラル、変数、その他の式、関数とプロパティの呼び出し、および定数で表される数値の計算を含む一般的な算術演算の実行に使用されます。</span><span class="sxs-lookup"><span data-stu-id="449ef-103">Arithmetic operators are used to perform many of the familiar arithmetic operations that involve the calculation of numeric values represented by literals, variables, other expressions, function and property calls, and constants.</span></span> <span data-ttu-id="449ef-104">オペランドのビットごとのレベルで動作し、ビット パターンを左または右にシフトするビット シフト演算子は、算術演算子を含む分類もします。</span><span class="sxs-lookup"><span data-stu-id="449ef-104">Also classified with arithmetic operators are the bit-shift operators, which act at the level of the individual bits of the operands and shift their bit patterns to the left or right.</span></span>  
  
## <a name="arithmetic-operations"></a><span data-ttu-id="449ef-105">算術演算</span><span class="sxs-lookup"><span data-stu-id="449ef-105">Arithmetic Operations</span></span>  
 <span data-ttu-id="449ef-106">と共に式の中で 2 つの値を追加することができます、 [+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)、または減算を別の 1 つ、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)次の例で示すように、します。</span><span class="sxs-lookup"><span data-stu-id="449ef-106">You can add two values in an expression together with the [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md), or subtract one from another with the [- Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 <span data-ttu-id="449ef-107">否定にも使用されます、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)が、1 つだけのオペランドで次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="449ef-107">Negation also uses the [- Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), but with only one operand, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 <span data-ttu-id="449ef-108">乗算と除算の使用、 [\* 演算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)と[/演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)、それぞれに、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="449ef-108">Multiplication and division use the [\* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) and [/ Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectively, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 <span data-ttu-id="449ef-109">指数演算を使用して、 [^ 演算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="449ef-109">Exponentiation uses the [^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 <span data-ttu-id="449ef-110">整数の除算を使用して実行、 [\ 演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="449ef-110">Integer division is carried out using the [\ Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span> <span data-ttu-id="449ef-111">整数除算の商を返します、つまり、回数を表す整数除数できます除算小数部分を考慮せず被除数をします。</span><span class="sxs-lookup"><span data-stu-id="449ef-111">Integer division returns the quotient, that is, the integer that represents the number of times the divisor can divide into the dividend without consideration of any remainder.</span></span> <span data-ttu-id="449ef-112">除数と被除数の両方が整数型にする必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、および`ULong`) この演算子。</span><span class="sxs-lookup"><span data-stu-id="449ef-112">Both the divisor and the dividend must be integral types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, and `ULong`) for this operator.</span></span> <span data-ttu-id="449ef-113">他のすべての種類は、最初、整数型に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ef-113">All other types must be converted to an integral type first.</span></span> <span data-ttu-id="449ef-114">次の例では、整数の除算を示します。</span><span class="sxs-lookup"><span data-stu-id="449ef-114">The following example demonstrates integer division.</span></span>  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 <span data-ttu-id="449ef-115">使用して、剰余演算が実行される、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="449ef-115">Modulus arithmetic is performed using the [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="449ef-116">この演算子は、整数回数、被除数を除数で割った剰余を返します。</span><span class="sxs-lookup"><span data-stu-id="449ef-116">This operator returns the remainder after dividing the divisor into the dividend an integral number of times.</span></span> <span data-ttu-id="449ef-117">除数と被除数の両方が整数型の場合、返される値は整数です。</span><span class="sxs-lookup"><span data-stu-id="449ef-117">If both divisor and dividend are integral types, the returned value is integral.</span></span> <span data-ttu-id="449ef-118">除数と被除数が浮動小数点型の場合、返される値は浮動小数点もです。</span><span class="sxs-lookup"><span data-stu-id="449ef-118">If divisor and dividend are floating-point types, the returned value is also floating-point.</span></span> <span data-ttu-id="449ef-119">次の例では、この動作を示します。</span><span class="sxs-lookup"><span data-stu-id="449ef-119">The following example demonstrates this behavior.</span></span>  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a><span data-ttu-id="449ef-120">0 による除算</span><span class="sxs-lookup"><span data-stu-id="449ef-120">Attempted Division by Zero</span></span>  
 <span data-ttu-id="449ef-121">0 による除算では、関連するデータ型に応じて異なる結果があります。</span><span class="sxs-lookup"><span data-stu-id="449ef-121">Division by zero has different results depending on the data types involved.</span></span> <span data-ttu-id="449ef-122">整数の区分で (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`) では、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]スロー、<xref:System.DivideByZeroException>例外。</span><span class="sxs-lookup"><span data-stu-id="449ef-122">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="449ef-123">除算の操作、`Decimal`または`Single`データ型、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]もスロー、<xref:System.DivideByZeroException>例外。</span><span class="sxs-lookup"><span data-stu-id="449ef-123">In division operations on the `Decimal` or `Single` data type, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] also throws a <xref:System.DivideByZeroException> exception.</span></span>  
  
 <span data-ttu-id="449ef-124">関係する浮動小数点の区分で、`Double`データ型、例外がスローされないと、結果は、クラスのメンバーを表す<xref:System.Double.NaN>、 <xref:System.Double.PositiveInfinity>、または<xref:System.Double.NegativeInfinity>被除数に応じて、します。</span><span class="sxs-lookup"><span data-stu-id="449ef-124">In floating-point divisions involving the `Double` data type, no exception is thrown, and the result is the class member representing <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, or <xref:System.Double.NegativeInfinity>, depending on the dividend.</span></span> <span data-ttu-id="449ef-125">次の表に、さまざまな除算の結果、 `Double` 0 での値。</span><span class="sxs-lookup"><span data-stu-id="449ef-125">The following table summarizes the various results of attempting to divide a `Double` value by zero.</span></span>  
  
|<span data-ttu-id="449ef-126">被除数のデータ型</span><span class="sxs-lookup"><span data-stu-id="449ef-126">Dividend data type</span></span>|<span data-ttu-id="449ef-127">除数のデータ型</span><span class="sxs-lookup"><span data-stu-id="449ef-127">Divisor data type</span></span>|<span data-ttu-id="449ef-128">被除数の値</span><span class="sxs-lookup"><span data-stu-id="449ef-128">Dividend value</span></span>|<span data-ttu-id="449ef-129">結果</span><span class="sxs-lookup"><span data-stu-id="449ef-129">Result</span></span>|  
|---|---|---|---|  
|`Double`|`Double`|<span data-ttu-id="449ef-130">0</span><span class="sxs-lookup"><span data-stu-id="449ef-130">0</span></span>|<span data-ttu-id="449ef-131"><xref:System.Double.NaN> (非数学的に定義されている数)</span><span class="sxs-lookup"><span data-stu-id="449ef-131"><xref:System.Double.NaN> (not a mathematically defined number)</span></span>|  
|`Double`|`Double`|<span data-ttu-id="449ef-132">> 0</span><span class="sxs-lookup"><span data-stu-id="449ef-132">> 0</span></span>|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|<span data-ttu-id="449ef-133">\< 0</span><span class="sxs-lookup"><span data-stu-id="449ef-133">\< 0</span></span>|<xref:System.Double.NegativeInfinity>|  
  
 <span data-ttu-id="449ef-134">キャッチする場合、<xref:System.DivideByZeroException>例外、それを処理するためのメンバーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="449ef-134">When you catch a <xref:System.DivideByZeroException> exception, you can use its members to help you handle it.</span></span> <span data-ttu-id="449ef-135">たとえば、<xref:System.Exception.Message%2A>プロパティは、例外のメッセージ テキストを保持します。</span><span class="sxs-lookup"><span data-stu-id="449ef-135">For example, the <xref:System.Exception.Message%2A> property holds the message text for the exception.</span></span> <span data-ttu-id="449ef-136">詳しくは、「[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="449ef-136">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="bit-shift-operations"></a><span data-ttu-id="449ef-137">ビット シフト演算</span><span class="sxs-lookup"><span data-stu-id="449ef-137">Bit-Shift Operations</span></span>  
 <span data-ttu-id="449ef-138">ビット シフト操作は、ビット パターンに対して算術、シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="449ef-138">A bit-shift operation performs an arithmetic shift on a bit pattern.</span></span> <span data-ttu-id="449ef-139">パターンは、左側のオペランドで含まれているし、右側のオペランドがパターンをシフトする位置の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="449ef-139">The pattern is contained in the operand on the left, while the operand on the right specifies the number of positions to shift the pattern.</span></span> <span data-ttu-id="449ef-140">右側に、パターンを移すことができます、 [>> 演算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)または左側に、 [<< 演算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="449ef-140">You can shift the pattern to the right with the [>> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) or to the left with the [<< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md).</span></span>  
  
 <span data-ttu-id="449ef-141">パターンのオペランドのデータ型でなければなりません`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`です。</span><span class="sxs-lookup"><span data-stu-id="449ef-141">The data type of the pattern operand must be `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`.</span></span> <span data-ttu-id="449ef-142">Shift キーを押し量オペランドのデータ型である必要があります`Integer`に拡大変換する必要がありますまたは`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="449ef-142">The data type of the shift amount operand must be `Integer` or must widen to `Integer`.</span></span>  
  
 <span data-ttu-id="449ef-143">算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。</span><span class="sxs-lookup"><span data-stu-id="449ef-143">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="449ef-144">シフトによって空いたビット位置は、次のように設定されます。</span><span class="sxs-lookup"><span data-stu-id="449ef-144">The bit positions vacated by a shift are set as follows:</span></span>  
  
-   <span data-ttu-id="449ef-145">算術左シフトの場合は 0</span><span class="sxs-lookup"><span data-stu-id="449ef-145">0 for an arithmetic left shift</span></span>  
  
-   <span data-ttu-id="449ef-146">正の数の算術右シフトの場合は 0</span><span class="sxs-lookup"><span data-stu-id="449ef-146">0 for an arithmetic right shift of a positive number</span></span>  
  
-   <span data-ttu-id="449ef-147">署名されていないデータ型の算術右シフトの場合は 0 (`Byte`、 `UShort`、 `UInteger`、 `ULong`)</span><span class="sxs-lookup"><span data-stu-id="449ef-147">0 for an arithmetic right shift of an unsigned data type (`Byte`, `UShort`, `UInteger`, `ULong`)</span></span>  
  
-   <span data-ttu-id="449ef-148">負の数値の算術右シフトの 1 (`SByte`、 `Short`、 `Integer`、または`Long`)</span><span class="sxs-lookup"><span data-stu-id="449ef-148">1 for an arithmetic right shift of a negative number (`SByte`, `Short`, `Integer`, or `Long`)</span></span>  
  
 <span data-ttu-id="449ef-149">次の例のシフト、`Integer`左と右の両方の値します。</span><span class="sxs-lookup"><span data-stu-id="449ef-149">The following example shifts an `Integer` value both left and right.</span></span>  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 <span data-ttu-id="449ef-150">算術シフトでは、オーバーフロー例外が生成されません。</span><span class="sxs-lookup"><span data-stu-id="449ef-150">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="449ef-151">ビット処理演算</span><span class="sxs-lookup"><span data-stu-id="449ef-151">Bitwise Operations</span></span>  
 <span data-ttu-id="449ef-152">論理演算子は、だけでなく`Not`、 `Or`、 `And`、および`Xor`も数値を使用する場合にビットごとの演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="449ef-152">In addition to being logical operators, `Not`, `Or`, `And`, and `Xor` also perform bitwise arithmetic when used on numeric values.</span></span> <span data-ttu-id="449ef-153">詳細については、「ビットごとの操作」を参照してください[論理および Visual Basic でビットごとの演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)です。</span><span class="sxs-lookup"><span data-stu-id="449ef-153">For more information, see "Bitwise Operations" in [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).</span></span>  
  
## <a name="type-safety"></a><span data-ttu-id="449ef-154">タイプ セーフ</span><span class="sxs-lookup"><span data-stu-id="449ef-154">Type Safety</span></span>  
 <span data-ttu-id="449ef-155">オペランドは、同じ型の通常する必要があります。</span><span class="sxs-lookup"><span data-stu-id="449ef-155">Operands should normally be of the same type.</span></span> <span data-ttu-id="449ef-156">などの追加を行う場合、`Integer`変数、する必要がありますに追加する別`Integer`して、変数は、型の変数に結果を割り当てる必要があります`Integer`もします。</span><span class="sxs-lookup"><span data-stu-id="449ef-156">For example, if you are doing addition with an `Integer` variable, you should add it to another `Integer` variable, and you should assign the result to a variable of type `Integer` as well.</span></span>  
  
 <span data-ttu-id="449ef-157">適切なタイプ セーフなことを確認する方法の 1 つコーディングの推奨手順を使用するが、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="449ef-157">One way to ensure good type-safe coding practice is to use the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="449ef-158">設定した場合`Option Strict On`、Visual Basic が自動的に実行*タイプ セーフ*変換します。</span><span class="sxs-lookup"><span data-stu-id="449ef-158">If you set `Option Strict On`, Visual Basic automatically performs *type-safe* conversions.</span></span> <span data-ttu-id="449ef-159">追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Double`変数、処理は正常、ため、`Integer`値に変換できる`Double`データの損失なし。</span><span class="sxs-lookup"><span data-stu-id="449ef-159">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to a `Double` variable, the operation proceeds normally, because an `Integer` value can be converted to `Double` without loss of data.</span></span> <span data-ttu-id="449ef-160">タイプ セーフの変換では、その一方とコンパイラ エラーが発生する`Option Strict On`です。</span><span class="sxs-lookup"><span data-stu-id="449ef-160">Type-unsafe conversions, on the other hand, cause a compiler error with `Option Strict On`.</span></span> <span data-ttu-id="449ef-161">追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Integer`変数で、コンパイラ エラーが発生、ため、`Double`変数を型に暗黙的に変換することはできません`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="449ef-161">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to an `Integer` variable, a compiler error results, because a `Double` variable cannot be implicitly converted to type `Integer`.</span></span>  
  
 <span data-ttu-id="449ef-162">設定した場合`Option Strict Off`、ただし、Visual Basic では発生する暗黙的な縮小変換が、予期しないデータまたは精度の損失があります。</span><span class="sxs-lookup"><span data-stu-id="449ef-162">If you set `Option Strict Off`, however, Visual Basic allows implicit narrowing conversions to take place, although they can result in the unexpected loss of data or precision.</span></span> <span data-ttu-id="449ef-163">このため、使用をお勧めする`Option Strict On`実稼働コードを記述する場合。</span><span class="sxs-lookup"><span data-stu-id="449ef-163">For this reason, we recommend that you use `Option Strict On` when writing production code.</span></span> <span data-ttu-id="449ef-164">詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="449ef-164">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449ef-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="449ef-165">See Also</span></span>  
 [<span data-ttu-id="449ef-166">算術演算子</span><span class="sxs-lookup"><span data-stu-id="449ef-166">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="449ef-167">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="449ef-167">Bit Shift Operators</span></span>](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="449ef-168">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="449ef-168">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="449ef-169">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="449ef-169">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="449ef-170">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="449ef-170">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="449ef-171">演算子の効率のよい組み合わせ</span><span class="sxs-lookup"><span data-stu-id="449ef-171">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
