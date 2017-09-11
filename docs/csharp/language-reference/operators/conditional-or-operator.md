---
title: "|| 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
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
ms.openlocfilehash: 57bcb25b0d453fa59855f40c3189eb4af2bb8b7f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="4ca17-102">|| 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4ca17-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="4ca17-103">条件付き OR 演算子 (`||`) では、`bool` オペランドの論理 OR が実行されます。</span><span class="sxs-lookup"><span data-stu-id="4ca17-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="4ca17-104">最初のオペランドが `true` と評価されると、2 番目のオペランドは評価されません。</span><span class="sxs-lookup"><span data-stu-id="4ca17-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="4ca17-105">最初のオペランドが `false` と評価されると、2 番目の演算子は、OR 式を、全体として、`true` または `false` に評価するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="4ca17-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ca17-106">コメント</span><span class="sxs-lookup"><span data-stu-id="4ca17-106">Remarks</span></span>  
 <span data-ttu-id="4ca17-107">次の演算は、</span><span class="sxs-lookup"><span data-stu-id="4ca17-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="4ca17-108">次の演算に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4ca17-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="4ca17-109">ただし `x` が `true` の場合、OR 演算は `y` の値に関係なく `true` となるため、`y` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="4ca17-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="4ca17-110">この概念は、"ショートサーキット" 評価と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4ca17-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="4ca17-111">条件付き OR 演算子はオーバーロードできませんが、通常の論理演算子、[true](../../../csharp/language-reference/keywords/true.md) 演算子、[false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、一定の制約内で、条件付き論理演算子のオーバーロードとも見なされます。</span><span class="sxs-lookup"><span data-stu-id="4ca17-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ca17-112">例</span><span class="sxs-lookup"><span data-stu-id="4ca17-112">Example</span></span>  
 <span data-ttu-id="4ca17-113">次の例では、`||` が使用されている式は、最初のオペランドだけを評価します。</span><span class="sxs-lookup"><span data-stu-id="4ca17-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="4ca17-114">`|` が使用されている式は、両方のオペランドを評価します。</span><span class="sxs-lookup"><span data-stu-id="4ca17-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="4ca17-115">2 番目の例では、両方のオペランドが評価されると、実行時例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="4ca17-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 <span data-ttu-id="4ca17-116">[!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4ca17-116">[!code-cs[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ca17-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ca17-117">See Also</span></span>  
 <span data-ttu-id="4ca17-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4ca17-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4ca17-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4ca17-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="4ca17-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="4ca17-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

