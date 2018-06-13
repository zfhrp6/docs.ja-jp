---
title: Mod 演算子 (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5120823f4e001fc3aff71f267176311e2465597a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604851"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="787f9-102">Mod 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="787f9-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="787f9-103">2 つの数値を除算し、残りの部分のみを返します。</span><span class="sxs-lookup"><span data-stu-id="787f9-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="787f9-104">構文</span><span class="sxs-lookup"><span data-stu-id="787f9-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="787f9-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="787f9-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="787f9-106">必須。</span><span class="sxs-lookup"><span data-stu-id="787f9-106">Required.</span></span> <span data-ttu-id="787f9-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="787f9-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="787f9-108">必須。</span><span class="sxs-lookup"><span data-stu-id="787f9-108">Required.</span></span> <span data-ttu-id="787f9-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="787f9-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="787f9-110">サポートされる型</span><span class="sxs-lookup"><span data-stu-id="787f9-110">Supported types</span></span>  
 <span data-ttu-id="787f9-111">すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="787f9-111">All numeric types.</span></span> <span data-ttu-id="787f9-112">これには、符号なし型と浮動小数点型が含まれますと`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="787f9-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="787f9-113">結果</span><span class="sxs-lookup"><span data-stu-id="787f9-113">Result</span></span>

<span data-ttu-id="787f9-114">結果の後に残りの部分は、`number1`で割った値`number2`です。</span><span class="sxs-lookup"><span data-stu-id="787f9-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="787f9-115">たとえば、式`14 Mod 4`2 に評価します。</span><span class="sxs-lookup"><span data-stu-id="787f9-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="787f9-116">間で違いがある*剰余*と*剰余*数学では、負の値ごとに異なる結果にします。</span><span class="sxs-lookup"><span data-stu-id="787f9-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="787f9-117">`Mod` Visual Basic、.NET Framework で演算子`op_Modulus`演算子、および基になる [rem]<xref:System.Reflection.Emit.OpCodes.Rem>剰余演算を実行する IL 命令します。</span><span class="sxs-lookup"><span data-stu-id="787f9-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="787f9-118">結果、`Mod`操作は、被除数の符号が保持されます`number1`、ため、正または負の値があります。</span><span class="sxs-lookup"><span data-stu-id="787f9-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="787f9-119">結果が範囲内に常に (-`number2`、 `number2`)、排他的なです。</span><span class="sxs-lookup"><span data-stu-id="787f9-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="787f9-120">例えば:</span><span class="sxs-lookup"><span data-stu-id="787f9-120">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="787f9-121">コメント</span><span class="sxs-lookup"><span data-stu-id="787f9-121">Remarks</span></span>  
 <span data-ttu-id="787f9-122">いずれか`number1`または`number2`浮動小数点値は、浮動小数点除算の剰余が返されます。</span><span class="sxs-lookup"><span data-stu-id="787f9-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="787f9-123">結果のデータ型のデータ型で除算に起因するすべての値を保持できる最小のデータ型は、`number1`と`number2`です。</span><span class="sxs-lookup"><span data-stu-id="787f9-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="787f9-124">場合`number1`または`number2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="787f9-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="787f9-125">関連する演算子を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="787f9-125">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="787f9-126">[\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)除算の商の整数を返します。</span><span class="sxs-lookup"><span data-stu-id="787f9-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="787f9-127">たとえば、式`14 \ 4`3 に評価します。</span><span class="sxs-lookup"><span data-stu-id="787f9-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="787f9-128">[/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)浮動小数点数として、残りの部分を含む、完全商を返します。</span><span class="sxs-lookup"><span data-stu-id="787f9-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="787f9-129">たとえば、式`14 / 4`3.5 に評価します。</span><span class="sxs-lookup"><span data-stu-id="787f9-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="787f9-130">0 による除算</span><span class="sxs-lookup"><span data-stu-id="787f9-130">Attempted division by zero</span></span>  
 <span data-ttu-id="787f9-131">場合`number2`の動作は 0 に評価される、`Mod`演算子はオペランドのデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="787f9-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="787f9-132">整数の除算をスロー、<xref:System.DivideByZeroException>例外。</span><span class="sxs-lookup"><span data-stu-id="787f9-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="787f9-133">浮動小数点除算返します<xref:System.Double.NaN>です。</span><span class="sxs-lookup"><span data-stu-id="787f9-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="787f9-134">同等の数式</span><span class="sxs-lookup"><span data-stu-id="787f9-134">Equivalent formula</span></span>  
 <span data-ttu-id="787f9-135">式`a Mod b`は次の式のいずれかに相当します。</span><span class="sxs-lookup"><span data-stu-id="787f9-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="787f9-136">浮動小数点は誤差</span><span class="sxs-lookup"><span data-stu-id="787f9-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="787f9-137">浮動小数点数を操作するときに、常がない正確な 10 進表現メモリに注意してください。</span><span class="sxs-lookup"><span data-stu-id="787f9-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="787f9-138">値の比較などの特定の操作から予期しない結果につながる可能性がこれと`Mod`演算子。</span><span class="sxs-lookup"><span data-stu-id="787f9-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="787f9-139">詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="787f9-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="787f9-140">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="787f9-140">Overloading</span></span>  
 <span data-ttu-id="787f9-141">`Mod`演算子*オーバー ロードされた*、つまり、クラスまたは構造体が、動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="787f9-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="787f9-142">コードが適用される場合`Mod`クラスまたはそのようなオーバー ロードを含む構造体のインスタンスをする、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="787f9-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="787f9-143">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="787f9-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="787f9-144">例</span><span class="sxs-lookup"><span data-stu-id="787f9-144">Example</span></span>  
 <span data-ttu-id="787f9-145">次の例では、`Mod`操作を 2 つの数値を除算し、残りの部分のみを返します。</span><span class="sxs-lookup"><span data-stu-id="787f9-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="787f9-146">どちらかの数値が浮動小数点数の場合は、結果は、残りの部分を表す浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="787f9-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="787f9-147">例</span><span class="sxs-lookup"><span data-stu-id="787f9-147">Example</span></span>  
 <span data-ttu-id="787f9-148">次の例では、浮動小数点のオペランドの不正確さの可能性を示します。</span><span class="sxs-lookup"><span data-stu-id="787f9-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="787f9-149">オペランドは、最初のステートメントで`Double`0.2、無限に繰り返されるバイナリ分数 0.20000000000000001 として格納されている値とします。</span><span class="sxs-lookup"><span data-stu-id="787f9-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="787f9-150">2 番目のステートメントでは、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`は正確に表現します。</span><span class="sxs-lookup"><span data-stu-id="787f9-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="787f9-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="787f9-151">See also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="787f9-152">算術演算子</span><span class="sxs-lookup"><span data-stu-id="787f9-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="787f9-153">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="787f9-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="787f9-154">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="787f9-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="787f9-155">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="787f9-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="787f9-156">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="787f9-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="787f9-157">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="787f9-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
