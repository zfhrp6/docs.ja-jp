---
title: "Mod 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="9e010-102">Mod 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e010-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="9e010-103">2 つの数値を除算し、残りの部分のみを返します。</span><span class="sxs-lookup"><span data-stu-id="9e010-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e010-104">構文</span><span class="sxs-lookup"><span data-stu-id="9e010-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="9e010-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9e010-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="9e010-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="9e010-106">Required.</span></span> <span data-ttu-id="9e010-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="9e010-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="9e010-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="9e010-108">Required.</span></span> <span data-ttu-id="9e010-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="9e010-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="9e010-110">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="9e010-110">Supported Types</span></span>  
 <span data-ttu-id="9e010-111">すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="9e010-111">All numeric types.</span></span> <span data-ttu-id="9e010-112">これには、符号なし型と浮動小数点型が含まれますと`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="9e010-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="9e010-113">結果</span><span class="sxs-lookup"><span data-stu-id="9e010-113">Result</span></span>  
 <span data-ttu-id="9e010-114">結果の後に残りの部分は、`number1`で割った値`number2`です。</span><span class="sxs-lookup"><span data-stu-id="9e010-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="9e010-115">たとえば、式`14 Mod 4`2 に評価します。</span><span class="sxs-lookup"><span data-stu-id="9e010-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e010-116">コメント</span><span class="sxs-lookup"><span data-stu-id="9e010-116">Remarks</span></span>  
 <span data-ttu-id="9e010-117">いずれか`number1`または`number2`浮動小数点値は、浮動小数点除算の剰余が返されます。</span><span class="sxs-lookup"><span data-stu-id="9e010-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="9e010-118">結果のデータ型のデータ型で除算に起因するすべての値を保持できる最小のデータ型は、`number1`と`number2`です。</span><span class="sxs-lookup"><span data-stu-id="9e010-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="9e010-119">場合`number1`または`number2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="9e010-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="9e010-120">関連する演算子を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9e010-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="9e010-121">[\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)除算の商の整数を返します。</span><span class="sxs-lookup"><span data-stu-id="9e010-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="9e010-122">たとえば、式`14 \ 4`3 に評価します。</span><span class="sxs-lookup"><span data-stu-id="9e010-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="9e010-123">[/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)浮動小数点数として、残りの部分を含む、完全商を返します。</span><span class="sxs-lookup"><span data-stu-id="9e010-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="9e010-124">たとえば、式`14 / 4`3.5 に評価します。</span><span class="sxs-lookup"><span data-stu-id="9e010-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="9e010-125">0 による除算</span><span class="sxs-lookup"><span data-stu-id="9e010-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="9e010-126">場合`number2`の動作は 0 に評価される、`Mod`演算子はオペランドのデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9e010-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="9e010-127">整数の除算をスロー、<xref:System.DivideByZeroException>例外。</span><span class="sxs-lookup"><span data-stu-id="9e010-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="9e010-128">浮動小数点除算返します<xref:System.Double.NaN>です。</span><span class="sxs-lookup"><span data-stu-id="9e010-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="9e010-129">同等の数式</span><span class="sxs-lookup"><span data-stu-id="9e010-129">Equivalent Formula</span></span>  
 <span data-ttu-id="9e010-130">式`a Mod b`は次の式のいずれかに相当します。</span><span class="sxs-lookup"><span data-stu-id="9e010-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="9e010-131">浮動小数点は誤差</span><span class="sxs-lookup"><span data-stu-id="9e010-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="9e010-132">浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9e010-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="9e010-133">これにより予期しない結果を比較値などの特定の操作から、`Mod`演算子。</span><span class="sxs-lookup"><span data-stu-id="9e010-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="9e010-134">詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e010-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9e010-135">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="9e010-135">Overloading</span></span>  
 <span data-ttu-id="9e010-136">`Mod`演算子*オーバー ロードされた*、つまり、クラスまたは構造体が、動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="9e010-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="9e010-137">コードが適用される場合`Mod`クラスまたはそのようなオーバー ロードを含む構造体のインスタンスをする、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e010-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9e010-138">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e010-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e010-139">例</span><span class="sxs-lookup"><span data-stu-id="9e010-139">Example</span></span>  
 <span data-ttu-id="9e010-140">次の例では、`Mod`操作を 2 つの数値を除算し、残りの部分のみを返します。</span><span class="sxs-lookup"><span data-stu-id="9e010-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="9e010-141">どちらかの数値が浮動小数点数の場合は、結果は、残りの部分を表す浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="9e010-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9e010-142">例</span><span class="sxs-lookup"><span data-stu-id="9e010-142">Example</span></span>  
 <span data-ttu-id="9e010-143">次の例では、浮動小数点のオペランドの不正確さの可能性を示します。</span><span class="sxs-lookup"><span data-stu-id="9e010-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="9e010-144">オペランドは、最初のステートメントで`Double`0.2、無限に繰り返されるバイナリ分数 0.20000000000000001 として格納されている値とします。</span><span class="sxs-lookup"><span data-stu-id="9e010-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="9e010-145">2 番目のステートメントでは、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`は正確に表現します。</span><span class="sxs-lookup"><span data-stu-id="9e010-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e010-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e010-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="9e010-147">算術演算子</span><span class="sxs-lookup"><span data-stu-id="9e010-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="9e010-148">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="9e010-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="9e010-149">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="9e010-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="9e010-150">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="9e010-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="9e010-151">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="9e010-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="9e010-152">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e010-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
