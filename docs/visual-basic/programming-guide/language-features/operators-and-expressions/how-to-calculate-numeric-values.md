---
title: "方法: 数値 (Visual Basic) を計算する |Microsoft ドキュメント"
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
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
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
ms.openlocfilehash: fe781cca8f716c792d3af153b2004c716bc87f90
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="e6d4d-102">方法: 数値を計算する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6d4d-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="e6d4d-103">数値式を使用して数値の値を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="e6d4d-104">A*数値式*リテラル、定数、および数値を表す変数を含む式を指定し、それらの値に対して作用する演算子です。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="e6d4d-105">数値の計算</span><span class="sxs-lookup"><span data-stu-id="e6d4d-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="e6d4d-106">数値の値を計算するには</span><span class="sxs-lookup"><span data-stu-id="e6d4d-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="e6d4d-107">数値式に&1; つまたは複数の数値リテラル、定数、および変数を結合します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="e6d4d-108">次の例では、いくつかの有効な数値式を示します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="e6d4d-109">最初の&3; つの行は、リテラル、定数、および変数を示します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="e6d4d-110">1 つは、単独で有効な数値式を形成します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="e6d4d-111">最後の行は、2 つのリテラルと変数の組み合わせを示しています。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="e6d4d-112">数値式が完全な形成されていませんが注[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ステートメント自体でします。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statement by itself.</span></span> <span data-ttu-id="e6d4d-113">完全なステートメントの一部として式を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="e6d4d-114">数値の値を格納するには</span><span class="sxs-lookup"><span data-stu-id="e6d4d-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="e6d4d-115">代入ステートメントを使用すると、次の例に示すように、変数に数値式で表される値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     <span data-ttu-id="e6d4d-116">[!code-vb[VbVbalrOperators #&82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e6d4d-116">[!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]</span></span>  
  
     <span data-ttu-id="e6d4d-117">上記の例では、等値演算子の右側にある式の値 (`=`)、変数に割り当てられた`j`、演算子の左側にあるため、 `j` 276 にします。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-117">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="e6d4d-118">詳細については、次を参照してください。[ステートメント](../../../../visual-basic/language-reference/statements/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-118">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="e6d4d-119">複数の演算子</span><span class="sxs-lookup"><span data-stu-id="e6d4d-119">Multiple Operators</span></span>  
 <span data-ttu-id="e6d4d-120">数値式に複数の演算子が含まれている場合、評価の順序は演算子の優先順位の規則によって決まります。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-120">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="e6d4d-121">演算子の優先順位のルールを無効にするには、式をかっこで囲みます、上記の例に示すように囲まれた式は、最初に評価されます。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-121">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="e6d4d-122">標準の演算子の優先順位をオーバーライドするには</span><span class="sxs-lookup"><span data-stu-id="e6d4d-122">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="e6d4d-123">かっこを使用して、最初に実行する対象の操作を囲みます。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-123">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="e6d4d-124">次の例では、同じオペランドと演算子を持つ&2; つの異なる結果を示します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-124">The following example shows two different results with the same operands and operators.</span></span>  
  
     <span data-ttu-id="e6d4d-125">[!code-vb[VbVbalrOperators&#83;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e6d4d-125">[!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]</span></span>  
  
     <span data-ttu-id="e6d4d-126">前の例の計算で`j`加算演算子の実行 (`+`) 最初ため、かっこで囲まれて`(67 + i)`通常の優先順位、およびに割り当てられた値をオーバーライドする`j`276 (4 回 69) は、です。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-126">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="e6d4d-127">計算`k`、通常の優先順位の演算子を実行 (`*`する前に`+`)、およびに割り当てられた値`k`270 (268 足す 2) は、です。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-127">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="e6d4d-128">詳細については、次を参照してください。 [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)します。</span><span class="sxs-lookup"><span data-stu-id="e6d4d-128">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d4d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6d4d-129">See Also</span></span>  
 <span data-ttu-id="e6d4d-130">[演算子よぶ式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6d4d-130">[Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="e6d4d-131"> [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="e6d4d-131"> [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="e6d4d-132"> [ステートメント](../../../../visual-basic/language-reference/statements/index.md) </span><span class="sxs-lookup"><span data-stu-id="e6d4d-132"> [Statements](../../../../visual-basic/language-reference/statements/index.md) </span></span>  
<span data-ttu-id="e6d4d-133"> [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="e6d4d-133"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="e6d4d-134"> [算術演算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="e6d4d-134"> [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="e6d4d-135"> [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span><span class="sxs-lookup"><span data-stu-id="e6d4d-135"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span></span>
