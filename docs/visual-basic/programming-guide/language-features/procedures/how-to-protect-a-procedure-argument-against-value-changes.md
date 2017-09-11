---
title: "方法: プロシージャ引数の値が変更された (Visual Basic) を保護する |Microsoft ドキュメント"
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
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
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
ms.openlocfilehash: db40b3426256e7789a5273ab4d0afc8d5b47c8a7
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="1bc6e-102">方法: プロシージャ引数の値が変化しないようにする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bc6e-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="1bc6e-103">プロシージャとパラメーターを宣言する場合は、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャのコードに呼び出し元のコードで引数を基になるプログラミング要素への直接の参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="1bc6e-104">これにより、呼び出し元のコードで引数を基になる値を変更するプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="1bc6e-105">場合によってはの呼び出し元のコードは、このような変更から保護します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="1bc6e-106">対応するパラメーターを宣言することで、引数を変更から常に保護することができます[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)の手順です。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="1bc6e-107">によって自動的に指定した引数を変更できるようにする場合、それを宣言できます`ByRef`させて、呼び出し元のコードの各呼び出しにおいて引き渡し方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="1bc6e-108">これは、対応する引数を値渡しするかっこで囲むか、参照渡しにかっこで囲まないとで実行します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="1bc6e-109">詳細については、次を参照してください。[方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc6e-110">例</span><span class="sxs-lookup"><span data-stu-id="1bc6e-110">Example</span></span>  
 <span data-ttu-id="1bc6e-111">次の例では、その要素の配列変数を実行して、操作を&2; つの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="1bc6e-112">`increase`プロシージャが単に各要素に&1; を追加します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="1bc6e-113">`replace`プロシージャでは、パラメーターに新しい配列を割り当てます`a()`し、各要素に&1; を追加します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="1bc6e-114">ただし、再割り当てには、呼び出し元のコードで基になる配列変数は変わりません。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="1bc6e-115">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1bc6e-115">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span></span>  
  
 <span data-ttu-id="1bc6e-116">[!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1bc6e-116">[!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span></span>  
  
 <span data-ttu-id="1bc6e-117">[!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1bc6e-117">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span></span>  
  
 <span data-ttu-id="1bc6e-118">最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-118">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="1bc6e-119">配列`n`、参照型では、`replace`引き渡し方法は、そのメンバーを変更できます`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-119">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="1bc6e-120">2 番目`MsgBox`表示を呼び出して"目後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-120">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="1bc6e-121">`n`は`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることで呼び出し元のコードにします。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-121">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="1bc6e-122">ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`して呼び出し元のコードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-122">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="1bc6e-123">メンバーが変更されたとき`a`、ローカルの配列のみ`k`が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-123">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="1bc6e-124">したがって、`replace`配列の値は増分されません`n`呼び出し元のコードにします。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-124">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bc6e-125">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1bc6e-125">Compiling the Code</span></span>  
 <span data-ttu-id="1bc6e-126">既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-126">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="1bc6e-127">いずれかを指定することをお勧めします[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-127">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="1bc6e-128">これは、コードを読みやすくするためです。</span><span class="sxs-lookup"><span data-stu-id="1bc6e-128">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc6e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bc6e-129">See Also</span></span>  
 <span data-ttu-id="1bc6e-130">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-130">[Procedures](./index.md) </span></span>  
<span data-ttu-id="1bc6e-131"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-131"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="1bc6e-132"> [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-132"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="1bc6e-133"> [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-133"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="1bc6e-134"> [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-134"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="1bc6e-135"> [値と参照渡しの引数を渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-135"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="1bc6e-136"> [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-136"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="1bc6e-137"> [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-137"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="1bc6e-138"> [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="1bc6e-138"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="1bc6e-139"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="1bc6e-139"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
