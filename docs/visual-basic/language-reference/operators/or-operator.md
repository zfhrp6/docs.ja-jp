---
title: "Or 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Or
dev_langs:
- VB
helpviewer_keywords:
- Or operator
- operators [Visual Basic], bitwise
- inclusive Or operator
- bitwise operators, OR operator
- Or keyword
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison
- logical disjunction
- disjunction operator
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
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
ms.openlocfilehash: 01d51f50dd785f168ed850e3f1763b300d9d2011
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="87c85-102">Or 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c85-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="87c85-103">2 つの論理和を実行`Boolean`式、または&2; つの数値式に対してビット単位の論理和。</span><span class="sxs-lookup"><span data-stu-id="87c85-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c85-104">構文</span><span class="sxs-lookup"><span data-stu-id="87c85-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="87c85-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="87c85-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="87c85-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="87c85-106">Required.</span></span> <span data-ttu-id="87c85-107">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="87c85-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="87c85-108">`Boolean`比較については、`result`は&2; つの包括的論理和`Boolean`値。</span><span class="sxs-lookup"><span data-stu-id="87c85-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="87c85-109">ビットごとの演算`result`は&2; つの数値のビット パターンの包括的論理和を表す数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="87c85-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="87c85-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="87c85-110">Required.</span></span> <span data-ttu-id="87c85-111">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="87c85-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="87c85-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="87c85-112">Required.</span></span> <span data-ttu-id="87c85-113">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="87c85-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87c85-114">コメント</span><span class="sxs-lookup"><span data-stu-id="87c85-114">Remarks</span></span>  
 <span data-ttu-id="87c85-115">`Boolean`比較については、`result`は`False`場合にのみ、両方`expression1`と`expression2`に評価される`False`します。</span><span class="sxs-lookup"><span data-stu-id="87c85-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="87c85-116">次の表に示す方法`result`決定されます。</span><span class="sxs-lookup"><span data-stu-id="87c85-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="87c85-117">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="87c85-117">If `expression1` is</span></span>|<span data-ttu-id="87c85-118">`expression2`は</span><span class="sxs-lookup"><span data-stu-id="87c85-118">And `expression2` is</span></span>|<span data-ttu-id="87c85-119">値`result`は</span><span class="sxs-lookup"><span data-stu-id="87c85-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="87c85-120">`Boolean` 、比較、`Or`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。</span><span class="sxs-lookup"><span data-stu-id="87c85-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="87c85-121">[OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)実行*ショート サーキット*、いる場合は`expression1`は`True`、し`expression2`は評価されません。</span><span class="sxs-lookup"><span data-stu-id="87c85-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="87c85-122">ビットごとの演算、`Or`演算子が&2; つの数値式の同じ位置にビットのビットごとの比較を実行し、対応するでビットを設定`result`次の表に従ってします。</span><span class="sxs-lookup"><span data-stu-id="87c85-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="87c85-123">場合にビット`expression1`は</span><span class="sxs-lookup"><span data-stu-id="87c85-123">If bit in `expression1` is</span></span>|<span data-ttu-id="87c85-124">でビット`expression2`は</span><span class="sxs-lookup"><span data-stu-id="87c85-124">And bit in `expression2` is</span></span>|<span data-ttu-id="87c85-125">内のビット`result`は</span><span class="sxs-lookup"><span data-stu-id="87c85-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="87c85-126">1</span><span class="sxs-lookup"><span data-stu-id="87c85-126">1</span></span>|<span data-ttu-id="87c85-127">1</span><span class="sxs-lookup"><span data-stu-id="87c85-127">1</span></span>|<span data-ttu-id="87c85-128">1</span><span class="sxs-lookup"><span data-stu-id="87c85-128">1</span></span>|  
