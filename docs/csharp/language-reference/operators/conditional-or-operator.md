---
title: "|| 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="34cda-102">|| 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="34cda-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="34cda-103">条件付き OR 演算子 (`||`) では、`bool` オペランドの論理 OR が実行されます。</span><span class="sxs-lookup"><span data-stu-id="34cda-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="34cda-104">最初のオペランドが `true` と評価されると、2 番目のオペランドは評価されません。</span><span class="sxs-lookup"><span data-stu-id="34cda-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="34cda-105">最初のオペランドが `false` と評価されると、2 番目の演算子は、OR 式を、全体として、`true` または `false` に評価するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="34cda-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34cda-106">コメント</span><span class="sxs-lookup"><span data-stu-id="34cda-106">Remarks</span></span>  
 <span data-ttu-id="34cda-107">次の演算は、</span><span class="sxs-lookup"><span data-stu-id="34cda-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="34cda-108">次の演算に対応しています。</span><span class="sxs-lookup"><span data-stu-id="34cda-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="34cda-109">ただし `x` が `true` の場合、OR 演算は `y` の値に関係なく `true` となるため、`y` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="34cda-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="34cda-110">この概念は、"ショートサーキット" 評価と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="34cda-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="34cda-111">条件付き OR 演算子はオーバーロードできませんが、通常の論理演算子、[true](../../../csharp/language-reference/keywords/true.md) 演算子、[false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、一定の制約内で、条件付き論理演算子のオーバーロードとも見なされます。</span><span class="sxs-lookup"><span data-stu-id="34cda-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34cda-112">例</span><span class="sxs-lookup"><span data-stu-id="34cda-112">Example</span></span>  
 <span data-ttu-id="34cda-113">次の例では、`||` が使用されている式は、最初のオペランドだけを評価します。</span><span class="sxs-lookup"><span data-stu-id="34cda-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="34cda-114">`|` が使用されている式は、両方のオペランドを評価します。</span><span class="sxs-lookup"><span data-stu-id="34cda-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="34cda-115">2 番目の例では、両方のオペランドが評価されると、実行時例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="34cda-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="34cda-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="34cda-116">See Also</span></span>  
 [<span data-ttu-id="34cda-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="34cda-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="34cda-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="34cda-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="34cda-119">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="34cda-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
