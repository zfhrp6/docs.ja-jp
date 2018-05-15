---
title: IsTrue 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: fc01b074d9aba245b1c55b75b841a7f195f7ec04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="9b07f-102">IsTrue 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b07f-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="9b07f-103">式は、かどうかを判断`True`です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="9b07f-104">呼び出すことはできません`IsTrue`明示的に、コードが、Visual Basic のコンパイラが使用できるからコードを生成する`OrElse`句。</span><span class="sxs-lookup"><span data-stu-id="9b07f-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="9b07f-105">クラスまたは構造体を定義しでその型の変数を使用する場合、`OrElse`を定義する必要があります句、`IsTrue`そのクラスまたは構造にします。</span><span class="sxs-lookup"><span data-stu-id="9b07f-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="9b07f-106">コンパイラは、`IsTrue`と`IsFalse`演算子として、*ペア*です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="9b07f-107">つまり、それらのいずれかを定義する場合をする必要がありますも定義、もう 1 つです。</span><span class="sxs-lookup"><span data-stu-id="9b07f-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="9b07f-108">IsTrue のコンパイラの使用</span><span class="sxs-lookup"><span data-stu-id="9b07f-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="9b07f-109">クラスまたは構造体を定義したらでその型の変数を使用することができます、 `For`、 `If`、 `Else``If`、または`While`ステートメント、または、`When`句。</span><span class="sxs-lookup"><span data-stu-id="9b07f-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else``If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="9b07f-110">これを行う場合、コンパイラは、演算子に、型に変換する`Boolean`条件をテストするための値します。</span><span class="sxs-lookup"><span data-stu-id="9b07f-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="9b07f-111">これは、適切な演算子は次の順序で検索します。</span><span class="sxs-lookup"><span data-stu-id="9b07f-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="9b07f-112">クラスまたは構造から拡大変換演算子`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="9b07f-113">クラスまたは構造から拡大変換演算子`Boolean?`です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="9b07f-114">`IsTrue`クラスまたは構造体で演算子。</span><span class="sxs-lookup"><span data-stu-id="9b07f-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="9b07f-115">縮小変換`Boolean?`からの変換を含まない`Boolean`に`Boolean?`です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="9b07f-116">クラスまたは構造から縮小変換演算子`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="9b07f-117">変換を定義していない場合`Boolean`または`IsTrue`演算子、コンパイラがエラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="9b07f-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b07f-118">`IsTrue`演算子を指定できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できますその動作のオペランドは、そのクラスまたは構造体の型を持つときにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9b07f-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="9b07f-119">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b07f-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9b07f-120">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b07f-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b07f-121">例</span><span class="sxs-lookup"><span data-stu-id="9b07f-121">Example</span></span>  
 <span data-ttu-id="9b07f-122">次のコード例の定義を含む構造体の輪郭の定義、`IsFalse`と`IsTrue`演算子。</span><span class="sxs-lookup"><span data-stu-id="9b07f-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9b07f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b07f-123">See Also</span></span>  
 [<span data-ttu-id="9b07f-124">IsFalse 演算子</span><span class="sxs-lookup"><span data-stu-id="9b07f-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="9b07f-125">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="9b07f-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="9b07f-126">OrElse 演算子</span><span class="sxs-lookup"><span data-stu-id="9b07f-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
