---
title: "-= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d7f26ae1fce54eb0d03a314a83ce523baeb3f348
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="--operator-c-reference"></a><span data-ttu-id="b516c-102">-= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b516c-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="b516c-103">減算代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="b516c-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b516c-104">コメント</span><span class="sxs-lookup"><span data-stu-id="b516c-104">Remarks</span></span>  
 <span data-ttu-id="b516c-105">次のような `-=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="b516c-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```  
x -= y  
```  
  
 <span data-ttu-id="b516c-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="b516c-106">is equivalent to</span></span>  
  
```  
x = x - y  
```  
  
 <span data-ttu-id="b516c-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="b516c-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b516c-108">[- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)の意味は、`x` および `y` の型によって異なります (数値オペランドの場合は減算、デリゲート オペランドの場合はデリゲートの削除、など)。</span><span class="sxs-lookup"><span data-stu-id="b516c-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="b516c-109">`-=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="b516c-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="b516c-110">-= 演算子は、C# でイベント サブスクリプションを解除するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="b516c-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="b516c-111">詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b516c-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b516c-112">例</span><span class="sxs-lookup"><span data-stu-id="b516c-112">Example</span></span>  
 <span data-ttu-id="b516c-113">[!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b516c-113">[!code-cs[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b516c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b516c-114">See Also</span></span>  
 <span data-ttu-id="b516c-115">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b516c-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b516c-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b516c-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="b516c-117">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="b516c-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

