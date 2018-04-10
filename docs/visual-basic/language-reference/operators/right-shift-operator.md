---
title: '&gt;&gt;演算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="23685-102">&gt;&gt;演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23685-102">&gt;&gt; Operator (Visual Basic)</span></span>
<span data-ttu-id="23685-103">ビット パターンに対して算術右シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="23685-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23685-104">構文</span><span class="sxs-lookup"><span data-stu-id="23685-104">Syntax</span></span>  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="23685-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="23685-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="23685-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="23685-106">Required.</span></span> <span data-ttu-id="23685-107">整数値。</span><span class="sxs-lookup"><span data-stu-id="23685-107">Integral numeric value.</span></span> <span data-ttu-id="23685-108">ビット パターンのシフトの結果。</span><span class="sxs-lookup"><span data-stu-id="23685-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="23685-109">データ型はのと同じ`pattern`です。</span><span class="sxs-lookup"><span data-stu-id="23685-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="23685-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="23685-110">Required.</span></span> <span data-ttu-id="23685-111">整数の数値式です。</span><span class="sxs-lookup"><span data-stu-id="23685-111">Integral numeric expression.</span></span> <span data-ttu-id="23685-112">シフトするビット パターンです。</span><span class="sxs-lookup"><span data-stu-id="23685-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="23685-113">データ型は整数型である必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="23685-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="23685-114">必須です。</span><span class="sxs-lookup"><span data-stu-id="23685-114">Required.</span></span> <span data-ttu-id="23685-115">数値式です。</span><span class="sxs-lookup"><span data-stu-id="23685-115">Numeric expression.</span></span> <span data-ttu-id="23685-116">ビット パターンをシフトするビット数。</span><span class="sxs-lookup"><span data-stu-id="23685-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="23685-117">データ型にする必要があります`Integer`に拡大変換または`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="23685-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23685-118">コメント</span><span class="sxs-lookup"><span data-stu-id="23685-118">Remarks</span></span>  
 <span data-ttu-id="23685-119">算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。</span><span class="sxs-lookup"><span data-stu-id="23685-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="23685-120">算術右シフトの右端のビット位置を超えてシフトは破棄され、左端 (符号) のビットが左側にある空いたビット位置に反映されます。</span><span class="sxs-lookup"><span data-stu-id="23685-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="23685-121">つまり、`pattern`負の値を持つ、空いた位置は、いずれかに設定されます。 それ以外の場合 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="23685-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="23685-122">なおデータ型`Byte`、 `UShort`、 `UInteger`、および`ULong`に反映されるまでの符号ビットがないように、符号がないです。</span><span class="sxs-lookup"><span data-stu-id="23685-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="23685-123">場合`pattern`の任意の符号なし型、空いた位置は常に 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="23685-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="23685-124">Visual Basic マスクの値を防ぐには、結果が保持できるよりも多くのビット シフト、`amount`のデータ型に対応するサイズ マスクを持つ`pattern`します。</span><span class="sxs-lookup"><span data-stu-id="23685-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="23685-125">これらの値のバイナリとシフト数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="23685-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="23685-126">サイズのマスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="23685-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="23685-127">データ型`pattern`</span><span class="sxs-lookup"><span data-stu-id="23685-127">Data type of `pattern`</span></span>|<span data-ttu-id="23685-128">サイズのマスク (10 進数)</span><span class="sxs-lookup"><span data-stu-id="23685-128">Size mask (decimal)</span></span>|<span data-ttu-id="23685-129">サイズのマスク (16 進数)</span><span class="sxs-lookup"><span data-stu-id="23685-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="23685-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="23685-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="23685-131">7</span><span class="sxs-lookup"><span data-stu-id="23685-131">7</span></span>|<span data-ttu-id="23685-132">(& A) H00000007</span><span class="sxs-lookup"><span data-stu-id="23685-132">&H00000007</span></span>|  
