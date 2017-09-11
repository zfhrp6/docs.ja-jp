---
title: "方法: 引数 (Visual Basic) を値渡しを強制する |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
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
ms.openlocfilehash: b151c319489ccda357faa082ce0b3c1addad0458
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="07dc1-102">方法: 引数の値渡しを強制する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07dc1-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="07dc1-103">プロシージャの宣言では、引き渡し方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="07dc1-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="07dc1-104">パラメーターが宣言されている場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]参照によって、対応する引数を渡すが必要です。</span><span class="sxs-lookup"><span data-stu-id="07dc1-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="07dc1-105">これにより、呼び出し元のコードで引数を基になるプログラミングの要素の値を変更する手順です。</span><span class="sxs-lookup"><span data-stu-id="07dc1-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="07dc1-106">このような変更を基になる要素を保護する場合をオーバーライドできます、`ByRef`引き渡し方法の手順で呼び出す引数の名前をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="07dc1-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="07dc1-107">このかっこは、呼び出しで引数リストを囲むかっこに追加します。</span><span class="sxs-lookup"><span data-stu-id="07dc1-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="07dc1-108">呼び出し元のコードを上書きできません、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="07dc1-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="07dc1-109">引数の値渡しを強制するには</span><span class="sxs-lookup"><span data-stu-id="07dc1-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="07dc1-110">対応するパラメーターが宣言されている場合`ByVal`の手順では、追加の手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="07dc1-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="07dc1-111">既に、引数の値渡しを期待しています。</span><span class="sxs-lookup"><span data-stu-id="07dc1-111"> already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="07dc1-112">対応するパラメーターが宣言されている場合`ByRef`の手順でプロシージャの呼び出しにかっこで囲まれた引数を囲みます。</span><span class="sxs-lookup"><span data-stu-id="07dc1-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07dc1-113">例</span><span class="sxs-lookup"><span data-stu-id="07dc1-113">Example</span></span>  
 <span data-ttu-id="07dc1-114">次の例では、オーバーライド、`ByRef`パラメーター宣言します。</span><span class="sxs-lookup"><span data-stu-id="07dc1-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="07dc1-115">強制的の呼び出しで`ByVal`かっこの&2; つのレベルに注意してください。</span><span class="sxs-lookup"><span data-stu-id="07dc1-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 <span data-ttu-id="07dc1-116">[!code-vb[VbVbcnProcedures&#39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="07dc1-116">[!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span></span>  
  
 <span data-ttu-id="07dc1-117">[!code-vb[VbVbcnProcedures #&40;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="07dc1-117">[!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span></span>  
  
 <span data-ttu-id="07dc1-118">`str`引数リスト内で余分なかっこで囲まれた、`setNewString`プロシージャが呼び出し元のコードにはその値を変更できませんと`MsgBox`ByVal が渡された場合は、「を置き換えることはできません」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="07dc1-118">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="07dc1-119">`str`囲まれていない余分なかっこで囲まれた、プロシージャを変更できますが、および`MsgBox`「inString 引数の新しい値はこれです。」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="07dc1-119">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07dc1-120">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="07dc1-120">Compiling the Code</span></span>  
 <span data-ttu-id="07dc1-121">参照渡しで変数を渡す場合は、使用、`ByRef`キーワードを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="07dc1-121">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="07dc1-122">既定で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は引数の値渡しします。</span><span class="sxs-lookup"><span data-stu-id="07dc1-122">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="07dc1-123">いずれかを指定することをお勧めします[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="07dc1-123">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="07dc1-124">これは、コードを読みやすくするためです。</span><span class="sxs-lookup"><span data-stu-id="07dc1-124">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="07dc1-125">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="07dc1-125">Robust Programming</span></span>  
 <span data-ttu-id="07dc1-126">プロシージャ パラメーターを宣言する場合は、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)コードの適切な実行は呼び出し元のコードの基になる要素に変更できることを依存している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="07dc1-126">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="07dc1-127">呼び出し元のコードは、引数をかっこで囲んででこの呼び出し元のメカニズムをオーバーライドする場合、または変更できない引数を渡す場合は、プロシージャは、基になる要素を変更できません。</span><span class="sxs-lookup"><span data-stu-id="07dc1-127">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="07dc1-128">これは、呼び出し元のコードで予期しない結果となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="07dc1-128">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="07dc1-129">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="07dc1-129">.NET Framework Security</span></span>  
 <span data-ttu-id="07dc1-130">呼び出し元のコードで引数を基になる値を変更する手順を可能にすることは潜在的なリスクは常にします。</span><span class="sxs-lookup"><span data-stu-id="07dc1-130">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="07dc1-131">この値を変更し、使用する前に有効性を確認する準備を期待することを確認します。</span><span class="sxs-lookup"><span data-stu-id="07dc1-131">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07dc1-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="07dc1-132">See Also</span></span>  
 <span data-ttu-id="07dc1-133">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-133">[Procedures](./index.md) </span></span>  
<span data-ttu-id="07dc1-134"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-134"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="07dc1-135"> [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-135"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="07dc1-136"> [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-136"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="07dc1-137"> [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-137"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="07dc1-138"> [値と参照渡しの引数を渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-138"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="07dc1-139"> [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="07dc1-140"> [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="07dc1-141"> [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="07dc1-141"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="07dc1-142"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="07dc1-142"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
