---
title: IsFalse 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="bcc53-102">IsFalse 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcc53-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="bcc53-103">式は、かどうかを判断`False`です。</span><span class="sxs-lookup"><span data-stu-id="bcc53-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="bcc53-104">呼び出すことはできません`IsFalse`明示的に、コードが、Visual Basic のコンパイラが使用できるからコードを生成する`AndAlso`句。</span><span class="sxs-lookup"><span data-stu-id="bcc53-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="bcc53-105">クラスまたは構造体を定義しでその型の変数を使用する場合、`AndAlso`を定義する必要があります句、`IsFalse`そのクラスまたは構造にします。</span><span class="sxs-lookup"><span data-stu-id="bcc53-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="bcc53-106">コンパイラは、`IsFalse`と`IsTrue`演算子として、*ペア*です。</span><span class="sxs-lookup"><span data-stu-id="bcc53-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="bcc53-107">つまり、それらのいずれかを定義する場合をする必要がありますも定義、もう 1 つです。</span><span class="sxs-lookup"><span data-stu-id="bcc53-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcc53-108">`IsFalse`演算子を指定できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できますその動作のオペランドは、そのクラスまたは構造体の型を持つときにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bcc53-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="bcc53-109">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="bcc53-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bcc53-110">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="bcc53-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcc53-111">例</span><span class="sxs-lookup"><span data-stu-id="bcc53-111">Example</span></span>  
 <span data-ttu-id="bcc53-112">次のコード例の定義を含む構造体の輪郭の定義、`IsFalse`と`IsTrue`演算子。</span><span class="sxs-lookup"><span data-stu-id="bcc53-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bcc53-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcc53-113">See Also</span></span>  
 [<span data-ttu-id="bcc53-114">IsTrue 演算子</span><span class="sxs-lookup"><span data-stu-id="bcc53-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="bcc53-115">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="bcc53-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="bcc53-116">AndAlso 演算子</span><span class="sxs-lookup"><span data-stu-id="bcc53-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
