---
title: '&lt;&lt; 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: bdec015309526aeac2499bc7b459b6ccab6f1e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604459"
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="30b59-102">&lt;&lt; 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30b59-102">&lt;&lt; Operator (Visual Basic)</span></span>
<span data-ttu-id="30b59-103">ビット パターンに対して算術左シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="30b59-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b59-104">構文</span><span class="sxs-lookup"><span data-stu-id="30b59-104">Syntax</span></span>  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="30b59-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="30b59-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="30b59-106">必須。</span><span class="sxs-lookup"><span data-stu-id="30b59-106">Required.</span></span> <span data-ttu-id="30b59-107">整数値。</span><span class="sxs-lookup"><span data-stu-id="30b59-107">Integral numeric value.</span></span> <span data-ttu-id="30b59-108">ビット パターンのシフトの結果。</span><span class="sxs-lookup"><span data-stu-id="30b59-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="30b59-109">データ型はのと同じ`pattern`です。</span><span class="sxs-lookup"><span data-stu-id="30b59-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="30b59-110">必須。</span><span class="sxs-lookup"><span data-stu-id="30b59-110">Required.</span></span> <span data-ttu-id="30b59-111">整数の数値式です。</span><span class="sxs-lookup"><span data-stu-id="30b59-111">Integral numeric expression.</span></span> <span data-ttu-id="30b59-112">シフトするビット パターンです。</span><span class="sxs-lookup"><span data-stu-id="30b59-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="30b59-113">データ型は整数型である必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="30b59-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="30b59-114">必須。</span><span class="sxs-lookup"><span data-stu-id="30b59-114">Required.</span></span> <span data-ttu-id="30b59-115">数値式です。</span><span class="sxs-lookup"><span data-stu-id="30b59-115">Numeric expression.</span></span> <span data-ttu-id="30b59-116">ビット パターンをシフトするビット数。</span><span class="sxs-lookup"><span data-stu-id="30b59-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="30b59-117">データ型にする必要があります`Integer`に拡大変換または`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="30b59-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b59-118">コメント</span><span class="sxs-lookup"><span data-stu-id="30b59-118">Remarks</span></span>  
 <span data-ttu-id="30b59-119">算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。</span><span class="sxs-lookup"><span data-stu-id="30b59-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="30b59-120">算術左シフト、結果のデータ型の範囲を超えてシフトは破棄され、右側の空いたビット位置は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="30b59-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="30b59-121">Visual Basic は、シフトの結果を保持できる以上のビット数を防ぐためには、値をマスク`amount`のデータ型に対応するサイズ マスクを持つ`pattern`します。</span><span class="sxs-lookup"><span data-stu-id="30b59-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="30b59-122">これらの値のバイナリとシフト数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="30b59-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="30b59-123">サイズのマスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="30b59-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="30b59-124">データ型 `pattern`</span><span class="sxs-lookup"><span data-stu-id="30b59-124">Data type of `pattern`</span></span>|<span data-ttu-id="30b59-125">サイズのマスク (10 進数)</span><span class="sxs-lookup"><span data-stu-id="30b59-125">Size mask (decimal)</span></span>|<span data-ttu-id="30b59-126">サイズのマスク (16 進数)</span><span class="sxs-lookup"><span data-stu-id="30b59-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="30b59-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="30b59-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="30b59-128">7</span><span class="sxs-lookup"><span data-stu-id="30b59-128">7</span></span>|<span data-ttu-id="30b59-129">(&AMP; A) H00000007</span><span class="sxs-lookup"><span data-stu-id="30b59-129">&H00000007</span></span>|  
|<span data-ttu-id="30b59-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="30b59-130">`Short`, `UShort`</span></span>|<span data-ttu-id="30b59-131">16</span><span class="sxs-lookup"><span data-stu-id="30b59-131">15</span></span>|<span data-ttu-id="30b59-132">(&AMP; A) H0000000F</span><span class="sxs-lookup"><span data-stu-id="30b59-132">&H0000000F</span></span>|  
|<span data-ttu-id="30b59-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="30b59-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="30b59-134">31</span><span class="sxs-lookup"><span data-stu-id="30b59-134">31</span></span>|<span data-ttu-id="30b59-135">(&AMP; A) H0000001F</span><span class="sxs-lookup"><span data-stu-id="30b59-135">&H0000001F</span></span>|  
|<span data-ttu-id="30b59-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="30b59-136">`Long`, `ULong`</span></span>|<span data-ttu-id="30b59-137">63</span><span class="sxs-lookup"><span data-stu-id="30b59-137">63</span></span>|<span data-ttu-id="30b59-138">(&AMP; A) H0000003F</span><span class="sxs-lookup"><span data-stu-id="30b59-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="30b59-139">場合`amount`の値は 0 が`result`の値と同一では、`pattern`です。</span><span class="sxs-lookup"><span data-stu-id="30b59-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="30b59-140">場合`amount`は負の値は符号なしの値として解釈され、適切なサイズ マスクとマスクします。</span><span class="sxs-lookup"><span data-stu-id="30b59-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="30b59-141">算術シフトでは、オーバーフロー例外が生成されません。</span><span class="sxs-lookup"><span data-stu-id="30b59-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30b59-142">`<<`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="30b59-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="30b59-143">コードは、このようなクラスまたは構造体で、この演算子を使用する場合、再定義された動作を理解していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="30b59-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="30b59-144">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="30b59-144">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30b59-145">例</span><span class="sxs-lookup"><span data-stu-id="30b59-145">Example</span></span>  
 <span data-ttu-id="30b59-146">次の例では、`<<`整数値の算術左シフトを実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="30b59-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="30b59-147">結果は、常に同じデータ移動されている式の型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="30b59-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 <span data-ttu-id="30b59-148">前の例の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="30b59-148">The results of the previous example are as follows:</span></span>  
  
-   <span data-ttu-id="30b59-149">`result1` 192 (0000 0000 1100 0000)。</span><span class="sxs-lookup"><span data-stu-id="30b59-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
-   <span data-ttu-id="30b59-150">`result2` 3072 (0000 1100 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="30b59-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
-   <span data-ttu-id="30b59-151">`result3` -32768 (1000 0000 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="30b59-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
-   <span data-ttu-id="30b59-152">`result4` 384 (0000 0001 1000 0000) は、します。</span><span class="sxs-lookup"><span data-stu-id="30b59-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
-   <span data-ttu-id="30b59-153">`result5` 0 (シフト 15 桁) です。</span><span class="sxs-lookup"><span data-stu-id="30b59-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="30b59-154">Shift キーを押し、金額`result4`17 として計算されますが 1 に等しいと 15 です。</span><span class="sxs-lookup"><span data-stu-id="30b59-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b59-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="30b59-155">See Also</span></span>  
 [<span data-ttu-id="30b59-156">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="30b59-156">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="30b59-157">代入演算子</span><span class="sxs-lookup"><span data-stu-id="30b59-157">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="30b59-158"><<= 演算子</span><span class="sxs-lookup"><span data-stu-id="30b59-158"><<= Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [<span data-ttu-id="30b59-159">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="30b59-159">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="30b59-160">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="30b59-160">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="30b59-161">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="30b59-161">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
