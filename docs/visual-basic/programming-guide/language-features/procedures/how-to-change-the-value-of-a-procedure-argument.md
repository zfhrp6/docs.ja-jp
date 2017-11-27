---
title: "方法: プロシージャ引数の値を変更する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba23c8f0b4b0b6e751546019af902a6305b9ef53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="0b30a-102">方法: プロシージャ引数の値を変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b30a-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="0b30a-103">プロシージャを呼び出すときに指定する各引数はプロシージャで定義されているパラメーターのいずれかに対応します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="0b30a-104">場合によっては、プロシージャのコードは、呼び出し元のコードで引数の基になる値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0b30a-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="0b30a-105">それ以外の場合に、プロシージャは、引数のローカル コピーのみを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0b30a-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="0b30a-106">プロシージャを呼び出す場合[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]が渡される引数のすべてのローカル コピーを作成[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b30a-106">When you call the procedure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="0b30a-107">渡された各引数に対して[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロシージャのコードに呼び出し元のコードで引数の基になるプログラミング要素への直接参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="0b30a-108">呼び出し元のコードに基になる要素が変更可能な引数が渡される場合`ByRef`、プロシージャ コードは、直接的な参照を使用して、呼び出し元のコード内の要素の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="0b30a-109">基になる値を変更します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="0b30a-110">呼び出し元のコードでプロシージャ引数の基になる値を変更するには</span><span class="sxs-lookup"><span data-stu-id="0b30a-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="0b30a-111">プロシージャ宣言で指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引数に対応するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="0b30a-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="0b30a-112">呼び出し元のコードでは、変更可能なプログラミング要素を引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="0b30a-113">呼び出し元のコードで囲まないでください引数、引数リストのかっこでします。</span><span class="sxs-lookup"><span data-stu-id="0b30a-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="0b30a-114">プロシージャのコードでは、呼び出し元のコードに基になる要素に値を代入するのにパラメーターの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="0b30a-115">例を参照してください。 詳しくは、デモについてはします。</span><span class="sxs-lookup"><span data-stu-id="0b30a-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="0b30a-116">ローカル コピーを変更します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-116">Changing Local Copies</span></span>  
 <span data-ttu-id="0b30a-117">呼び出し元のコードに基になる要素が、変更不可能な要素である場合、または引数が渡される`ByVal`プロシージャが呼び出し元のコードでは、その値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="0b30a-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="0b30a-118">ただし、プロシージャは、このような引数のローカル コピーを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="0b30a-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="0b30a-119">プロシージャ コードでプロシージャ引数のコピーを変更するには</span><span class="sxs-lookup"><span data-stu-id="0b30a-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="0b30a-120">プロシージャ宣言で指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)引数に対応するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="0b30a-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="0b30a-121">または</span><span class="sxs-lookup"><span data-stu-id="0b30a-121">-or-</span></span>  
  
     <span data-ttu-id="0b30a-122">呼び出し元のコードでは、引数、引数リストのかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="0b30a-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="0b30a-123">これにより、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]引数を値渡し、場合でも、対応するパラメーターを指定する`ByRef`です。</span><span class="sxs-lookup"><span data-stu-id="0b30a-123">This forces [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="0b30a-124">プロシージャのコードでは、引数のローカル コピーに値を代入するのにパラメーターの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="0b30a-125">呼び出し元のコードに基になる値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="0b30a-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b30a-126">例</span><span class="sxs-lookup"><span data-stu-id="0b30a-126">Example</span></span>  
 <span data-ttu-id="0b30a-127">次の例では、その要素の配列変数を行い、操作を 2 つの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="0b30a-128">`increase`プロシージャが単に各要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="0b30a-129">`replace`プロシージャがパラメーターに新しい配列を割り当てます`a()`し、各要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 <span data-ttu-id="0b30a-130">最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="0b30a-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="0b30a-131">配列`n`、参照型では、`replace`引き渡し方法になっても、そのメンバーを変更できます`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="0b30a-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="0b30a-132">2 番目`MsgBox`表示を呼び出して"目後: 101、201、301"です。</span><span class="sxs-lookup"><span data-stu-id="0b30a-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="0b30a-133">`n`渡される`ByRef`、`replace`変数を変更できます`n`呼び出し元のコードと割り当てを新しい配列にします。</span><span class="sxs-lookup"><span data-stu-id="0b30a-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="0b30a-134">`n` 、参照型では、`replace`そのメンバーを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="0b30a-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="0b30a-135">プロシージャは、呼び出し元のコードでは、変数自体を変更されないようにできます。</span><span class="sxs-lookup"><span data-stu-id="0b30a-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="0b30a-136">参照してください[する方法: プロシージャ引数の値が変化しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b30a-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b30a-137">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0b30a-137">Compiling the Code</span></span>  
 <span data-ttu-id="0b30a-138">参照によって変数を渡す際に使用する必要あります、`ByRef`このメカニズムを指定するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="0b30a-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="0b30a-139">既定で[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]は引数の値渡しします。</span><span class="sxs-lookup"><span data-stu-id="0b30a-139">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="0b30a-140">いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="0b30a-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="0b30a-141">これにより、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="0b30a-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0b30a-142">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0b30a-142">.NET Framework Security</span></span>  
 <span data-ttu-id="0b30a-143">呼び出し元のコードで引数の基になる値を変更するプロシージャを許可するのには潜在的なリスクは常にします。</span><span class="sxs-lookup"><span data-stu-id="0b30a-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="0b30a-144">この値を変更してを使用する前の有効性を確認する準備を行うことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0b30a-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b30a-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b30a-145">See Also</span></span>  
 [<span data-ttu-id="0b30a-146">手順</span><span class="sxs-lookup"><span data-stu-id="0b30a-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="0b30a-147">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="0b30a-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="0b30a-148">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="0b30a-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="0b30a-149">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="0b30a-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="0b30a-150">変更できる引数と変更できない引数の違い</span><span class="sxs-lookup"><span data-stu-id="0b30a-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="0b30a-151">引数の値渡しと参照渡しの違い</span><span class="sxs-lookup"><span data-stu-id="0b30a-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="0b30a-152">方法: プロシージャ引数の値が変化しないようにする</span><span class="sxs-lookup"><span data-stu-id="0b30a-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="0b30a-153">方法: 引数の値渡しを強制する</span><span class="sxs-lookup"><span data-stu-id="0b30a-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="0b30a-154">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="0b30a-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="0b30a-155">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="0b30a-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
