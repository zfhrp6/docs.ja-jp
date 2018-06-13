---
title: / 演算子 (C# リファレンス)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 9d0bbff1fd9f4ab3c93c879d12ccd5fde1187b44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272572"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ae68a-102">/ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ae68a-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="ae68a-103">除算演算子 (`/`) は、1 つ目のオペランドを 2 つ目のオペランドで除算します。</span><span class="sxs-lookup"><span data-stu-id="ae68a-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="ae68a-104">すべての数値型には定義済みの除算演算子があります。</span><span class="sxs-lookup"><span data-stu-id="ae68a-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="ae68a-105">コメント</span><span class="sxs-lookup"><span data-stu-id="ae68a-105">Remarks</span></span>  
 <span data-ttu-id="ae68a-106">ユーザー定義型は `/` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="ae68a-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="ae68a-107">`/` 演算子のオーバーロードは、[/= 演算子](division-assignment-operator.md)を暗黙的にオーバーロードします。</span><span class="sxs-lookup"><span data-stu-id="ae68a-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="ae68a-108">2 つの整数を除算した場合、結果は常に整数になります。</span><span class="sxs-lookup"><span data-stu-id="ae68a-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="ae68a-109">たとえば、7 / 3 の結果は 2 となります。</span><span class="sxs-lookup"><span data-stu-id="ae68a-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="ae68a-110">これを切り捨て除算と混同しないでください。`/` 演算子では 0 方向に丸められます。-7/3 は-2 になります。</span><span class="sxs-lookup"><span data-stu-id="ae68a-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="ae68a-111">有理数として商を取得するには、`float`、`double`、または `decimal` 型を使います。</span><span class="sxs-lookup"><span data-stu-id="ae68a-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="ae68a-112">[組み込み数値型](../../../csharp/language-reference/keywords/reference-tables-for-types.md)の間で変換を行う方法はたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="ae68a-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="ae68a-113">余りを計算するには、[剰余演算子](../../../csharp/language-reference/operators/remainder-operator.md) `%` を使います。</span><span class="sxs-lookup"><span data-stu-id="ae68a-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae68a-114">例</span><span class="sxs-lookup"><span data-stu-id="ae68a-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ae68a-115">参照</span><span class="sxs-lookup"><span data-stu-id="ae68a-115">See Also</span></span>  
 [<span data-ttu-id="ae68a-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ae68a-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ae68a-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ae68a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ae68a-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="ae68a-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
