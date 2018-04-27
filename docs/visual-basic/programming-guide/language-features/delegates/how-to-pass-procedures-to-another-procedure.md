---
title: '方法 : Visual Basic でプロシージャを別のプロシージャに渡す'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 30264e0480b603b21f8f71893af0fd742af40286
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="4e0ea-102">方法 : Visual Basic でプロシージャを別のプロシージャに渡す</span><span class="sxs-lookup"><span data-stu-id="4e0ea-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>
<span data-ttu-id="4e0ea-103">この例では、デリゲートを使用してプロシージャを別のプロシージャに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="4e0ea-104">デリゲートは、Visual Basic の他の型と同様に使用できる型です。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="4e0ea-105">`AddressOf`演算子プロシージャ名に適用される場合は、デリゲート オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="4e0ea-106">この例で取得した、別のプロシージャへの参照を実行できるデリゲート パラメーターを持つプロシージャ、`AddressOf`演算子。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="4e0ea-107">デリゲートと一致するプロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-107">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="4e0ea-108">という名前のデリゲートを作成する`MathOperator`です。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  <span data-ttu-id="4e0ea-109">という名前のプロシージャを作成する`AddNumbers`パラメーターと戻り値の型と一致する`MathOperator`署名が一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  <span data-ttu-id="4e0ea-110">という名前のプロシージャを作成する`SubtractNumbers`と一致するシグネチャを持つ`MathOperator`します。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  <span data-ttu-id="4e0ea-111">という名前のプロシージャを作成する`DelegateTest`をパラメーターとしてデリゲートを取得します。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="4e0ea-112">この手順への参照を受け入れることができる`AddNumbers`または`SubtractNumbers`、署名が一致するので、`MathOperator`署名します。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  <span data-ttu-id="4e0ea-113">という名前のプロシージャを作成する`Test`を呼び出す`DelegateTest`のデリゲートが 1 回`AddNumbers`をパラメーターとして再度のデリゲートを使用して`SubtractNumbers`をパラメーターとして。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     <span data-ttu-id="4e0ea-114">ときに`Test`が呼び出されると、その最初の結果を表示`AddNumbers`で動作している`5`と`3`は 8 です。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="4e0ea-115">結果、`SubtractNumbers`に作用する`9`と`3`が表示されたらは 6 です。</span><span class="sxs-lookup"><span data-stu-id="4e0ea-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e0ea-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e0ea-116">See Also</span></span>  
 [<span data-ttu-id="4e0ea-117">デリゲート</span><span class="sxs-lookup"><span data-stu-id="4e0ea-117">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="4e0ea-118">AddressOf 演算子</span><span class="sxs-lookup"><span data-stu-id="4e0ea-118">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="4e0ea-119">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="4e0ea-119">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="4e0ea-120">方法: デリゲート メソッドを呼び出す</span><span class="sxs-lookup"><span data-stu-id="4e0ea-120">How to: Invoke a Delegate Method</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
