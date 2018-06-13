---
title: OrElse 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604823"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="fbaee-102">OrElse 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbaee-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="fbaee-103">ショート サーキットの 2 つの式の包括的論理和を実行します。</span><span class="sxs-lookup"><span data-stu-id="fbaee-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbaee-104">構文</span><span class="sxs-lookup"><span data-stu-id="fbaee-104">Syntax</span></span>  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="fbaee-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="fbaee-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="fbaee-106">必須。</span><span class="sxs-lookup"><span data-stu-id="fbaee-106">Required.</span></span> <span data-ttu-id="fbaee-107">任意のブール型 (`Boolean`) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbaee-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="fbaee-108">必須。</span><span class="sxs-lookup"><span data-stu-id="fbaee-108">Required.</span></span> <span data-ttu-id="fbaee-109">任意のブール型 (`Boolean`) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbaee-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="fbaee-110">必須。</span><span class="sxs-lookup"><span data-stu-id="fbaee-110">Required.</span></span> <span data-ttu-id="fbaee-111">任意のブール型 (`Boolean`) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="fbaee-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbaee-112">コメント</span><span class="sxs-lookup"><span data-stu-id="fbaee-112">Remarks</span></span>  
 <span data-ttu-id="fbaee-113">論理演算があると言われます*ショート サーキット*場合は、コンパイルされたコードが別の式の結果に応じて、1 つの式の評価をバイパスできます。</span><span class="sxs-lookup"><span data-stu-id="fbaee-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="fbaee-114">最初に評価される式の結果には、操作の最終的な結果が判断した場合必要はありませんを 2 番目の式を評価するため、最終的な結果を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="fbaee-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="fbaee-115">ショート サーキットによりでバイパスされる式が複雑な場合、またはプロシージャの呼び出しが含まれる場合、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="fbaee-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="fbaee-116">いずれかまたは両方の式に評価される場合`True`、`result`は`True`します。</span><span class="sxs-lookup"><span data-stu-id="fbaee-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="fbaee-117">次に示す方法`result`決定されます。</span><span class="sxs-lookup"><span data-stu-id="fbaee-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="fbaee-118">場合`expression1`は</span><span class="sxs-lookup"><span data-stu-id="fbaee-118">If `expression1` is</span></span>|<span data-ttu-id="fbaee-119">および`expression2`は</span><span class="sxs-lookup"><span data-stu-id="fbaee-119">And `expression2` is</span></span>|<span data-ttu-id="fbaee-120">値`result`は</span><span class="sxs-lookup"><span data-stu-id="fbaee-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="fbaee-121">(評価されません)</span><span class="sxs-lookup"><span data-stu-id="fbaee-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="fbaee-122">データの種類</span><span class="sxs-lookup"><span data-stu-id="fbaee-122">Data Types</span></span>  
 <span data-ttu-id="fbaee-123">`OrElse`に対してのみ演算子が定義されて、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="fbaee-124">各オペランドを必要に応じて変換`Boolean`での操作を実行して`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-124">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="fbaee-125">数値型に結果を割り当てると、Visual Basic 変換から`Boolean`その型にします。</span><span class="sxs-lookup"><span data-stu-id="fbaee-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="fbaee-126">予期しない動作を引き起こすこれ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbaee-126">This could produce unexpected behavior.</span></span> <span data-ttu-id="fbaee-127">たとえば、`5 OrElse 12`結果`–1`に変換される`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-127">For example, `5 OrElse 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fbaee-128">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="fbaee-128">Overloading</span></span>  
 <span data-ttu-id="fbaee-129">[または演算子](../../../visual-basic/language-reference/operators/or-operator.md)と[IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体できます動作を再定義オペランドは、そのクラスの型を持つまたは構造体。</span><span class="sxs-lookup"><span data-stu-id="fbaee-129">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fbaee-130">オーバー ロード、`Or`と`IsTrue`演算子の動作に影響、`OrElse`演算子。</span><span class="sxs-lookup"><span data-stu-id="fbaee-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="fbaee-131">コードで使用する場合`OrElse`クラスまたはオーバー ロードする構造体で`Or`と`IsTrue`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbaee-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="fbaee-132">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-132">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbaee-133">例</span><span class="sxs-lookup"><span data-stu-id="fbaee-133">Example</span></span>  
 <span data-ttu-id="fbaee-134">次の例では、 `OrElse` 2 つの式に対して論理和演算を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="fbaee-135">結果は、`Boolean`値を表す 2 つの式のいずれかが true であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="fbaee-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="fbaee-136">最初の式が場合`True`、2 つ目は評価されません。</span><span class="sxs-lookup"><span data-stu-id="fbaee-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 <span data-ttu-id="fbaee-137">前の例の結果を生成する`True`、 `True`、および`False`それぞれします。</span><span class="sxs-lookup"><span data-stu-id="fbaee-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="fbaee-138">計算に`firstCheck`、1 つ目が既にあるために、2 番目の式は評価されません`True`です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="fbaee-139">計算に 2 番目の式を評価するただし、`secondCheck`です。</span><span class="sxs-lookup"><span data-stu-id="fbaee-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbaee-140">例</span><span class="sxs-lookup"><span data-stu-id="fbaee-140">Example</span></span>  
 <span data-ttu-id="fbaee-141">次の例は、`If`しています.`Then` 2 つのプロシージャ呼び出しを含むステートメント。</span><span class="sxs-lookup"><span data-stu-id="fbaee-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="fbaee-142">最初の呼び出しが返された場合`True`、2 番目の手順は呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="fbaee-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="fbaee-143">これは、ことが予期しない結果に 2 番目の手順は、コードのこのセクションの実行時に常に実行する重要なタスクを実行する場合。</span><span class="sxs-lookup"><span data-stu-id="fbaee-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fbaee-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbaee-144">See Also</span></span>  
 [<span data-ttu-id="fbaee-145">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbaee-145">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="fbaee-146">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="fbaee-146">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="fbaee-147">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="fbaee-147">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="fbaee-148">Or 演算子</span><span class="sxs-lookup"><span data-stu-id="fbaee-148">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)  
 [<span data-ttu-id="fbaee-149">IsTrue 演算子</span><span class="sxs-lookup"><span data-stu-id="fbaee-149">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="fbaee-150">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="fbaee-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
