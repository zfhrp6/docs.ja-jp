---
title: '方法: 引数の値渡しを強制する (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30f5e5fe7b9c92f90673dc99a0e299136a38305b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="75eb6-102">方法: 引数の値渡しを強制する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75eb6-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="75eb6-103">プロシージャ宣言では、引き渡し方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="75eb6-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="75eb6-104">パラメーターが宣言されている場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、参照によって、対応する引数を渡す Visual Basic が必要です。</span><span class="sxs-lookup"><span data-stu-id="75eb6-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="75eb6-105">これにより、呼び出し元のコードで引数の基になるプログラミング要素の値を変更する手順です。</span><span class="sxs-lookup"><span data-stu-id="75eb6-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="75eb6-106">このような変更を基になる要素を保護する場合は、オーバーライドできます、`ByRef`引き渡し方法の手順では引数の名前をかっこで囲んだ呼び出します。</span><span class="sxs-lookup"><span data-stu-id="75eb6-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="75eb6-107">このかっこは、呼び出しで引数リストを囲むかっこだけでなく、します。</span><span class="sxs-lookup"><span data-stu-id="75eb6-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="75eb6-108">呼び出し元のコードがオーバーライドすることはできません、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="75eb6-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="75eb6-109">引数の値渡しを強制するには</span><span class="sxs-lookup"><span data-stu-id="75eb6-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="75eb6-110">対応するパラメーターが宣言されている場合`ByVal`の手順では、追加の手順を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="75eb6-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="75eb6-111">Visual Basic は、既に、値渡しの引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="75eb6-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="75eb6-112">対応するパラメーターが宣言されている場合`ByRef`の手順で、プロシージャ呼び出しでのかっこ内に引数を囲みます。</span><span class="sxs-lookup"><span data-stu-id="75eb6-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75eb6-113">例</span><span class="sxs-lookup"><span data-stu-id="75eb6-113">Example</span></span>  
 <span data-ttu-id="75eb6-114">次の例よりも優先、`ByRef`パラメーター宣言します。</span><span class="sxs-lookup"><span data-stu-id="75eb6-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="75eb6-115">強制する呼び出しで`ByVal`かっこの 2 つのレベルに注意してください。</span><span class="sxs-lookup"><span data-stu-id="75eb6-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 <span data-ttu-id="75eb6-116">ときに`str`引数リスト内で余分なかっこで囲まれて、`setNewString`プロシージャが呼び出し元のコードでは、その値を変更ことはできませんと`MsgBox`ByVal を越えた場合は、「を置換できません」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75eb6-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="75eb6-117">ときに`str`囲まれていない追加のかっこ内にプロシージャを変更できますが、および`MsgBox`「inString 引数の新しい値はこのです」が表示されます。</span><span class="sxs-lookup"><span data-stu-id="75eb6-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75eb6-118">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="75eb6-118">Compiling the Code</span></span>  
 <span data-ttu-id="75eb6-119">参照によって変数を渡す際に使用する必要あります、`ByRef`このメカニズムを指定するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="75eb6-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="75eb6-120">Visual Basic では既定では、引数の値渡しです。</span><span class="sxs-lookup"><span data-stu-id="75eb6-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="75eb6-121">いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。</span><span class="sxs-lookup"><span data-stu-id="75eb6-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="75eb6-122">これにより、コードを読みやすくします。</span><span class="sxs-lookup"><span data-stu-id="75eb6-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="75eb6-123">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="75eb6-123">Robust Programming</span></span>  
 <span data-ttu-id="75eb6-124">プロシージャ パラメーターを宣言する場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、正しいコードの実行は呼び出し元のコードに基になる要素を変更することに依存しています。</span><span class="sxs-lookup"><span data-stu-id="75eb6-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="75eb6-125">呼び出し元のコードは、引数をかっこで囲んででこの呼び出し元のメカニズムをオーバーライドする場合、または変更できない引数を渡す場合は、プロシージャは、基になる要素を変更できません。</span><span class="sxs-lookup"><span data-stu-id="75eb6-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="75eb6-126">これにより、呼び出し元のコードで予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75eb6-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="75eb6-127">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="75eb6-127">.NET Framework Security</span></span>  
 <span data-ttu-id="75eb6-128">呼び出し元のコードで引数の基になる値を変更するプロシージャを許可するのには潜在的なリスクは常にします。</span><span class="sxs-lookup"><span data-stu-id="75eb6-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="75eb6-129">この値を変更してを使用する前の有効性を確認する準備を行うことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="75eb6-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75eb6-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="75eb6-130">See Also</span></span>  
 [<span data-ttu-id="75eb6-131">手順</span><span class="sxs-lookup"><span data-stu-id="75eb6-131">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="75eb6-132">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="75eb6-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="75eb6-133">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="75eb6-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="75eb6-134">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="75eb6-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="75eb6-135">変更できる引数と変更できない引数の違い</span><span class="sxs-lookup"><span data-stu-id="75eb6-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="75eb6-136">引数の値渡しと参照渡しの違い</span><span class="sxs-lookup"><span data-stu-id="75eb6-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="75eb6-137">方法: プロシージャ引数の値を変更する</span><span class="sxs-lookup"><span data-stu-id="75eb6-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="75eb6-138">方法: プロシージャ引数の値が変化しないようにする</span><span class="sxs-lookup"><span data-stu-id="75eb6-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="75eb6-139">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="75eb6-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="75eb6-140">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="75eb6-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
