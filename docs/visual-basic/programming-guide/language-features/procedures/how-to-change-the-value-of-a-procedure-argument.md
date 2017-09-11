---
title: "方法: プロシージャ引数 (Visual Basic) の値を変更 |Microsoft ドキュメント"
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: 16
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
ms.openlocfilehash: 3f192d738ca2753cd12b6fffca1f4f94a606a42c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="bc6b6-102">方法: プロシージャ引数の値を変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc6b6-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="bc6b6-103">プロシージャを呼び出すときに指定する各引数はプロシージャで定義されているパラメーターの&1; つに対応します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="bc6b6-104">場合によっては、プロシージャのコードは呼び出し元のコードで引数を基になる値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="bc6b6-105">それ以外の場合で、手順は、引数のローカル コピーのみを変更できます。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="bc6b6-106">プロシージャを呼び出すときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]渡される引数は、すべてのローカル コピーを作成[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-106">When you call the procedure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="bc6b6-107">渡された各引数に対して[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャのコードに呼び出し元のコードで引数を基になるプログラミング要素への直接の参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="bc6b6-108">呼び出し元のコードに基になる要素が変更可能な引数が渡された場合`ByRef`プロシージャのコードが直接参照を使用して呼び出し元のコードに、要素の値に変更します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="bc6b6-109">基になる値を変更します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="bc6b6-110">呼び出し元のコードでプロシージャ引数の基になる値を変更するには</span><span class="sxs-lookup"><span data-stu-id="bc6b6-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="bc6b6-111">プロシージャの宣言で指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引数に対応するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="bc6b6-112">呼び出し元のコードで変更可能なプログラミング要素を引数として渡します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="bc6b6-113">呼び出し元のコードで囲む必要はありません引数リスト内のかっこで囲まれた引数です。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="bc6b6-114">プロシージャのコードでは、呼び出し元のコードで基になる要素に値を代入するのにパラメーター名を使用します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="bc6b6-115">この例を参照してくださいデモのさらに下です。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="bc6b6-116">ローカル コピーを変更します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-116">Changing Local Copies</span></span>  
 <span data-ttu-id="bc6b6-117">呼び出し元のコード内の基になる要素が、変更不可能な要素である場合、または引数が渡された場合`ByVal`プロシージャが呼び出し元のコードにはその値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="bc6b6-118">ただし、プロシージャは、このような引数のローカル コピーを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="bc6b6-119">プロシージャ コード内でプロシージャの引数のコピーを変更するには</span><span class="sxs-lookup"><span data-stu-id="bc6b6-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="bc6b6-120">プロシージャの宣言で指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)引数に対応するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="bc6b6-121">または</span><span class="sxs-lookup"><span data-stu-id="bc6b6-121">-or-</span></span>  
  
     <span data-ttu-id="bc6b6-122">呼び出し元のコードでは、引数、引数リストのかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="bc6b6-123">これにより、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]場合でも、対応するパラメーターを指定値で、引数を渡す`ByRef`します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-123">This forces [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="bc6b6-124">プロシージャ コード内でパラメーター名を使用して、引数のローカル コピーに値を代入します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="bc6b6-125">呼び出し元のコードで基になる値は変更されません。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc6b6-126">例</span><span class="sxs-lookup"><span data-stu-id="bc6b6-126">Example</span></span>  
 <span data-ttu-id="bc6b6-127">次の例では、その要素の配列変数を実行して、操作を&2; つの手順を示します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="bc6b6-128">`increase`プロシージャが単に各要素に&1; を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="bc6b6-129">`replace`プロシージャでは、パラメーターに新しい配列を割り当てます`a()`し、各要素に&1; を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 <span data-ttu-id="bc6b6-130">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc6b6-130">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span></span>  
  
 <span data-ttu-id="bc6b6-131">[!code-vb[VbVbcnProcedures&#36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc6b6-131">[!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span></span>  
  
 <span data-ttu-id="bc6b6-132">[!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc6b6-132">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span></span>  
  
 <span data-ttu-id="bc6b6-133">最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-133">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="bc6b6-134">配列`n`、参照型では、`replace`引き渡し方法は、そのメンバーを変更できます`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-134">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="bc6b6-135">2 番目`MsgBox`表示を呼び出して"目後: 101、201、301"です。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-135">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="bc6b6-136">`n`は`ByRef`、`replace`変数を変更できます`n`呼び出し元のコードと割り当てを新しい配列にします。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-136">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="bc6b6-137">`n` 、参照型では、`replace`そのメンバーを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-137">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="bc6b6-138">プロシージャを防ぐため、呼び出し元のコードでは、変数自体を変更できないことができます。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-138">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="bc6b6-139">参照してください[方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md)します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-139">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc6b6-140">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bc6b6-140">Compiling the Code</span></span>  
 <span data-ttu-id="bc6b6-141">参照渡しで変数を渡す場合は、使用、`ByRef`キーワードを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-141">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="bc6b6-142">既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-142">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="bc6b6-143">いずれかを指定することをお勧めします[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-143">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="bc6b6-144">これは、コードを読みやすくするためです。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-144">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bc6b6-145">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="bc6b6-145">.NET Framework Security</span></span>  
 <span data-ttu-id="bc6b6-146">呼び出し元のコードで引数を基になる値を変更する手順を可能にすることは潜在的なリスクは常にします。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-146">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="bc6b6-147">この値を変更し、使用する前に有効性を確認する準備を期待することを確認します。</span><span class="sxs-lookup"><span data-stu-id="bc6b6-147">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6b6-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc6b6-148">See Also</span></span>  
 <span data-ttu-id="bc6b6-149">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-149">[Procedures](./index.md) </span></span>  
<span data-ttu-id="bc6b6-150"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-150"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="bc6b6-151"> [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-151"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="bc6b6-152"> [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-152"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="bc6b6-153"> [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-153"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="bc6b6-154"> [値と参照渡しの引数を渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-154"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="bc6b6-155"> [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="bc6b6-156"> [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="bc6b6-157"> [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="bc6b6-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="bc6b6-158"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="bc6b6-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
