---
title: '方法: 2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="1518a-102">方法: 2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1518a-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="1518a-103">オブジェクトを参照する 2 つの変数があれば、いずれかを使用できる、`Is`または`IsNot`演算子、またはその両方を同じインスタンスを参照しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="1518a-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="1518a-104">2 つのオブジェクトが等しいかどうかをテストするには</span><span class="sxs-lookup"><span data-stu-id="1518a-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="1518a-105">使用して、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)または[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)オペランドとして 2 つの変数にします。</span><span class="sxs-lookup"><span data-stu-id="1518a-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="1518a-106">2 つのオブジェクトが同じインスタンスを参照するかどうかに応じて、特定のアクションを実行する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1518a-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="1518a-107">上記の例では、コントロール`c`フォームでアクティブなコントロールに対して`f`です。</span><span class="sxs-lookup"><span data-stu-id="1518a-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="1518a-108">アクティブなコントロールはありませんかがある場合はこれ以上が場合と同じコントロール インスタンス`c`、`If`ステートメントは失敗し、手順は、さらに処理することがなくを返します。</span><span class="sxs-lookup"><span data-stu-id="1518a-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="1518a-109">使用するかどうか`Is`または`IsNot`に個人の利便性の問題です。</span><span class="sxs-lookup"><span data-stu-id="1518a-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="1518a-110">1 つを指定された式に他方より読みやすくする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1518a-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1518a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="1518a-111">See Also</span></span>  
 [<span data-ttu-id="1518a-112">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="1518a-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
