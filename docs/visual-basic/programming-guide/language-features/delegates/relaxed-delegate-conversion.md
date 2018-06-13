---
title: 厳密でないデリゲート変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: c4a41bf74716a6ea7d3c1139651834acccf27657
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650830"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="3b16a-102">厳密でないデリゲート変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b16a-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="3b16a-103">厳密でないデリゲート変換を使用すると、サブと関数は、それぞれの署名が同一ではない場合でも、ハンドラーまたはデリゲートを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="3b16a-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="3b16a-104">そのため、デリゲートへのバインディングは、メソッドの呼び出しを既に許可されているバインディングで一貫性のあるになります。</span><span class="sxs-lookup"><span data-stu-id="3b16a-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="3b16a-105">パラメーターと戻り値の型</span><span class="sxs-lookup"><span data-stu-id="3b16a-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="3b16a-106">正確なシグネチャの一致の代わりに厳密でない変換が必要です、次の条件が満たされているときに`Option Strict`に設定されている`On`:</span><span class="sxs-lookup"><span data-stu-id="3b16a-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="3b16a-107">各デリゲート パラメーターのデータ型から、対応する関数のパラメーター、割り当て済みのデータ型への拡大変換が存在する必要がありますまたは`Sub`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="3b16a-108">次の例では、デリゲート`Del1`1 つのパラメーターを持ち、`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="3b16a-109">パラメーター`m`式に割り当てられているラムダからの拡大変換がある対象のデータ型である必要があります`Integer`など`Long`または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="3b16a-110">縮小変換が許可される場合にのみ`Option Strict`に設定されている`Off`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="3b16a-111">割り当てられている関数の戻り値の型から反対方向に拡大変換が存在する必要がありますまたは`Sub`デリゲートの戻り値の型にします。</span><span class="sxs-lookup"><span data-stu-id="3b16a-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="3b16a-112">次の例では、各割り当てられているラムダ式の本体必要がありますを拡大するデータ型に評価される`Integer`戻り値の型のため`del1`は`Integer`します。</span><span class="sxs-lookup"><span data-stu-id="3b16a-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="3b16a-113">場合`Option Strict`に設定されている`Off`では、双方向でが削除されて制限を拡大します。</span><span class="sxs-lookup"><span data-stu-id="3b16a-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="3b16a-114">パラメーターの仕様を省略すること</span><span class="sxs-lookup"><span data-stu-id="3b16a-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="3b16a-115">厳密でないデリゲートでは、割り当てられているメソッドのパラメーターの仕様を完全に省略することができます。</span><span class="sxs-lookup"><span data-stu-id="3b16a-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="3b16a-116">いくつかのパラメーターを指定およびその他を省略できませんに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3b16a-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="3b16a-117">パラメーターを省略する機能は、いくつかの複雑なパラメーターが含まれて、イベント ハンドラーを定義するなどの状況で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3b16a-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="3b16a-118">一部のイベント ハンドラーの引数は使用されません。</span><span class="sxs-lookup"><span data-stu-id="3b16a-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="3b16a-119">代わりに、ハンドラーをイベントが登録し、その引数を無視コントロールの状態に直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="3b16a-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="3b16a-120">厳密でないデリゲートを使用するときに何の結果もあいまいさは、このような宣言の引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="3b16a-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="3b16a-121">次の例では、完全に指定されたメソッドで`OnClick`として書き直すことができます`RelaxedOnClick`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="3b16a-122">AddressOf 例</span><span class="sxs-lookup"><span data-stu-id="3b16a-122">AddressOf Examples</span></span>  
 <span data-ttu-id="3b16a-123">ラムダ式は、型の関係を簡単に参照して、前の例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b16a-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="3b16a-124">ただし、同じリラクゼーションを使用するデリゲートの割り当て用に許可されて`AddressOf`、 `Handles`、または`AddHandler`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="3b16a-125">次の例では、次のように機能します。 `f1`、 `f2`、 `f3`、および`f4`すべてに代入できます`Del1`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="3b16a-126">次の例は、有効な場合にのみ`Option Strict`に設定されている`Off`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="3b16a-127">関数の戻り値を削除します。</span><span class="sxs-lookup"><span data-stu-id="3b16a-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="3b16a-128">厳密でないデリゲート変換は、機能を割り当てることができます、`Sub`デリゲート、効果的に関数の戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3b16a-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="3b16a-129">ただし、割り当てることはできません、`Sub`を関数デリゲート。</span><span class="sxs-lookup"><span data-stu-id="3b16a-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="3b16a-130">次の例では、関数のアドレスで`doubler`に割り当てられている`Sub`委任`Del3`です。</span><span class="sxs-lookup"><span data-stu-id="3b16a-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3b16a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b16a-131">See Also</span></span>  
 [<span data-ttu-id="3b16a-132">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="3b16a-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="3b16a-133">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="3b16a-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="3b16a-134">デリゲート</span><span class="sxs-lookup"><span data-stu-id="3b16a-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 <span data-ttu-id="3b16a-135">方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="3b16a-135">[How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span></span>  
 [<span data-ttu-id="3b16a-136">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="3b16a-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3b16a-137">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="3b16a-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
