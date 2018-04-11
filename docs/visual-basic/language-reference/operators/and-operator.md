---
title: And 演算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="18042-102">And 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18042-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="18042-103">2 つの論理積`Boolean`式、または 2 つの数値式に対してビットごとの積。</span><span class="sxs-lookup"><span data-stu-id="18042-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18042-104">構文</span><span class="sxs-lookup"><span data-stu-id="18042-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="18042-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="18042-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="18042-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="18042-106">Required.</span></span> <span data-ttu-id="18042-107">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="18042-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="18042-108">ブール値の比較の`result`は 2 つの論理積`Boolean`値。</span><span class="sxs-lookup"><span data-stu-id="18042-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="18042-109">ビットごとの演算`result`は、次の 2 つの数値のビット パターンのビットごとの積を表す数値を指定します。</span><span class="sxs-lookup"><span data-stu-id="18042-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="18042-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="18042-110">Required.</span></span> <span data-ttu-id="18042-111">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="18042-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="18042-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="18042-112">Required.</span></span> <span data-ttu-id="18042-113">どの`Boolean`または数値式です。</span><span class="sxs-lookup"><span data-stu-id="18042-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18042-114">コメント</span><span class="sxs-lookup"><span data-stu-id="18042-114">Remarks</span></span>  
 <span data-ttu-id="18042-115">ブール値の比較の`result`は`True`場合にのみ、両方`expression1`と`expression2`に評価される`True`です。</span><span class="sxs-lookup"><span data-stu-id="18042-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="18042-116">次に示す方法`result`決定されます。</span><span class="sxs-lookup"><span data-stu-id="18042-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="18042-117">場合`expression1`は</span><span class="sxs-lookup"><span data-stu-id="18042-117">If `expression1` is</span></span>|<span data-ttu-id="18042-118">および`expression2`は</span><span class="sxs-lookup"><span data-stu-id="18042-118">And `expression2` is</span></span>|<span data-ttu-id="18042-119">値`result`は</span><span class="sxs-lookup"><span data-stu-id="18042-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="18042-120">ブール値の比較で、`And`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。</span><span class="sxs-lookup"><span data-stu-id="18042-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="18042-121">[AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)実行*ショート サーキット*、つまりを`expression1`は`False`、し、`expression2`は評価されません。</span><span class="sxs-lookup"><span data-stu-id="18042-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="18042-122">数値の値に適用されるときに、`And`演算子が 2 つの数値式で同じ位置にビットのビットごとの比較を実行し、対応するにビットを設定`result`次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="18042-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="18042-123">場合内のビット`expression1`は</span><span class="sxs-lookup"><span data-stu-id="18042-123">If bit in `expression1` is</span></span>|<span data-ttu-id="18042-124">でビット`expression2`は</span><span class="sxs-lookup"><span data-stu-id="18042-124">And bit in `expression2` is</span></span>|<span data-ttu-id="18042-125">内のビット`result`は</span><span class="sxs-lookup"><span data-stu-id="18042-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="18042-126">1</span><span class="sxs-lookup"><span data-stu-id="18042-126">1</span></span>|<span data-ttu-id="18042-127">1</span><span class="sxs-lookup"><span data-stu-id="18042-127">1</span></span>|<span data-ttu-id="18042-128">1</span><span class="sxs-lookup"><span data-stu-id="18042-128">1</span></span>|  
|<span data-ttu-id="18042-129">1</span><span class="sxs-lookup"><span data-stu-id="18042-129">1</span></span>|<span data-ttu-id="18042-130">0</span><span class="sxs-lookup"><span data-stu-id="18042-130">0</span></span>|<span data-ttu-id="18042-131">0</span><span class="sxs-lookup"><span data-stu-id="18042-131">0</span></span>|  
|<span data-ttu-id="18042-132">0</span><span class="sxs-lookup"><span data-stu-id="18042-132">0</span></span>|<span data-ttu-id="18042-133">1</span><span class="sxs-lookup"><span data-stu-id="18042-133">1</span></span>|<span data-ttu-id="18042-134">0</span><span class="sxs-lookup"><span data-stu-id="18042-134">0</span></span>|  
|<span data-ttu-id="18042-135">0</span><span class="sxs-lookup"><span data-stu-id="18042-135">0</span></span>|<span data-ttu-id="18042-136">0</span><span class="sxs-lookup"><span data-stu-id="18042-136">0</span></span>|<span data-ttu-id="18042-137">0</span><span class="sxs-lookup"><span data-stu-id="18042-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="18042-138">論理演算子およびビット演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確な結果のようにかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="18042-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="18042-139">データ型</span><span class="sxs-lookup"><span data-stu-id="18042-139">Data Types</span></span>  
 <span data-ttu-id="18042-140">いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`数値を指定する式 (– 1`True`と 0 を`False`) し、ビットごとの演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="18042-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="18042-141">ブール値の比較結果のデータ型は`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="18042-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="18042-142">ビットごとの比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="18042-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="18042-143">「リレーショナルとビットごとの比較」表を参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="18042-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18042-144">`And`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="18042-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="18042-145">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="18042-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="18042-146">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="18042-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18042-147">例</span><span class="sxs-lookup"><span data-stu-id="18042-147">Example</span></span>  
 <span data-ttu-id="18042-148">次の例では、 `And` 2 つの式に対して論理積を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="18042-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="18042-149">結果は、`Boolean`が両方の式かどうかを表す値`True`です。</span><span class="sxs-lookup"><span data-stu-id="18042-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="18042-150">前の例の結果を生成する`True`と`False`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="18042-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18042-151">例</span><span class="sxs-lookup"><span data-stu-id="18042-151">Example</span></span>  
 <span data-ttu-id="18042-152">次の例では、`And`オペレーターが 2 つの数値式のビットごとの論理積を実行します。</span><span class="sxs-lookup"><span data-stu-id="18042-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="18042-153">結果のパターン内のビットは、オペランドの対応するビットは次の両方 1 に設定する場合に設定されます。</span><span class="sxs-lookup"><span data-stu-id="18042-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="18042-154">前の例では、それぞれ 8、2、および 0 の場合の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="18042-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18042-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="18042-155">See Also</span></span>  
 [<span data-ttu-id="18042-156">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18042-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="18042-157">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="18042-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="18042-158">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="18042-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="18042-159">AndAlso 演算子</span><span class="sxs-lookup"><span data-stu-id="18042-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="18042-160">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="18042-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
