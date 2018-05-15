---
title: '方法: プロシージャ引数の値が変化しないようにする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: d2e131b770d8498a634d946a5900f9b373ca7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="5bdea-102">方法: プロシージャ引数の値が変化しないようにする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bdea-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="5bdea-103">プロシージャがパラメーターとしてを宣言する場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic は、プロシージャ コード、呼び出し元のコードで引数の基になるこのプログラミング要素への直接参照します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="5bdea-104">これにより、プロシージャが呼び出し元のコードで引数の基になる値を変更します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="5bdea-105">場合によっては呼び出し元のコードは、このような変更を防ぐためにする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5bdea-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="5bdea-106">対応するパラメーターを宣言することで、変更から引数を保護できます常に[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)の手順でします。</span><span class="sxs-lookup"><span data-stu-id="5bdea-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="5bdea-107">によって自動的に指定された引数を変更できるようにする場合は、宣言できる`ByRef`させて、呼び出し元のコードの各呼び出しに渡すメカニズムを確認します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="5bdea-108">これは、対応する引数を値渡しをかっこで囲むか、参照渡しをかっこで囲まないとで実行します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="5bdea-109">詳細については、次を参照してください。[する方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)です。</span><span class="sxs-lookup"><span data-stu-id="5bdea-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bdea-110">例</span><span class="sxs-lookup"><span data-stu-id="5bdea-110">Example</span></span>  
 <span data-ttu-id="5bdea-111">次の例では、その要素の配列変数を行い、操作を 2 つの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="5bdea-112">`increase`プロシージャが単に各要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="5bdea-113">`replace`プロシージャがパラメーターに新しい配列を割り当てます`a()`し、各要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="5bdea-114">ただし、再割り当てでは、呼び出し元のコードに基になる、配列変数には影響しません。</span><span class="sxs-lookup"><span data-stu-id="5bdea-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 <span data-ttu-id="5bdea-115">最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="5bdea-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="5bdea-116">配列`n`、参照型では、`replace`引き渡し方法になっても、そのメンバーを変更できます`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="5bdea-116">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="5bdea-117">2 番目`MsgBox`表示を呼び出して"目後: 41、11、21、31"です。</span><span class="sxs-lookup"><span data-stu-id="5bdea-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="5bdea-118">`n`渡される`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることによって、呼び出し元のコードにします。</span><span class="sxs-lookup"><span data-stu-id="5bdea-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="5bdea-119">ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`呼び出し元のコードで渡される入力します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="5bdea-120">メンバーが変更されたとき`a`、ローカルの配列のみ`k`が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="5bdea-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="5bdea-121">したがって、`replace`配列の値をインクリメントしない`n`呼び出し元のコードにします。</span><span class="sxs-lookup"><span data-stu-id="5bdea-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bdea-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5bdea-122">Compiling the Code</span></span>  
 <span data-ttu-id="5bdea-123">Visual Basic では既定では、引数の値渡しです。</span><span class="sxs-lookup"><span data-stu-id="5bdea-123">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="5bdea-124">いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="5bdea-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="5bdea-125">これにより、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="5bdea-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdea-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bdea-126">See Also</span></span>  
 [<span data-ttu-id="5bdea-127">手順</span><span class="sxs-lookup"><span data-stu-id="5bdea-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5bdea-128">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="5bdea-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5bdea-129">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="5bdea-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="5bdea-130">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="5bdea-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="5bdea-131">変更できる引数と変更できない引数の違い</span><span class="sxs-lookup"><span data-stu-id="5bdea-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="5bdea-132">引数の値渡しと参照渡しの違い</span><span class="sxs-lookup"><span data-stu-id="5bdea-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="5bdea-133">方法: プロシージャ引数の値を変更する</span><span class="sxs-lookup"><span data-stu-id="5bdea-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="5bdea-134">方法: 引数の値渡しを強制する</span><span class="sxs-lookup"><span data-stu-id="5bdea-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="5bdea-135">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="5bdea-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="5bdea-136">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="5bdea-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
