---
title: "引数値渡しと参照渡し (Visual Basic) の相違点 |Microsoft ドキュメント"
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
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
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
ms.openlocfilehash: 706c64cd316791a748e2b68fe406e34084b04d5a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="9c0f1-102">引数の値渡しと参照渡しの違い (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c0f1-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>
<span data-ttu-id="9c0f1-103">プロシージャに&1; つまたは複数の引数を渡すときに、各引数は、呼び出し元のコード内の基になるプログラミング要素に対応します。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="9c0f1-104">この基になる要素の値またはへの参照を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="9c0f1-105">これと呼ばれますが、*渡し*します。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="9c0f1-106">値渡し</span><span class="sxs-lookup"><span data-stu-id="9c0f1-106">Passing by Value</span></span>  
 <span data-ttu-id="9c0f1-107">引数を渡す*値によって*を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャ定義でパラメーターに対応するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-107">You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="9c0f1-108">これを使用するメカニズムを渡すときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の手順でローカル変数に基になるプログラミング要素の値をコピーします。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-108">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="9c0f1-109">プロシージャのコードには、呼び出し元のコード内の基になる要素へのアクセスがありません。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="9c0f1-110">参照による受け渡し</span><span class="sxs-lookup"><span data-stu-id="9c0f1-110">Passing by Reference</span></span>  
 <span data-ttu-id="9c0f1-111">引数を渡す*参照によって*を指定して、 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)プロシージャ定義でパラメーターに対応するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-111">You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="9c0f1-112">これを使用するメカニズムを渡すときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]呼び出し元のコードで、手順、基になるプログラミング要素への直接参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-112">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="9c0f1-113">引数渡しの方法および要素の型</span><span class="sxs-lookup"><span data-stu-id="9c0f1-113">Passing Mechanism and Element Type</span></span>  
 <span data-ttu-id="9c0f1-114">渡す機能の選択は、基になる要素の型の分類と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="9c0f1-115">値渡しまたは参照渡しか参照何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャ コードに提供します。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-115">Passing by value or by reference refers to what [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies to the procedure code.</span></span> <span data-ttu-id="9c0f1-116">値型または参照型は、メモリ内プログラミング要素を格納する方法を参照します。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="9c0f1-117">ただし、引き渡し方法および要素の型は相互にします。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="9c0f1-118">参照型の値は、メモリ内の他の場所でのデータへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="9c0f1-119">つまり、基になる要素自体にアクセスできない場合でも値が参照型を渡すときにプロシージャ コードが基になる要素のデータへのポインターを持っています。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="9c0f1-120">など、要素が、配列変数の場合は、プロシージャのコードでは、変数自体にアクセスできないが、配列メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="9c0f1-121">変更する権限</span><span class="sxs-lookup"><span data-stu-id="9c0f1-121">Ability to Modify</span></span>  
 <span data-ttu-id="9c0f1-122">引数として、変更不可能な要素を渡すときに、手順変更できません呼び出し元のコードに渡されるかどうか`ByVal`または`ByRef`です。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="9c0f1-123">変更可能な要素には、次の表は、要素の型と渡し間のやり取りを示します。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="9c0f1-124">要素型</span><span class="sxs-lookup"><span data-stu-id="9c0f1-124">Element type</span></span>|<span data-ttu-id="9c0f1-125">渡されました。`ByVal`</span><span class="sxs-lookup"><span data-stu-id="9c0f1-125">Passed `ByVal`</span></span>|<span data-ttu-id="9c0f1-126">渡されました。`ByRef`</span><span class="sxs-lookup"><span data-stu-id="9c0f1-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="9c0f1-127">値型 (値のみを含む)</span><span class="sxs-lookup"><span data-stu-id="9c0f1-127">Value type (contains only a value)</span></span>|<span data-ttu-id="9c0f1-128">プロシージャには、変数、またはそのメンバーを変更できません。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="9c0f1-129">プロシージャには、変数とそのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="9c0f1-130">参照型 (クラスまたは構造体のインスタンスへのポインターが含まれています)</span><span class="sxs-lookup"><span data-stu-id="9c0f1-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="9c0f1-131">プロシージャは、変数を変更できませんが、指すインスタンスのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="9c0f1-132">プロシージャには、変数と、ポイントするインスタンスのメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="9c0f1-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c0f1-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c0f1-133">See Also</span></span>  
 <span data-ttu-id="9c0f1-134">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="9c0f1-135"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9c0f1-136"> [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-136"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="9c0f1-137"> [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-137"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="9c0f1-138"> [引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-138"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="9c0f1-139"> [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="9c0f1-140"> [方法: プロシージャ引数の値は変更しないように](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="9c0f1-141"> [方法: 引数値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-141"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="9c0f1-142"> [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="9c0f1-142"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="9c0f1-143"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="9c0f1-143"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
