---
title: / 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 17eb3eddfae3cf7c818514a2fee20f646876a6ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604524"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d9754-102">/ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9754-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="d9754-103">2 つの数値を除算し、浮動小数点の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="d9754-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9754-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9754-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="d9754-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d9754-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="d9754-106">必須。</span><span class="sxs-lookup"><span data-stu-id="d9754-106">Required.</span></span> <span data-ttu-id="d9754-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="d9754-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="d9754-108">必須。</span><span class="sxs-lookup"><span data-stu-id="d9754-108">Required.</span></span> <span data-ttu-id="d9754-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="d9754-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="d9754-110">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="d9754-110">Supported Types</span></span>  
 <span data-ttu-id="d9754-111">符号なしと浮動小数点型を含むすべての数値型と`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="d9754-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="d9754-112">結果</span><span class="sxs-lookup"><span data-stu-id="d9754-112">Result</span></span>  
 <span data-ttu-id="d9754-113">結果は完全の商`expression1`で割った値`expression2`、小数部分を含むです。</span><span class="sxs-lookup"><span data-stu-id="d9754-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="d9754-114">[\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)残りの部分を削除する整数の商を返します。</span><span class="sxs-lookup"><span data-stu-id="d9754-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9754-115">コメント</span><span class="sxs-lookup"><span data-stu-id="d9754-115">Remarks</span></span>  
 <span data-ttu-id="d9754-116">結果のデータ型は、オペランドの型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d9754-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="d9754-117">次の表では、結果のデータ型を決定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d9754-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="d9754-118">オペランドのデータ型</span><span class="sxs-lookup"><span data-stu-id="d9754-118">Operand data types</span></span>|<span data-ttu-id="d9754-119">結果のデータ型</span><span class="sxs-lookup"><span data-stu-id="d9754-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="d9754-120">両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="d9754-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="d9754-121">1 つの式は、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)が、他のデータ型では、 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="d9754-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="d9754-122">1 つの式は、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)が、他のデータ型では、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="d9754-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="d9754-123">いずれかの式、[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型</span><span class="sxs-lookup"><span data-stu-id="d9754-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="d9754-124">任意の整数の数値式に拡大変換除算を実行すると、前に`Double`です。</span><span class="sxs-lookup"><span data-stu-id="d9754-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="d9754-125">Visual Basic がの結果を変換しようとした場合は、結果は、整数データ型に割り当てる、`Double`その型にします。</span><span class="sxs-lookup"><span data-stu-id="d9754-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="d9754-126">結果がその型に収まらない場合は、例外がスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="d9754-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="d9754-127">具体的には、このヘルプ ページの「0 による除算」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9754-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="d9754-128">場合`expression1`または`expression2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="d9754-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="d9754-129">0 による除算</span><span class="sxs-lookup"><span data-stu-id="d9754-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="d9754-130">場合`expression2`を 0 に評価される、`/`演算子がオペランドのデータ型の動作が異なります。</span><span class="sxs-lookup"><span data-stu-id="d9754-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="d9754-131">次の表は、可能な動作を示します。</span><span class="sxs-lookup"><span data-stu-id="d9754-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="d9754-132">オペランドのデータ型</span><span class="sxs-lookup"><span data-stu-id="d9754-132">Operand data types</span></span>|<span data-ttu-id="d9754-133">動作場合`expression2`ゼロ</span><span class="sxs-lookup"><span data-stu-id="d9754-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="d9754-134">浮動小数点 (`Single`または`Double`)</span><span class="sxs-lookup"><span data-stu-id="d9754-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="d9754-135">無限大が返されます (<xref:System.Double.PositiveInfinity>または<xref:System.Double.NegativeInfinity>)、または<xref:System.Double.NaN>(非数) 場合`expression1`も 0 であります。</span><span class="sxs-lookup"><span data-stu-id="d9754-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="d9754-136">スローされます。 <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="d9754-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="d9754-137">整数 (符号付きまたは符号なし)</span><span class="sxs-lookup"><span data-stu-id="d9754-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="d9754-138">整数型をスローへの変換を試行<xref:System.OverflowException>整数型を受け入れることはできませんので<xref:System.Double.PositiveInfinity>、 <xref:System.Double.NegativeInfinity>、または <xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="d9754-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d9754-139">`/`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="d9754-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d9754-140">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9754-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d9754-141">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9754-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9754-142">例</span><span class="sxs-lookup"><span data-stu-id="d9754-142">Example</span></span>  
 <span data-ttu-id="d9754-143">この例では、`/`浮動小数点除算を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="d9754-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="d9754-144">結果は、2 つのオペランドの商です。</span><span class="sxs-lookup"><span data-stu-id="d9754-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 <span data-ttu-id="d9754-145">前の例の式は、2.5 3.333333 の値を返します。</span><span class="sxs-lookup"><span data-stu-id="d9754-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="d9754-146">結果は常に浮動小数点 (`Double`) 場合でも、両方のオペランドが整数の定数、します。</span><span class="sxs-lookup"><span data-stu-id="d9754-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9754-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9754-147">See Also</span></span>  
 [<span data-ttu-id="d9754-148">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9754-148">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="d9754-149">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9754-149">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="d9754-150">演算子の結果のデータ型</span><span class="sxs-lookup"><span data-stu-id="d9754-150">Data Types of Operator Results</span></span>](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [<span data-ttu-id="d9754-151">算術演算子</span><span class="sxs-lookup"><span data-stu-id="d9754-151">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="d9754-152">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="d9754-152">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d9754-153">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="d9754-153">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d9754-154">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="d9754-154">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
