---
title: '% 演算子 (C# リファレンス)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f891d-102">% 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f891d-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="f891d-103">剰余演算子 (`%`) は、最初のオペランドを 2 番目のオペランドで除算した後の剰余を計算します。</span><span class="sxs-lookup"><span data-stu-id="f891d-103">The remainder operator (`%`) computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="f891d-104">すべての数値型には定義済みの剰余演算子があります。</span><span class="sxs-lookup"><span data-stu-id="f891d-104">All numeric types have predefined remainder operators.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="f891d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f891d-105">Remarks</span></span>  
 <span data-ttu-id="f891d-106">式 `a % b` は常に `(-b, b)` の範囲の値を返します。`b` または `-b` が返されることはありません。被除数の符号が保持されます。</span><span class="sxs-lookup"><span data-stu-id="f891d-106">The formula `a % b` will always return a value on the range `(-b, b)`, exclusive (it can never return `b` or `-b`), keeping the sign of the dividend.</span></span> <span data-ttu-id="f891d-107">整数除算の場合、剰余演算子はルール `a % b = a - (a / b) * b` を満たします。</span><span class="sxs-lookup"><span data-stu-id="f891d-107">For integer division, the remainder operator satisfies the rule `a % b = a - (a / b) * b`.</span></span>
  
 <span data-ttu-id="f891d-108">これを正規剰余と混同しないでください。正規剰余は同様のルールを満たしますが、切り捨て除算であり、`[0, b)` の範囲の値を返します。</span><span class="sxs-lookup"><span data-stu-id="f891d-108">This is not to be confused with canonical modulus, which satisfies a similar rule but with floored division and returns values on the range `[0, b)`.</span></span> <span data-ttu-id="f891d-109">C# には、正規剰余の演算子はありません。</span><span class="sxs-lookup"><span data-stu-id="f891d-109">C# does not have an operator for canonical modulus.</span></span> <span data-ttu-id="f891d-110">ただし、動作は正の被除数と同じです。</span><span class="sxs-lookup"><span data-stu-id="f891d-110">However, the behavior is the same for positive dividends.</span></span>
  
 <span data-ttu-id="f891d-111">ユーザー定義型は `%` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="f891d-111">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="f891d-112">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="f891d-112">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f891d-113">例</span><span class="sxs-lookup"><span data-stu-id="f891d-113">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="f891d-114">コメント</span><span class="sxs-lookup"><span data-stu-id="f891d-114">Comments</span></span>  
 <span data-ttu-id="f891d-115">double 型に関連する丸めエラーに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f891d-115">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f891d-116">参照</span><span class="sxs-lookup"><span data-stu-id="f891d-116">See Also</span></span>  
 [<span data-ttu-id="f891d-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f891d-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f891d-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f891d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f891d-119">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f891d-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
