---
title: '方法: 2 つのオブジェクトが同一であるかどうか判別する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: bbcac2fc51e57427b125ec2f5e68f017a60186d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650099"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="39951-102">方法: 2 つのオブジェクトが同一であるかどうか判別する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39951-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="39951-103">Visual basic で 2 つの変数参照が同一と見なされます、ポインターが同じ場合、つまり、両方の変数がメモリ内で同じクラスのインスタンスを指している場合。</span><span class="sxs-lookup"><span data-stu-id="39951-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="39951-104">たとえば、Windows フォーム アプリケーションでは、場合を決定するを比較するかどうか、現在のインスタンス (`Me`) など、特定のインスタンスと同じ`Form2`です。</span><span class="sxs-lookup"><span data-stu-id="39951-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="39951-105">Visual Basic では、ポインターを比較する 2 つの演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="39951-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="39951-106">[Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)を返します`True`オブジェクトが一致する場合、 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)返します`True`されていない場合。</span><span class="sxs-lookup"><span data-stu-id="39951-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="39951-107">2 つのオブジェクトが同じかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="39951-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="39951-108">2 つのオブジェクトが同じかどうかを決定するには</span><span class="sxs-lookup"><span data-stu-id="39951-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="39951-109">セットアップ、 `Boolean` 2 つのオブジェクトをテストする式。</span><span class="sxs-lookup"><span data-stu-id="39951-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="39951-110">テスト式で使用して、`Is`演算子のオペランドとして 2 つのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="39951-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="39951-111">`Is` 返します`True`場合は、オブジェクトが、同じクラスのインスタンスをポイントします。</span><span class="sxs-lookup"><span data-stu-id="39951-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="39951-112">2 つのオブジェクトが同じでないかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="39951-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="39951-113">2 つのオブジェクトが同一でないと結合するメッセージが不適切であることができる場合、操作を実行することもあります`Not`と`Is`、たとえば`If Not obj1 Is obj2`します。</span><span class="sxs-lookup"><span data-stu-id="39951-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="39951-114">このようなケースで使用できます、`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="39951-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="39951-115">2 つのオブジェクトが同一でないかどうかを確認</span><span class="sxs-lookup"><span data-stu-id="39951-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="39951-116">セットアップ、 `Boolean` 2 つのオブジェクトをテストする式。</span><span class="sxs-lookup"><span data-stu-id="39951-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="39951-117">テスト式で使用して、`IsNot`演算子のオペランドとして 2 つのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="39951-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="39951-118">`IsNot` 返します`True`オブジェクトは、同じクラスのインスタンスを指していない場合。</span><span class="sxs-lookup"><span data-stu-id="39951-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39951-119">例</span><span class="sxs-lookup"><span data-stu-id="39951-119">Example</span></span>  
 <span data-ttu-id="39951-120">次の例の組み合わせをテストする`Object`変数を同じクラスのインスタンスを指しているかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39951-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="39951-121">前の例では、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39951-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="39951-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="39951-122">See Also</span></span>  
 [<span data-ttu-id="39951-123">Object 型</span><span class="sxs-lookup"><span data-stu-id="39951-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="39951-124">オブジェクト変数</span><span class="sxs-lookup"><span data-stu-id="39951-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="39951-125">オブジェクト変数の値</span><span class="sxs-lookup"><span data-stu-id="39951-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="39951-126">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="39951-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="39951-127">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="39951-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="39951-128">方法: 2 つのオブジェクトが関連しているかどうかを決める</span><span class="sxs-lookup"><span data-stu-id="39951-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="39951-129">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="39951-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