|<span data-ttu-id="87c85-129">1</span><span class="sxs-lookup"><span data-stu-id="87c85-129">1</span></span>|<span data-ttu-id="87c85-130">0</span><span class="sxs-lookup"><span data-stu-id="87c85-130">0</span></span>|<span data-ttu-id="87c85-131">1</span><span class="sxs-lookup"><span data-stu-id="87c85-131">1</span></span>|  
|<span data-ttu-id="87c85-132">0</span><span class="sxs-lookup"><span data-stu-id="87c85-132">0</span></span>|<span data-ttu-id="87c85-133">1</span><span class="sxs-lookup"><span data-stu-id="87c85-133">1</span></span>|<span data-ttu-id="87c85-134">1</span><span class="sxs-lookup"><span data-stu-id="87c85-134">1</span></span>|  
|<span data-ttu-id="87c85-135">0</span><span class="sxs-lookup"><span data-stu-id="87c85-135">0</span></span>|<span data-ttu-id="87c85-136">0</span><span class="sxs-lookup"><span data-stu-id="87c85-136">0</span></span>|<span data-ttu-id="87c85-137">0</span><span class="sxs-lookup"><span data-stu-id="87c85-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="87c85-138">論理/ビット処理演算子は、他の算術演算子や関係演算子より優先順位が低いため、ビットごとの演算を正確に実行されるようにかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="87c85-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="87c85-139">データ型</span><span class="sxs-lookup"><span data-stu-id="87c85-139">Data Types</span></span>  
 <span data-ttu-id="87c85-140">1 つのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`数値を指定する式 (– 1`True`および 0 を`False`) し、ビットごとの演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="87c85-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="87c85-141">`Boolean`比較については、結果のデータ型は`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="87c85-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="87c85-142">ビットごとの比較結果のデータ型は、数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="87c85-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="87c85-143">「リレーショナルとビットごとの比較」表を参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。</span><span class="sxs-lookup"><span data-stu-id="87c85-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="87c85-144">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="87c85-144">Overloading</span></span>  
 <span data-ttu-id="87c85-145">`Or`演算子を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。</span><span class="sxs-lookup"><span data-stu-id="87c85-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="87c85-146">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義される動作を確認ください。</span><span class="sxs-lookup"><span data-stu-id="87c85-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="87c85-147">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="87c85-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c85-148">例</span><span class="sxs-lookup"><span data-stu-id="87c85-148">Example</span></span>  
 <span data-ttu-id="87c85-149">次の例では、`Or`オペレーターが&2; つの式の包括的論理和を実行します。</span><span class="sxs-lookup"><span data-stu-id="87c85-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="87c85-150">結果は、`Boolean`を表す値が&2; つの式のいずれかのかどうか`True`します。</span><span class="sxs-lookup"><span data-stu-id="87c85-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 <span data-ttu-id="87c85-151">[!code-vb[VbVbalrOperators&#35;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="87c85-151">[!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="87c85-152">前の例の結果を生成する`True`、 `True`、および`False`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="87c85-152">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c85-153">例</span><span class="sxs-lookup"><span data-stu-id="87c85-153">Example</span></span>  
 <span data-ttu-id="87c85-154">次の例では、`Or`オペレーターが&2; つの数値式のビットごとの包括的論理和を実行します。</span><span class="sxs-lookup"><span data-stu-id="87c85-154">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="87c85-155">結果パターン内のビットは、オペランドの対応するビットのいずれか 1 に設定されている場合に設定されます。</span><span class="sxs-lookup"><span data-stu-id="87c85-155">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 <span data-ttu-id="87c85-156">[!code-vb[VbVbalrOperators&#36;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="87c85-156">[!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="87c85-157">前の例では、それぞれ 10、14 日、14 の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="87c85-157">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87c85-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="87c85-158">See Also</span></span>  
 <span data-ttu-id="87c85-159">[論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="87c85-159">[Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="87c85-160"> [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="87c85-160"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="87c85-161"> [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="87c85-161"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="87c85-162"> [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md) </span><span class="sxs-lookup"><span data-stu-id="87c85-162"> [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) </span></span>  
<span data-ttu-id="87c85-163"> [Visual Basic での論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="87c85-163"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>

