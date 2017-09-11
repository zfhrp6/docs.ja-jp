---
title: "デリゲート変換 (Visual Basic)、緩和 |Microsoft ドキュメント"
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
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
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
ms.openlocfilehash: 016c808145f7faba26a288cd5075f10d7f5279d5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="04d0e-102">厳密でないデリゲート変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04d0e-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="04d0e-103">厳密でないデリゲート変換を使用すると、そのシグネチャが同一でない場合でも、デリゲートやハンドラーにサブルーチンや関数を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="04d0e-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="04d0e-104">そのため、デリゲートへのバインディングは、メソッド呼び出しで既に認められているバインディングと一致になります。</span><span class="sxs-lookup"><span data-stu-id="04d0e-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="04d0e-105">パラメーターと戻り値の型</span><span class="sxs-lookup"><span data-stu-id="04d0e-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="04d0e-106">正確に一致するシグネチャの代わりに厳密でない変換が必要です、次の条件が満たされているときに`Option Strict`に設定されている`On`:</span><span class="sxs-lookup"><span data-stu-id="04d0e-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="04d0e-107">デリゲートの各パラメーターのデータ型から割り当てられている関数の対応するパラメーターのデータ型への拡大変換が存在する必要がありますか`Sub`します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="04d0e-108">次の例では、デリゲート`Del1`1 つのパラメーター、`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="04d0e-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="04d0e-109">パラメーター`m`で割り当てられているラムダ式がありますがから拡大変換が存在するデータ型`Integer`など`Long`または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="04d0e-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     <span data-ttu-id="04d0e-110">[!code-vb[VbVbalrRelaxedDelegates&#1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-110">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
     <span data-ttu-id="04d0e-111">[!code-vb[VbVbalrRelaxedDelegates&#2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-111">[!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span></span>  
  
     <span data-ttu-id="04d0e-112">縮小変換が許可される場合にのみ`Option Strict`に設定されている`Off`します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-112">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     <span data-ttu-id="04d0e-113">[!code-vb[VbVbalrRelaxedDelegates&#8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-113">[!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span></span>  
  
-   <span data-ttu-id="04d0e-114">割り当てられている関数の戻り値の型から反対方向に拡大変換が存在する必要がありますか`Sub`デリゲートの戻り値の型にします。</span><span class="sxs-lookup"><span data-stu-id="04d0e-114">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="04d0e-115">次の例については、各割り当てられているラムダ式の本体を拡大変換後のデータ型に評価する必要があります`Integer`戻り値の型のため`del1`は`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="04d0e-115">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     <span data-ttu-id="04d0e-116">[!code-vb[VbVbalrRelaxedDelegates&#3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-116">[!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-117">場合`Option Strict`に設定されている`Off`、双方向でが削除されて制限を拡大します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-117">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 <span data-ttu-id="04d0e-118">[!code-vb[VbVbalrRelaxedDelegates&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-118">[!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span></span>  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="04d0e-119">パラメーターの指定を省略すること</span><span class="sxs-lookup"><span data-stu-id="04d0e-119">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="04d0e-120">厳密でないデリゲートを使用して、割り当てられているメソッドのパラメーターの仕様を完全に省略することもします。</span><span class="sxs-lookup"><span data-stu-id="04d0e-120">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 <span data-ttu-id="04d0e-121">[!code-vb[VbVbalrRelaxedDelegates&#5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-121">[!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-122">[!code-vb[VbVbalrRelaxedDelegates&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-122">[!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-123">いくつかのパラメーターを指定し、他のユーザーを省略できないに注意してください。</span><span class="sxs-lookup"><span data-stu-id="04d0e-123">Note that you cannot specify some parameters and omit others.</span></span>  
  
 <span data-ttu-id="04d0e-124">[!code-vb[VbVbalrRelaxedDelegates&#15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-124">[!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-125">パラメーターを省略する機能は、いくつかの複雑なパラメーターが関係している、イベント ハンドラーを定義するような状況で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="04d0e-125">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="04d0e-126">いくつかのイベント ハンドラーの引数は使用されません。</span><span class="sxs-lookup"><span data-stu-id="04d0e-126">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="04d0e-127">代わりに、ハンドラーは、イベントが登録されているし、する引数を無視コントロールの状態を直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="04d0e-127">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="04d0e-128">厳密でないデリゲートを使用すると、ときに何のあいまいさの結果は、このような宣言の引数を省略することができます。</span><span class="sxs-lookup"><span data-stu-id="04d0e-128">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="04d0e-129">次の例では、完全に指定したメソッドで`OnClick`として書き直すことが`RelaxedOnClick`です。</span><span class="sxs-lookup"><span data-stu-id="04d0e-129">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="04d0e-130">AddressOf 例</span><span class="sxs-lookup"><span data-stu-id="04d0e-130">AddressOf Examples</span></span>  
 <span data-ttu-id="04d0e-131">ラムダ式は、表示する型の関係を簡単に、前の例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="04d0e-131">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="04d0e-132">ただし、同じリラクゼーションは許可されますを使用するデリゲートの割り当ての`AddressOf`、 `Handles`、または`AddHandler`です。</span><span class="sxs-lookup"><span data-stu-id="04d0e-132">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="04d0e-133">次の例では、機能`f1`、 `f2`、 `f3`、および`f4`に割り当てられるすべて`Del1`です。</span><span class="sxs-lookup"><span data-stu-id="04d0e-133">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 <span data-ttu-id="04d0e-134">[!code-vb[VbVbalrRelaxedDelegates&#1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-134">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-135">[!code-vb[VbVbalrRelaxedDelegates&#7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-135">[!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-136">[!code-vb[VbVbalrRelaxedDelegates&#9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-136">[!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-137">次の例は、有効な場合にのみ`Option Strict`に設定されている`Off`します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-137">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 <span data-ttu-id="04d0e-138">[!code-vb[VbVbalrRelaxedDelegates&#14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-138">[!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span></span>  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="04d0e-139">関数の戻り値を削除します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-139">Dropping Function Returns</span></span>  
 <span data-ttu-id="04d0e-140">厳密でないデリゲート変換を使用すると、機能を割り当てる、`Sub`デリゲート、事実上、関数の戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-140">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="04d0e-141">ただし、割り当てることはできません、`Sub`を関数デリゲート。</span><span class="sxs-lookup"><span data-stu-id="04d0e-141">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="04d0e-142">次の例では、関数のアドレスで`doubler`に割り当てられている`Sub`委任`Del3`します。</span><span class="sxs-lookup"><span data-stu-id="04d0e-142">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 <span data-ttu-id="04d0e-143">[!code-vb[VbVbalrRelaxedDelegates&#10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-143">[!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span></span>  
  
 <span data-ttu-id="04d0e-144">[!code-vb[VbVbalrRelaxedDelegates&#11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="04d0e-144">[!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d0e-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="04d0e-145">See Also</span></span>  
 <span data-ttu-id="04d0e-146">[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="04d0e-146">[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="04d0e-147"> [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="04d0e-147"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="04d0e-148"> [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="04d0e-148"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="04d0e-149"> [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="04d0e-149"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="04d0e-150"> [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="04d0e-150"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="04d0e-151"> [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="04d0e-151"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
