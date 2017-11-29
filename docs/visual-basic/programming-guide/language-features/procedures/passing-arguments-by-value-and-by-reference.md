---
title: "引数の値渡しと参照渡し (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752c0c8e90cafe457cbd5d684bc984a1ea4632ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="afdbb-102">引数の値渡しと参照渡し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afdbb-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="afdbb-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]、プロシージャに引数を渡すことができます*値によって*または*参照によって*です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="afdbb-104">これと呼ばれますが、*渡し*プロシージャが呼び出し元のコードで引数の基になるプログラミング要素を変更できるかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="afdbb-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="afdbb-105">プロシージャ宣言では、各パラメーターの引き渡し方法を決定を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="afdbb-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="afdbb-106">相違点</span><span class="sxs-lookup"><span data-stu-id="afdbb-106">Distinctions</span></span>  
 <span data-ttu-id="afdbb-107">プロシージャに引数を渡すときの相互作用をいくつかの違いに注意してください。</span><span class="sxs-lookup"><span data-stu-id="afdbb-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="afdbb-108">基になるプログラミング要素が変更可能または変更不可能なのかどうか</span><span class="sxs-lookup"><span data-stu-id="afdbb-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="afdbb-109">引数自体が変更可能または変更不可能なのかどうか</span><span class="sxs-lookup"><span data-stu-id="afdbb-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="afdbb-110">値渡しまたは参照渡しの引数が渡されるかどうか</span><span class="sxs-lookup"><span data-stu-id="afdbb-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="afdbb-111">引数のデータ型は、値型または参照型かどうか</span><span class="sxs-lookup"><span data-stu-id="afdbb-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="afdbb-112">詳細については、次を参照してください。[の相違点の間で変更可能なと変更できない引数](./differences-between-modifiable-and-nonmodifiable-arguments.md)と[の相違点の間で値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="afdbb-113">引き渡し方法の選択</span><span class="sxs-lookup"><span data-stu-id="afdbb-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="afdbb-114">各引数の慎重に引き渡し方法を選択してください。</span><span class="sxs-lookup"><span data-stu-id="afdbb-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="afdbb-115">**保護**です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-115">**Protection**.</span></span> <span data-ttu-id="afdbb-116">引数を渡す方法を選択すると、最も重要な条件を変更する変数を呼び出すことの公開です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="afdbb-117">引数を渡す場合の利点`ByRef`は、プロシージャがその引数を呼び出し元のコードに値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="afdbb-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="afdbb-118">引数を渡す場合の利点`ByVal`プロシージャによって変更されない変数を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="afdbb-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="afdbb-119">**パフォーマンス**です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-119">**Performance**.</span></span> <span data-ttu-id="afdbb-120">引き渡し方法が、コードのパフォーマンスに影響を与えることができますが、違いは通常意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="afdbb-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="afdbb-121">1 つの例外は、渡された値の型`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="afdbb-122">この場合、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]引数のデータ全体の内容をコピーします。</span><span class="sxs-lookup"><span data-stu-id="afdbb-122">In this case, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] copies the entire data contents of the argument.</span></span> <span data-ttu-id="afdbb-123">そのため、構造体などの大きな値型のだということを渡す方が効率的`ByRef`です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="afdbb-124">参照型の場合は、データへのポインターのみ、コピーした (4 バイト 32 ビット プラットフォームでは、64 ビット プラットフォームでは 8 バイト) です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="afdbb-125">そのため、型の引数を渡すことができます`String`または`Object`パフォーマンスに悪影響を与えない値。</span><span class="sxs-lookup"><span data-stu-id="afdbb-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="afdbb-126">引き渡し方法の決定</span><span class="sxs-lookup"><span data-stu-id="afdbb-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="afdbb-127">プロシージャ宣言では、各パラメーターの引き渡し方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="afdbb-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="afdbb-128">呼び出し元のコードがオーバーライドすることはできません、`ByVal`メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="afdbb-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="afdbb-129">パラメーターが宣言されている場合`ByRef`、呼び出し元のコードにするためのメカニズムを強制できます`ByVal`を呼び出しでは、かっこで囲み、引数名によってです。</span><span class="sxs-lookup"><span data-stu-id="afdbb-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="afdbb-130">詳細については、次を参照してください。[する方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="afdbb-131">既定で[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]は引数の値渡しします。</span><span class="sxs-lookup"><span data-stu-id="afdbb-131">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="afdbb-132">引数の値渡しする場合</span><span class="sxs-lookup"><span data-stu-id="afdbb-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="afdbb-133">引数の基になる呼び出し元のコード要素が変更できない要素の場合は、対応するパラメーターを宣言[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="afdbb-134">変更不可能な要素の値は、コードでは変更されません。</span><span class="sxs-lookup"><span data-stu-id="afdbb-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="afdbb-135">基になる要素は変更できますが、その値を変更できるようにする手順をしたくない場合、パラメーターを宣言`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="afdbb-136">呼び出し元のコードだけでは、値渡し変更可能な要素の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="afdbb-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="afdbb-137">参照引数を渡す場合</span><span class="sxs-lookup"><span data-stu-id="afdbb-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="afdbb-138">プロシージャに呼び出し元のコード内の基になる要素を変更する正規品である必要がある場合は、対応するパラメーターを宣言[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="afdbb-139">正しいコードの実行は、呼び出し元のコード内の基になる要素を変更するプロシージャに依存している場合に、パラメーター宣言`ByRef`です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="afdbb-140">値で渡す場合、または呼び出し元のコードをオーバーライドする場合、`ByRef`引数をかっこで囲んで、プロシージャの呼び出しが予期しない結果を生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afdbb-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afdbb-141">例</span><span class="sxs-lookup"><span data-stu-id="afdbb-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="afdbb-142">説明</span><span class="sxs-lookup"><span data-stu-id="afdbb-142">Description</span></span>  
 <span data-ttu-id="afdbb-143">引数の値渡しと参照渡しする次の例を示しています。</span><span class="sxs-lookup"><span data-stu-id="afdbb-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="afdbb-144">プロシージャ`Calculate`両方を持つ、`ByVal`と`ByRef`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="afdbb-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="afdbb-145">利率、指定された`rate`と合計金額、 `debt`、プロシージャのタスクはの新しい値を計算する`debt`の元の値を利率を適用した結果は`debt`します。</span><span class="sxs-lookup"><span data-stu-id="afdbb-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="afdbb-146">`debt`は、`ByRef`パラメーター、呼び出し元のコードに対応する引数の値で、新しい合計を反映`debt`です。</span><span class="sxs-lookup"><span data-stu-id="afdbb-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="afdbb-147">パラメーター`rate`は、`ByVal`パラメーターのため`Calculate`その値を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="afdbb-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="afdbb-148">コード</span><span class="sxs-lookup"><span data-stu-id="afdbb-148">Code</span></span>  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="afdbb-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="afdbb-149">See Also</span></span>  
 [<span data-ttu-id="afdbb-150">手順</span><span class="sxs-lookup"><span data-stu-id="afdbb-150">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="afdbb-151">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="afdbb-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="afdbb-152">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="afdbb-152">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="afdbb-153">方法: プロシージャ引数の値を変更する</span><span class="sxs-lookup"><span data-stu-id="afdbb-153">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="afdbb-154">方法: プロシージャ引数の値が変化しないようにする</span><span class="sxs-lookup"><span data-stu-id="afdbb-154">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="afdbb-155">方法: 引数の値渡しを強制する</span><span class="sxs-lookup"><span data-stu-id="afdbb-155">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="afdbb-156">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="afdbb-156">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="afdbb-157">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="afdbb-157">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
