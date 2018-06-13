---
title: Or 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 9e02f619a81ee3c15321dfd44963c1a7d29843ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604771"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="a6dd9-102">Or 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6dd9-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="a6dd9-103">2 つの論理和を求めます`Boolean`式、または 2 つの数値式のビットごとの論理和です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6dd9-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6dd9-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="a6dd9-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a6dd9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a6dd9-106">必須。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-106">Required.</span></span> <span data-ttu-id="a6dd9-107">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="a6dd9-108">`Boolean`比較、`result`は 2 つの包括的論理和`Boolean`値。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="a6dd9-109">ビットごとの演算`result`は、次の 2 つの数値のビット パターンの包括的論理和を表す数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="a6dd9-110">必須。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-110">Required.</span></span> <span data-ttu-id="a6dd9-111">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a6dd9-112">必須。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-112">Required.</span></span> <span data-ttu-id="a6dd9-113">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6dd9-114">コメント</span><span class="sxs-lookup"><span data-stu-id="a6dd9-114">Remarks</span></span>  
 <span data-ttu-id="a6dd9-115">`Boolean`比較、`result`は`False`場合にのみ、両方`expression1`と`expression2`に評価される`False`です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="a6dd9-116">次に示す方法`result`決定されます。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="a6dd9-117">場合`expression1`は</span><span class="sxs-lookup"><span data-stu-id="a6dd9-117">If `expression1` is</span></span>|<span data-ttu-id="a6dd9-118">および`expression2`は</span><span class="sxs-lookup"><span data-stu-id="a6dd9-118">And `expression2` is</span></span>|<span data-ttu-id="a6dd9-119">値`result`は</span><span class="sxs-lookup"><span data-stu-id="a6dd9-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="a6dd9-120">`Boolean` 、比較、`Or`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="a6dd9-121">[OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)実行*ショート サーキット*、つまりを`expression1`は`True`、し、`expression2`は評価されません。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="a6dd9-122">ビットごとの演算、`Or`演算子が 2 つの数値式で同じ位置にビットのビットごとの比較を実行し、対応するにビットを設定`result`次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="a6dd9-123">場合内のビット`expression1`は</span><span class="sxs-lookup"><span data-stu-id="a6dd9-123">If bit in `expression1` is</span></span>|<span data-ttu-id="a6dd9-124">でビット`expression2`は</span><span class="sxs-lookup"><span data-stu-id="a6dd9-124">And bit in `expression2` is</span></span>|<span data-ttu-id="a6dd9-125">内のビット`result`は</span><span class="sxs-lookup"><span data-stu-id="a6dd9-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="a6dd9-126">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-126">1</span></span>|<span data-ttu-id="a6dd9-127">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-127">1</span></span>|<span data-ttu-id="a6dd9-128">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-128">1</span></span>|  
|<span data-ttu-id="a6dd9-129">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-129">1</span></span>|<span data-ttu-id="a6dd9-130">0</span><span class="sxs-lookup"><span data-stu-id="a6dd9-130">0</span></span>|<span data-ttu-id="a6dd9-131">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-131">1</span></span>|  
|<span data-ttu-id="a6dd9-132">0</span><span class="sxs-lookup"><span data-stu-id="a6dd9-132">0</span></span>|<span data-ttu-id="a6dd9-133">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-133">1</span></span>|<span data-ttu-id="a6dd9-134">1</span><span class="sxs-lookup"><span data-stu-id="a6dd9-134">1</span></span>|  
|<span data-ttu-id="a6dd9-135">0</span><span class="sxs-lookup"><span data-stu-id="a6dd9-135">0</span></span>|<span data-ttu-id="a6dd9-136">0</span><span class="sxs-lookup"><span data-stu-id="a6dd9-136">0</span></span>|<span data-ttu-id="a6dd9-137">0</span><span class="sxs-lookup"><span data-stu-id="a6dd9-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a6dd9-138">論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確に実行されるようにかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="a6dd9-139">データの種類</span><span class="sxs-lookup"><span data-stu-id="a6dd9-139">Data Types</span></span>  
 <span data-ttu-id="a6dd9-140">いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`数値を指定する式 (– 1`True`と 0 を`False`) し、ビットごとの演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="a6dd9-141">`Boolean` 、比較結果のデータ型は`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="a6dd9-142">ビットごとの比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a6dd9-143">「リレーショナルとビットごとの比較」表を参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a6dd9-144">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="a6dd9-144">Overloading</span></span>  
 <span data-ttu-id="a6dd9-145">`Or`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a6dd9-146">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a6dd9-147">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6dd9-148">例</span><span class="sxs-lookup"><span data-stu-id="a6dd9-148">Example</span></span>  
 <span data-ttu-id="a6dd9-149">次の例では、`Or`オペレーターが 2 つの式の包括的論理和を実行します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="a6dd9-150">結果は、`Boolean`を表す値が 2 つの式のいずれかのかどうか`True`です。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 <span data-ttu-id="a6dd9-151">前の例の結果を生成する`True`、 `True`、および`False`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6dd9-152">例</span><span class="sxs-lookup"><span data-stu-id="a6dd9-152">Example</span></span>  
 <span data-ttu-id="a6dd9-153">次の例では、`Or`オペレーターが 2 つの数値式のビットごとの包括的論理和を実行します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="a6dd9-154">結果のパターン内のビットは、オペランドの対応するビットのいずれか 1 に設定されている場合に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 <span data-ttu-id="a6dd9-155">前の例では、それぞれ 10、14、14 の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="a6dd9-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6dd9-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6dd9-156">See Also</span></span>  
 [<span data-ttu-id="a6dd9-157">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6dd9-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="a6dd9-158">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="a6dd9-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="a6dd9-159">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="a6dd9-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="a6dd9-160">OrElse 演算子</span><span class="sxs-lookup"><span data-stu-id="a6dd9-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [<span data-ttu-id="a6dd9-161">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="a6dd9-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
