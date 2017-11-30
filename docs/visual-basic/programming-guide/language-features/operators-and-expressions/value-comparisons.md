---
title: "値の比較 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c11f12bbaf261c0853e96802f03322c5e7fdc706
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="0b4da-102">値の比較 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b4da-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="0b4da-103">比較演算子は、数値変数の値を比較する式を構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0b4da-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="0b4da-104">これらの式を返す、`Boolean`値かどうかに基づいて、比較は true または false です。</span><span class="sxs-lookup"><span data-stu-id="0b4da-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="0b4da-105">このような式の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0b4da-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="0b4da-106">最初の式の評価が`True`45 は 26 より大きいため、します。</span><span class="sxs-lookup"><span data-stu-id="0b4da-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="0b4da-107">2 番目の例を評価する`False`26 は 45 より大きいため、します。</span><span class="sxs-lookup"><span data-stu-id="0b4da-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="0b4da-108">この方法での数値式を比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="0b4da-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="0b4da-109">式を比較する自体には、次の例のように、複雑な式。</span><span class="sxs-lookup"><span data-stu-id="0b4da-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="0b4da-110">この複合式には、リテラル、変数、および関数の呼び出しが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0b4da-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="0b4da-111">比較演算子の両辺の式が評価され、結果として得られる値が使用して比較されます、`>=`比較演算子です。</span><span class="sxs-lookup"><span data-stu-id="0b4da-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="0b4da-112">左側の式の値がより大きいか、右の式の値と等しい、全体の式の評価が`True`以外の場合、評価結果が`False`です。</span><span class="sxs-lookup"><span data-stu-id="0b4da-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="0b4da-113">値を比較する式で最もよく使用`If...Then`次の例のように、構築します。</span><span class="sxs-lookup"><span data-stu-id="0b4da-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="0b4da-114">`=`符号は、比較演算子だけでなく、代入演算子。</span><span class="sxs-lookup"><span data-stu-id="0b4da-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="0b4da-115">比較演算子として使用する場合は、次の例で示すように、左側の値が、右側の値と等しいかどうかを評価します。</span><span class="sxs-lookup"><span data-stu-id="0b4da-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="0b4da-116">任意の場所、比較式を使用することも、`Boolean`値などで、必要なは、 `If`、 `While`、 `Loop`、または`ElseIf`ステートメントを割り当てるかに値を渡すときや、`Boolean`変数。</span><span class="sxs-lookup"><span data-stu-id="0b4da-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="0b4da-117">次の例では、比較式によって返される値が割り当てられている、`Boolean`変数。</span><span class="sxs-lookup"><span data-stu-id="0b4da-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0b4da-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b4da-118">See Also</span></span>  
 [<span data-ttu-id="0b4da-119">ブール式</span><span class="sxs-lookup"><span data-stu-id="0b4da-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="0b4da-120">演算子および式</span><span class="sxs-lookup"><span data-stu-id="0b4da-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="0b4da-121">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="0b4da-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="0b4da-122">方法 : 数値を計算する</span><span class="sxs-lookup"><span data-stu-id="0b4da-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="0b4da-123">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="0b4da-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
