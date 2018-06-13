---
title: '\ 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: ef3946e871e1dc248b54932e16f6cae6026da08e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604238"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bc47d-102">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc47d-102">\ Operator (Visual Basic)</span></span>
<span data-ttu-id="bc47d-103">2 つの数値を除算し、整数の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="bc47d-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc47d-104">構文</span><span class="sxs-lookup"><span data-stu-id="bc47d-104">Syntax</span></span>  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="bc47d-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="bc47d-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="bc47d-106">必須。</span><span class="sxs-lookup"><span data-stu-id="bc47d-106">Required.</span></span> <span data-ttu-id="bc47d-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="bc47d-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="bc47d-108">必須。</span><span class="sxs-lookup"><span data-stu-id="bc47d-108">Required.</span></span> <span data-ttu-id="bc47d-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="bc47d-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="bc47d-110">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="bc47d-110">Supported Types</span></span>  
 <span data-ttu-id="bc47d-111">符号なしと浮動小数点型を含むすべての数値型と`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="bc47d-112">結果</span><span class="sxs-lookup"><span data-stu-id="bc47d-112">Result</span></span>  
 <span data-ttu-id="bc47d-113">結果は整数の商`expression1`で割った値`expression2`、小数部分を破棄し、整数部分のみを保持します。</span><span class="sxs-lookup"><span data-stu-id="bc47d-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="bc47d-114">これは呼ば*切り捨て*です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="bc47d-115">結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="bc47d-116">「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="bc47d-117">[/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)小数部分の残りの部分を保持するフルの商を返します。</span><span class="sxs-lookup"><span data-stu-id="bc47d-117">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc47d-118">コメント</span><span class="sxs-lookup"><span data-stu-id="bc47d-118">Remarks</span></span>  
 <span data-ttu-id="bc47d-119">除算を実行する前に、Visual Basic に任意の浮動小数点の数値式の変換を試みます`Long`です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="bc47d-120">場合`Option Strict`は`On`、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bc47d-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="bc47d-121">場合`Option Strict`は`Off`、<xref:System.OverflowException>値の範囲外の場合は、 [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md).</span></span> <span data-ttu-id="bc47d-122">変換`Long`対象にも*銀行型丸め*です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="bc47d-123">詳細についてを参照してください「小数部分」[型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="bc47d-124">場合`expression1`または`expression2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="bc47d-124">If `expression1` or `expression2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="bc47d-125">0 による除算</span><span class="sxs-lookup"><span data-stu-id="bc47d-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="bc47d-126">場合`expression2`を 0 に評価される、`\`演算子をスロー、<xref:System.DivideByZeroException>例外。</span><span class="sxs-lookup"><span data-stu-id="bc47d-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="bc47d-127">これは、すべての数値データ型のオペランドの場合は true です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc47d-128">`\`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="bc47d-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bc47d-129">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc47d-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bc47d-130">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-130">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc47d-131">例</span><span class="sxs-lookup"><span data-stu-id="bc47d-131">Example</span></span>  
 <span data-ttu-id="bc47d-132">次の例では、`\`整数除算を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="bc47d-133">結果は、破棄された後に 2 つのオペランドの商の整数を表す整数です。</span><span class="sxs-lookup"><span data-stu-id="bc47d-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 <span data-ttu-id="bc47d-134">前の例の式では、2、3、33、および、~ 22 日の値をそれぞれ返します。</span><span class="sxs-lookup"><span data-stu-id="bc47d-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc47d-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc47d-135">See Also</span></span>  
 [<span data-ttu-id="bc47d-136">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="bc47d-136">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="bc47d-137">/演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc47d-137">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="bc47d-138">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="bc47d-138">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="bc47d-139">算術演算子</span><span class="sxs-lookup"><span data-stu-id="bc47d-139">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="bc47d-140">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="bc47d-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="bc47d-141">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="bc47d-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="bc47d-142">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="bc47d-142">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
