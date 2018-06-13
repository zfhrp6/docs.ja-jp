---
title: -= 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 2f37bfa303fb523840b15e896ee3b4a967eb5b2b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171456"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="4f463-102">-= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4f463-102">-= Operator (C# Reference)</span></span>
<span data-ttu-id="4f463-103">減算代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="4f463-103">The subtraction assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f463-104">コメント</span><span class="sxs-lookup"><span data-stu-id="4f463-104">Remarks</span></span>  
 <span data-ttu-id="4f463-105">次のような `-=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="4f463-105">An expression using the `-=` assignment operator, such as</span></span>  
  
```csharp  
x -= y  
```  
  
 <span data-ttu-id="4f463-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="4f463-106">is equivalent to</span></span>  
  
```csharp  
x = x - y  
```  
  
 <span data-ttu-id="4f463-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="4f463-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4f463-108">[- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)の意味は、`x` および `y` の型によって異なります (数値オペランドの場合は減算、デリゲート オペランドの場合はデリゲートの削除、など)。</span><span class="sxs-lookup"><span data-stu-id="4f463-108">The meaning of the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) is dependent on the types of `x` and `y` (subtraction for numeric operands, delegate removal for delegate operands, and so forth).</span></span>  
  
 <span data-ttu-id="4f463-109">`-=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [- 演算子](../../../csharp/language-reference/operators/subtraction-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="4f463-109">The `-=` operator cannot be overloaded directly, but user-defined types can overload the [- operator](../../../csharp/language-reference/operators/subtraction-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="4f463-110">-= 演算子は、C# でイベント サブスクリプションを解除するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="4f463-110">The -= operator is also used in C# to unsubscribe from an event.</span></span> <span data-ttu-id="4f463-111">詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f463-111">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f463-112">例</span><span class="sxs-lookup"><span data-stu-id="4f463-112">Example</span></span>  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4f463-113">参照</span><span class="sxs-lookup"><span data-stu-id="4f463-113">See Also</span></span>  
 [<span data-ttu-id="4f463-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="4f463-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4f463-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4f463-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4f463-116">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="4f463-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
