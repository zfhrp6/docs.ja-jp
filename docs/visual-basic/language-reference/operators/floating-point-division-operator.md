---
title: "/演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 82255339c3bdab7f6e760de9bef073f463260877
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1abae-102">/ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1abae-102">/ Operator (Visual Basic)</span></span>
<span data-ttu-id="1abae-103">2 つの数値を除算して、浮動小数点の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="1abae-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abae-104">構文</span><span class="sxs-lookup"><span data-stu-id="1abae-104">Syntax</span></span>  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1abae-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1abae-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="1abae-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="1abae-106">Required.</span></span> <span data-ttu-id="1abae-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="1abae-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1abae-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="1abae-108">Required.</span></span> <span data-ttu-id="1abae-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="1abae-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="1abae-110">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="1abae-110">Supported Types</span></span>  
 <span data-ttu-id="1abae-111">署名なしで、浮動小数点型を含むすべての数値型と`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="1abae-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="1abae-112">結果</span><span class="sxs-lookup"><span data-stu-id="1abae-112">Result</span></span>  
 <span data-ttu-id="1abae-113">結果は、すべての商`expression1`で割った値`expression2`、小数部分を含みます。</span><span class="sxs-lookup"><span data-stu-id="1abae-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="1abae-114">[\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)残りの部分を削除する整数の商を返します。</span><span class="sxs-lookup"><span data-stu-id="1abae-114">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1abae-115">コメント</span><span class="sxs-lookup"><span data-stu-id="1abae-115">Remarks</span></span>  
 <span data-ttu-id="1abae-116">結果のデータ型は、オペランドの型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1abae-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="1abae-117">次の表では、結果のデータ型を決定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1abae-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="1abae-118">オペランドのデータ型</span><span class="sxs-lookup"><span data-stu-id="1abae-118">Operand data types</span></span>|<span data-ttu-id="1abae-119">結果のデータ型</span><span class="sxs-lookup"><span data-stu-id="1abae-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="1abae-120">両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="1abae-120">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="1abae-121">1 つの式は、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)データ型と、その他は、[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="1abae-121">One expression is a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) data type and the other is not a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="1abae-122">1 つの式は、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)データ型とその他のではありません、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="1abae-122">One expression is a [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) data type and the other is not a [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) or a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="1abae-123">いずれかの式、[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型</span><span class="sxs-lookup"><span data-stu-id="1abae-123">Either expression is a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="1abae-124">整数の数式に拡大変換除算を実行する前に`Double`します。</span><span class="sxs-lookup"><span data-stu-id="1abae-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="1abae-125">Visual Basic がから結果を変換しようとした場合は、結果を整数データ型を割り当てると、`Double`その型にします。</span><span class="sxs-lookup"><span data-stu-id="1abae-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="1abae-126">結果がその型に収まらない場合は、例外がスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="1abae-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="1abae-127">具体的には、このページで「0 による除算」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1abae-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="1abae-128">場合`expression1`または`expression2`に評価[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="1abae-128">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="1abae-129">0 による除算</span><span class="sxs-lookup"><span data-stu-id="1abae-129">Attempted Division by Zero</span></span>  
 <span data-ttu-id="1abae-130">場合`expression2`をゼロに評価される、`/`演算子がオペランドのデータ型の動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="1abae-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="1abae-131">次の表は、それぞれの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="1abae-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="1abae-132">オペランドのデータ型</span><span class="sxs-lookup"><span data-stu-id="1abae-132">Operand data types</span></span>|<span data-ttu-id="1abae-133">動作場合`expression2`ゼロ</span><span class="sxs-lookup"><span data-stu-id="1abae-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="1abae-134">浮動小数点 (`Single`または`Double`)</span><span class="sxs-lookup"><span data-stu-id="1abae-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="1abae-135">無限大が返されます (<xref:System.Double.PositiveInfinity>または<xref:System.Double.NegativeInfinity>)、または<xref:System.Double.NaN>(非数) 場合`expression1`も&0; である</xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></span><span class="sxs-lookup"><span data-stu-id="1abae-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="1abae-136">スローされます。<xref:System.DivideByZeroException></xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="1abae-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="1abae-137">整数 (符号付きまたは符号なし)</span><span class="sxs-lookup"><span data-stu-id="1abae-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="1abae-138">整数型への変換を試行<xref:System.OverflowException>整数型を受け入れることはできませんので<xref:System.Double.PositiveInfinity>、 <xref:System.Double.NegativeInfinity>、または<xref:System.Double.NaN></xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></xref:System.OverflowException></span><span class="sxs-lookup"><span data-stu-id="1abae-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1abae-139">`/`演算子を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。</span><span class="sxs-lookup"><span data-stu-id="1abae-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1abae-140">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義される動作を確認ください。</span><span class="sxs-lookup"><span data-stu-id="1abae-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1abae-141">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="1abae-141">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1abae-142">例</span><span class="sxs-lookup"><span data-stu-id="1abae-142">Example</span></span>  
 <span data-ttu-id="1abae-143">この例では、`/`浮動小数点除算を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="1abae-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="1abae-144">結果は、2 つのオペランドの商です。</span><span class="sxs-lookup"><span data-stu-id="1abae-144">The result is the quotient of the two operands.</span></span>  
  
 <span data-ttu-id="1abae-145">[!code-vb[VbVbalrOperators&#16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1abae-145">[!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="1abae-146">前の例の式では、2.5 と 3.333333 の値を返します。</span><span class="sxs-lookup"><span data-stu-id="1abae-146">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="1abae-147">結果が常に浮動小数点型ことに注意してください (`Double`) 場合でも、両方のオペランドが整数の定数、します。</span><span class="sxs-lookup"><span data-stu-id="1abae-147">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abae-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="1abae-148">See Also</span></span>  
 <span data-ttu-id="1abae-149">[/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="1abae-149">[/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="1abae-150"> [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="1abae-150"> [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) </span></span>  
<span data-ttu-id="1abae-151"> [演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span><span class="sxs-lookup"><span data-stu-id="1abae-151"> [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md) </span></span>  
<span data-ttu-id="1abae-152"> [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="1abae-152"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="1abae-153"> [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="1abae-153"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="1abae-154"> [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="1abae-154"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="1abae-155"> [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="1abae-155"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