|<span data-ttu-id="23685-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="23685-133">`Short`, `UShort`</span></span>|<span data-ttu-id="23685-134">15</span><span class="sxs-lookup"><span data-stu-id="23685-134">15</span></span>|<span data-ttu-id="23685-135">(& A) H0000000F</span><span class="sxs-lookup"><span data-stu-id="23685-135">&H0000000F</span></span>|  
|<span data-ttu-id="23685-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="23685-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="23685-137">31</span><span class="sxs-lookup"><span data-stu-id="23685-137">31</span></span>|<span data-ttu-id="23685-138">(& A) H0000001F</span><span class="sxs-lookup"><span data-stu-id="23685-138">&H0000001F</span></span>|  
|<span data-ttu-id="23685-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="23685-139">`Long`, `ULong`</span></span>|<span data-ttu-id="23685-140">63</span><span class="sxs-lookup"><span data-stu-id="23685-140">63</span></span>|<span data-ttu-id="23685-141">(& A) H0000003F</span><span class="sxs-lookup"><span data-stu-id="23685-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="23685-142">場合`amount`の値は 0 が`result`の値と同一では、`pattern`です。</span><span class="sxs-lookup"><span data-stu-id="23685-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="23685-143">場合`amount`は負の値は符号なしの値として解釈され、適切なサイズ マスクとマスクします。</span><span class="sxs-lookup"><span data-stu-id="23685-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="23685-144">算術シフトでは、オーバーフロー例外が生成されません。</span><span class="sxs-lookup"><span data-stu-id="23685-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="23685-145">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="23685-145">Overloading</span></span>  
 <span data-ttu-id="23685-146">`>>`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="23685-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="23685-147">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="23685-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="23685-148">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="23685-148">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23685-149">例</span><span class="sxs-lookup"><span data-stu-id="23685-149">Example</span></span>  
 <span data-ttu-id="23685-150">次の例では、`>>`整数値に対して算術右シフトを実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="23685-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="23685-151">結果は、常に同じデータ移動されている式の型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="23685-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 <span data-ttu-id="23685-152">前の例の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="23685-152">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="23685-153">`result1`2560 (0000 1010 0000 0000)。</span><span class="sxs-lookup"><span data-stu-id="23685-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
-   <span data-ttu-id="23685-154">`result2`160 (0000 0000 1010 0000)。</span><span class="sxs-lookup"><span data-stu-id="23685-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
-   <span data-ttu-id="23685-155">`result3`2 (0000 0000 0000 0010) です。</span><span class="sxs-lookup"><span data-stu-id="23685-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
-   <span data-ttu-id="23685-156">`result4`640 (0000 0010 1000 0000)。</span><span class="sxs-lookup"><span data-stu-id="23685-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
-   <span data-ttu-id="23685-157">`result5`0 (シフト 15 桁) です。</span><span class="sxs-lookup"><span data-stu-id="23685-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="23685-158">Shift キーを押し、金額`result4`18 として計算されますが 2 と等しいと 15 です。</span><span class="sxs-lookup"><span data-stu-id="23685-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="23685-159">次の例では、負の値に算術シフトを示します。</span><span class="sxs-lookup"><span data-stu-id="23685-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 <span data-ttu-id="23685-160">前の例の結果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="23685-160">The results of the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="23685-161">`negresult1`-512 (1111 1110 0000 0000) は、します。</span><span class="sxs-lookup"><span data-stu-id="23685-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
-   <span data-ttu-id="23685-162">`negresult2`-1 (符号ビットが反映されますです)。</span><span class="sxs-lookup"><span data-stu-id="23685-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23685-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="23685-163">See Also</span></span>  
 [<span data-ttu-id="23685-164">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="23685-164">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="23685-165">代入演算子</span><span class="sxs-lookup"><span data-stu-id="23685-165">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="23685-166">>>= 演算子</span><span class="sxs-lookup"><span data-stu-id="23685-166">>>= Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [<span data-ttu-id="23685-167">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="23685-167">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="23685-168">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="23685-168">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="23685-169">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="23685-169">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
