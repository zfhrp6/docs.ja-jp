---
title: "引数値渡しと参照渡し (Visual Basic) |Microsoft ドキュメント"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 44107171d6f24e22614788470c65cf7ad8d28640
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="67ea1-102">引数の値渡しと参照渡し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67ea1-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="67ea1-103">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、プロシージャに引数を渡すことができます*値によって*または*参照によって*します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="67ea1-104">これと呼ばれますが、*渡す機能*、し、プロシージャが呼び出し元のコードで引数を基になるプログラミングの要素を変更するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="67ea1-105">プロシージャの宣言では、各パラメーターの引き渡し方法を決定を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="67ea1-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="67ea1-106">相違点</span><span class="sxs-lookup"><span data-stu-id="67ea1-106">Distinctions</span></span>  
 <span data-ttu-id="67ea1-107">プロシージャに引数を渡す場合は、相互にやり取りするいくつかの違いに注意してください。</span><span class="sxs-lookup"><span data-stu-id="67ea1-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="67ea1-108">基になるプログラミング要素は、変更可能または変更できないかどうか</span><span class="sxs-lookup"><span data-stu-id="67ea1-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="67ea1-109">引数自体が変更可能または変更不可能なのかどうか</span><span class="sxs-lookup"><span data-stu-id="67ea1-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="67ea1-110">値渡しまたは参照渡しの引数が渡されるかどうか</span><span class="sxs-lookup"><span data-stu-id="67ea1-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="67ea1-111">引数のデータ型は、値型または参照型かどうか</span><span class="sxs-lookup"><span data-stu-id="67ea1-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="67ea1-112">詳細については、次を参照してください。[変更間の相違点と変更できない引数](./differences-between-modifiable-and-nonmodifiable-arguments.md)と[の相違点の間の値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="67ea1-113">渡す機能の選択</span><span class="sxs-lookup"><span data-stu-id="67ea1-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="67ea1-114">慎重に各引数の引き渡し方法を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67ea1-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="67ea1-115">**保護**します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-115">**Protection**.</span></span> <span data-ttu-id="67ea1-116">引数を渡す方法を選択すると、最も重要な条件を変更する変数を呼び出すことのリスクです。</span><span class="sxs-lookup"><span data-stu-id="67ea1-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="67ea1-117">引数を渡す場合の利点`ByRef`はプロシージャがその引数を通じて呼び出し元コードに値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="67ea1-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="67ea1-118">引数を渡す場合の利点`ByVal`からプロシージャによって変更されている変数を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="67ea1-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="67ea1-119">**パフォーマンス**します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-119">**Performance**.</span></span> <span data-ttu-id="67ea1-120">引数渡しの方法が、コードのパフォーマンスに影響を与えることができますが、違いは一般にごくわずかです。</span><span class="sxs-lookup"><span data-stu-id="67ea1-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="67ea1-121">唯一の例外が渡される値型`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="67ea1-122">この場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]引数のデータ全体の内容をコピーします。</span><span class="sxs-lookup"><span data-stu-id="67ea1-122">In this case, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the entire data contents of the argument.</span></span> <span data-ttu-id="67ea1-123">そのため、構造体などの大きな値型場合がこれを渡す方が効率的`ByRef`します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="67ea1-124">参照型でデータへのポインターにのみ、コピーした (4 バイト プラットフォームでは 32 ビット、64 ビット プラットフォームでは 8 バイト) です。</span><span class="sxs-lookup"><span data-stu-id="67ea1-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="67ea1-125">そのため、型の引数を渡すことができます`String`または`Object`パフォーマンスを損なわずに値渡しされます。</span><span class="sxs-lookup"><span data-stu-id="67ea1-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="67ea1-126">引数渡しの方法の決定</span><span class="sxs-lookup"><span data-stu-id="67ea1-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="67ea1-127">プロシージャの宣言では、各パラメーターの引き渡し方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="67ea1-128">呼び出し元のコードを上書きできません、`ByVal`メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="67ea1-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="67ea1-129">パラメーターが宣言されている場合`ByRef`、呼び出し元のコードにするメカニズムを強制できます`ByVal`引数の名前を呼び出しでは、かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="67ea1-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="67ea1-130">詳細については、次を参照してください。[方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="67ea1-131">既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。</span><span class="sxs-lookup"><span data-stu-id="67ea1-131">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="67ea1-132">引数の値渡しする場合</span><span class="sxs-lookup"><span data-stu-id="67ea1-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="67ea1-133">引数の基になる呼び出し元のコード要素が変更不可能な要素の場合は、対応するパラメーターを宣言[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="67ea1-134">変更不可能な要素の値に変更できるコードはありません。</span><span class="sxs-lookup"><span data-stu-id="67ea1-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="67ea1-135">基になる要素が変更可能をその値を変更できるようにする手順をしたくない場合に、パラメーター宣言`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="67ea1-136">呼び出し元のコードだけでは、値によって渡される変更可能な要素の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="67ea1-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="67ea1-137">引数は参照渡しする場合</span><span class="sxs-lookup"><span data-stu-id="67ea1-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="67ea1-138">プロシージャの呼び出し元のコードで基になる要素を変更する必要が本当の場合は、対応するパラメーターを宣言[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="67ea1-139">コードの適切な実行は、呼び出し元のコード内の基になる要素を変更するプロシージャに依存している場合に、パラメーター宣言`ByRef`します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="67ea1-140">値で渡す場合、または呼び出し元のコードをオーバーライドする場合、`ByRef`渡す引数をかっこで囲んで機能プロシージャの呼び出しが予期しない結果を生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="67ea1-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ea1-141">例</span><span class="sxs-lookup"><span data-stu-id="67ea1-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="67ea1-142">説明</span><span class="sxs-lookup"><span data-stu-id="67ea1-142">Description</span></span>  
 <span data-ttu-id="67ea1-143">次の例では、引数を値渡しする場合と参照渡しする場合を示します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="67ea1-144">プロシージャ`Calculate`が両方とも、`ByVal`と`ByRef`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="67ea1-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="67ea1-145">金利、指定された`rate`、および合計金額、 `debt`、プロシージャの作業は、新しい値を計算する`debt`の元の値を金利を適用した結果は`debt`です。</span><span class="sxs-lookup"><span data-stu-id="67ea1-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="67ea1-146">`debt`は、`ByRef`パラメーター、呼び出し元のコードに対応する引数の値に新しい合計が反映されます`debt`します。</span><span class="sxs-lookup"><span data-stu-id="67ea1-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="67ea1-147">パラメーター`rate`は、`ByVal`パラメーターのため`Calculate`の値を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="67ea1-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="67ea1-148">コード</span><span class="sxs-lookup"><span data-stu-id="67ea1-148">Code</span></span>  
 <span data-ttu-id="67ea1-149">[!code-vb[VbVbcnProcedures #&74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="67ea1-149">[!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ea1-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="67ea1-150">See Also</span></span>  
 <span data-ttu-id="67ea1-151">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-151">[Procedures](./index.md) </span></span>  
<span data-ttu-id="67ea1-152"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="67ea1-153"> [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-153"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="67ea1-154"> [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-154"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="67ea1-155"> [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="67ea1-156"> [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="67ea1-157"> [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="67ea1-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="67ea1-158"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="67ea1-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
