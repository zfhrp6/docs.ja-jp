---
title: "方法: Visual Basic での別のプロシージャに渡す |Microsoft ドキュメント"
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
- AddressOf operator
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
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
ms.openlocfilehash: 95cbcf836b0dad875851052a367666c00cd54e37
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="ea792-102">方法 : Visual Basic でプロシージャを別のプロシージャに渡す</span><span class="sxs-lookup"><span data-stu-id="ea792-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="ea792-103">この例では、デリゲートを使用してプロシージャを別のプロシージャに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ea792-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="ea792-104">デリゲートは、その他の種類のように使用できる型[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="ea792-104">A delegate is a type that you can use like any other type in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="ea792-105">`AddressOf`演算子は、プロシージャの名前に適用する場合は、デリゲート オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="ea792-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="ea792-106">この例で取得される別のプロシージャへの参照を使用できるデリゲート パラメーターを持つプロシージャには、`AddressOf`演算子。</span><span class="sxs-lookup"><span data-stu-id="ea792-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="ea792-107">デリゲートと一致する手順を作成します。</span><span class="sxs-lookup"><span data-stu-id="ea792-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="ea792-108">という名前のデリゲートを作成する`MathOperator`です。</span><span class="sxs-lookup"><span data-stu-id="ea792-108">Create a delegate named `MathOperator`.</span></span>  
  
     <span data-ttu-id="ea792-109">[!code-vb[VbVbalrDelegates&#1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ea792-109">[!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]</span></span>  
  
2.  <span data-ttu-id="ea792-110">という名前のプロシージャを作成する`AddNumbers`パラメーターと戻り値の型と一致する`MathOperator`署名が一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="ea792-110">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     <span data-ttu-id="ea792-111">[!code-vb[VbVbalrDelegates&#2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ea792-111">[!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]</span></span>  
  
3.  <span data-ttu-id="ea792-112">という名前のプロシージャを作成する`SubtractNumbers`と一致するシグネチャを持つ`MathOperator`です。</span><span class="sxs-lookup"><span data-stu-id="ea792-112">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     <span data-ttu-id="ea792-113">[!code-vb[VbVbalrDelegates&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ea792-113">[!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]</span></span>  
  
4.  <span data-ttu-id="ea792-114">という名前のプロシージャを作成する`DelegateTest`パラメーターとしてデリゲートを取得します。</span><span class="sxs-lookup"><span data-stu-id="ea792-114">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="ea792-115">この手順への参照を受け入れることができる`AddNumbers`または`SubtractNumbers`、署名が一致するので、`MathOperator`署名します。</span><span class="sxs-lookup"><span data-stu-id="ea792-115">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     <span data-ttu-id="ea792-116">[!code-vb[VbVbalrDelegates&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ea792-116">[!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]</span></span>  
  
5.  <span data-ttu-id="ea792-117">という名前のプロシージャを作成する`Test`を呼び出す`DelegateTest`のデリゲートが&1; 回`AddNumbers`をパラメーターとして、もう一度のデリゲートを使用して`SubtractNumbers`をパラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="ea792-117">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     <span data-ttu-id="ea792-118">[!code-vb[VbVbalrDelegates&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ea792-118">[!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]</span></span>  
  
     <span data-ttu-id="ea792-119">`Test`が呼び出されると、その最初の結果を表示`AddNumbers`に機能している`5`と`3`は 8 です。</span><span class="sxs-lookup"><span data-stu-id="ea792-119">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="ea792-120">結果、`SubtractNumbers`に行動する`9`と`3`が表示されたら、6 であります。</span><span class="sxs-lookup"><span data-stu-id="ea792-120">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea792-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea792-121">See Also</span></span>  
 <span data-ttu-id="ea792-122">[デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea792-122">[Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="ea792-123"> [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ea792-123"> [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="ea792-124"> [Delegate ステートメント](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ea792-124"> [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="ea792-125"> [方法: デリゲート メソッドを呼び出す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span><span class="sxs-lookup"><span data-stu-id="ea792-125"> [How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span></span>
