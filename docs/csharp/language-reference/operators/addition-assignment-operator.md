---
title: "+= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
caps.latest.revision: 20
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
ms.openlocfilehash: 42567b2d8e7d9b694ce64ccb88e0fd4bfe05b020
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="cafa8-102">+= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cafa8-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="cafa8-103">加算代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="cafa8-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cafa8-104">コメント</span><span class="sxs-lookup"><span data-stu-id="cafa8-104">Remarks</span></span>  
 <span data-ttu-id="cafa8-105">次のような `+=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="cafa8-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```  
x += y  
```  
  
 <span data-ttu-id="cafa8-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="cafa8-106">is equivalent to</span></span>  
  
```  
x = x + y  
```  
  
 <span data-ttu-id="cafa8-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="cafa8-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="cafa8-108">[+ 演算子](../../../csharp/language-reference/operators/addition-operator.md)の意味は、`x` および `y` の型によって異なります (たとえば、数値オペランドの場合は加算、文字列オペランドの場合は連結になります)。</span><span class="sxs-lookup"><span data-stu-id="cafa8-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="cafa8-109">`+=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [+ 演算子](../../../csharp/language-reference/operators/addition-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="cafa8-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="cafa8-110">`+=` 演算子は、イベントに対する応答として呼び出されるメソッドを指定するときにも使用されます。こうしたメソッドは、イベント ハンドラーと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cafa8-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="cafa8-111">このコンテキストでの `+=` 演算子の使用は、"*イベントのサブスクライブ*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cafa8-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="cafa8-112">詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cafa8-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span> <span data-ttu-id="cafa8-113">また、「[デリゲート](../../../csharp/programming-guide/delegates/index.md)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="cafa8-113">and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cafa8-114">例</span><span class="sxs-lookup"><span data-stu-id="cafa8-114">Example</span></span>  
 <span data-ttu-id="cafa8-115">[!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cafa8-115">[!code-cs[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cafa8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cafa8-116">See Also</span></span>  
 <span data-ttu-id="cafa8-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cafa8-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cafa8-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cafa8-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="cafa8-119">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="cafa8-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

