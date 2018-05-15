---
title: Not 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 332cee57c8d25d7f51737e01e70ba515d50bd6e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="6fc6c-102">Not 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc6c-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="6fc6c-103">論理否定を実行、`Boolean`式、または数値式のビットごとの否定。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fc6c-104">構文</span><span class="sxs-lookup"><span data-stu-id="6fc6c-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="6fc6c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="6fc6c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6fc6c-106">必須。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-106">Required.</span></span> <span data-ttu-id="6fc6c-107">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="6fc6c-108">必須。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-108">Required.</span></span> <span data-ttu-id="6fc6c-109">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fc6c-110">コメント</span><span class="sxs-lookup"><span data-stu-id="6fc6c-110">Remarks</span></span>  
 <span data-ttu-id="6fc6c-111">`Boolean`式では、次の表に示す方法`result`決定されます。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="6fc6c-112">場合`expression`は</span><span class="sxs-lookup"><span data-stu-id="6fc6c-112">If `expression` is</span></span>|<span data-ttu-id="6fc6c-113">値`result`は</span><span class="sxs-lookup"><span data-stu-id="6fc6c-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="6fc6c-114">数値式の場合、`Not`演算子が任意の数値式のビット値を反転し、対応するにビットを設定`result`次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="6fc6c-115">場合内のビット`expression`は</span><span class="sxs-lookup"><span data-stu-id="6fc6c-115">If bit in `expression` is</span></span>|<span data-ttu-id="6fc6c-116">内のビット`result`は</span><span class="sxs-lookup"><span data-stu-id="6fc6c-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="6fc6c-117">1</span><span class="sxs-lookup"><span data-stu-id="6fc6c-117">1</span></span>|<span data-ttu-id="6fc6c-118">0</span><span class="sxs-lookup"><span data-stu-id="6fc6c-118">0</span></span>|  
|<span data-ttu-id="6fc6c-119">0</span><span class="sxs-lookup"><span data-stu-id="6fc6c-119">0</span></span>|<span data-ttu-id="6fc6c-120">1</span><span class="sxs-lookup"><span data-stu-id="6fc6c-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6fc6c-121">論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確に実行されるようにかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="6fc6c-122">データの種類</span><span class="sxs-lookup"><span data-stu-id="6fc6c-122">Data Types</span></span>  
 <span data-ttu-id="6fc6c-123">結果のデータ型は、ブール型の否定の`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="6fc6c-124">ビットごとの否定の結果のデータ型は、のと同じ`expression`です。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="6fc6c-125">ただし、式が場合`Decimal`、結果は`Long`します。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6fc6c-126">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="6fc6c-126">Overloading</span></span>  
 <span data-ttu-id="6fc6c-127">`Not`演算子を指定できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できますその動作のオペランドは、そのクラスまたは構造体の型を持つときにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="6fc6c-128">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6fc6c-129">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc6c-130">例</span><span class="sxs-lookup"><span data-stu-id="6fc6c-130">Example</span></span>  
 <span data-ttu-id="6fc6c-131">次の例では、`Not`に対して論理否定演算を実行する演算子、`Boolean`式。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="6fc6c-132">結果は、`Boolean`式の値の逆を表す値です。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 <span data-ttu-id="6fc6c-133">前の例の結果を生成する`False`と`True`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc6c-134">例</span><span class="sxs-lookup"><span data-stu-id="6fc6c-134">Example</span></span>  
 <span data-ttu-id="6fc6c-135">次の例では、`Not`数値式のビットごとの論理否定演算を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="6fc6c-136">結果のパターン内のビットは符号ビットを含めて、オペランドのパターンに対応するビットの逆に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 <span data-ttu-id="6fc6c-137">前の例では、それぞれ – 11、– 9、および – 7 の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="6fc6c-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc6c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fc6c-138">See Also</span></span>  
 [<span data-ttu-id="6fc6c-139">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc6c-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="6fc6c-140">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="6fc6c-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="6fc6c-141">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="6fc6c-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="6fc6c-142">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="6fc6c-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
