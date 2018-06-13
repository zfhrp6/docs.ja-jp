---
title: '&gt; 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 1589c5e785b33db6106a0ef0a58202e771db9fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273499"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="988ac-102">&gt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="988ac-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="988ac-103">すべての数値型と列挙型で "より大きい" 関係演算子 (`>`) が定義されます。これは、最初のオペランドが 2 番目のオペランドより大きい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="988ac-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="988ac-104">コメント</span><span class="sxs-lookup"><span data-stu-id="988ac-104">Remarks</span></span>  
 <span data-ttu-id="988ac-105">ユーザー定義型は `>` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="988ac-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="988ac-106">`>` をオーバーロードする場合は、[<](../../../csharp/language-reference/operators/less-than-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="988ac-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="988ac-107">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="988ac-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="988ac-108">例</span><span class="sxs-lookup"><span data-stu-id="988ac-108">Example</span></span>  
 [!code-csharp[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="988ac-109">参照</span><span class="sxs-lookup"><span data-stu-id="988ac-109">See Also</span></span>  
 [<span data-ttu-id="988ac-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="988ac-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="988ac-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="988ac-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="988ac-112">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="988ac-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="988ac-113">explicit</span><span class="sxs-lookup"><span data-stu-id="988ac-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
