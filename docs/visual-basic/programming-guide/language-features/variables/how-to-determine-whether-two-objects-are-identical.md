---
title: "方法:&2; つのオブジェクトが (Visual Basic) の場合と同じであるかどうかを判断する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
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
ms.openlocfilehash: c9621412eb1429ed07d8861114a67a67b6c1d58c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="3b7a5-102">方法:&2; つのオブジェクトが同一であるかどうか判別する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b7a5-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="3b7a5-103">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、2 つの変数参照が同一と見なされます、ポインターが同じ場合、つまり、両方の変数がメモリ内の同じクラス インスタンスを指している場合。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="3b7a5-104">たとえば、Windows フォーム アプリケーションでは、場合を判断する比較するかどうか、現在のインスタンス (`Me`) など、特定のインスタンスと同じ`Form2`します。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="3b7a5-105">ポインターを比較する&2; つの演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-105"> provides two operators to compare pointers.</span></span> <span data-ttu-id="3b7a5-106">[Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)返します`True`場合は、オブジェクトが同一で、および[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)を返します`True`されていない場合。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="3b7a5-107">2 つのオブジェクトが同じかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="3b7a5-108">2 つのオブジェクトが同じかどうかを判断するには</span><span class="sxs-lookup"><span data-stu-id="3b7a5-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="3b7a5-109">セットアップ、 `Boolean`&2; つのオブジェクトをテストする式。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="3b7a5-110">テスト式で使用して、`Is`演算子のオペランドとして&2; つのオブジェクトを指定しています。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="3b7a5-111">`Is`返します`True`オブジェクトが同じクラスのインスタンスを指している場合。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="3b7a5-112">2 つのオブジェクトが同一でないかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="3b7a5-113">2 つのオブジェクトが同一で可能でありを結合する厄介なアクションの実行することが必要`Not`と`Is`、たとえば`If Not obj1 Is obj2`です。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="3b7a5-114">このようなケースで使用できます、`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="3b7a5-115">2 つのオブジェクトが同一でないかどうかを判断するには</span><span class="sxs-lookup"><span data-stu-id="3b7a5-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="3b7a5-116">セットアップ、 `Boolean`&2; つのオブジェクトをテストする式。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="3b7a5-117">テスト式で使用して、`IsNot`演算子のオペランドとして&2; つのオブジェクトを指定しています。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="3b7a5-118">`IsNot`返します`True`場合は、オブジェクトが同じクラスのインスタンスを指すようにします。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7a5-119">例</span><span class="sxs-lookup"><span data-stu-id="3b7a5-119">Example</span></span>  
 <span data-ttu-id="3b7a5-120">次の例では、組の`Object`変数を同じクラスのインスタンスを指しているかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 <span data-ttu-id="3b7a5-121">[!code-vb[VbVbalrKeywords&#14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3b7a5-121">[!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]</span></span>  
  
 <span data-ttu-id="3b7a5-122">前の例では、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-122">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="3b7a5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b7a5-123">See Also</span></span>  
 <span data-ttu-id="3b7a5-124">[オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="3b7a5-124">[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="3b7a5-125"> [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3b7a5-125"> [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
<span data-ttu-id="3b7a5-126"> [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span><span class="sxs-lookup"><span data-stu-id="3b7a5-126"> [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md) </span></span>  
<span data-ttu-id="3b7a5-127"> [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="3b7a5-127"> [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="3b7a5-128"> [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="3b7a5-128"> [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="3b7a5-129"> [方法:&2; つのオブジェクトが関連するかどうかを判別します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span><span class="sxs-lookup"><span data-stu-id="3b7a5-129"> [How to: Determine Whether Two Objects Are Related](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md) </span></span>  
<span data-ttu-id="3b7a5-130"> [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="3b7a5-130"> [Me, My, MyBase, and MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>
