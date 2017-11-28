---
title: "% 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a8929-102">% 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a8929-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="a8929-103">`%` 演算子は、最初のオペランドを 2 番目のオペランドで除算した後の剰余を計算します。</span><span class="sxs-lookup"><span data-stu-id="a8929-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="a8929-104">すべての数値型には定義済みの剰余演算子があります。</span><span class="sxs-lookup"><span data-stu-id="a8929-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8929-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a8929-105">Remarks</span></span>  
 <span data-ttu-id="a8929-106">ユーザー定義型は `%` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="a8929-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="a8929-107">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="a8929-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8929-108">例</span><span class="sxs-lookup"><span data-stu-id="a8929-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="a8929-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a8929-109">Comments</span></span>  
 <span data-ttu-id="a8929-110">double 型に関連する丸めエラーに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a8929-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8929-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8929-111">See Also</span></span>  
 [<span data-ttu-id="a8929-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a8929-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a8929-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a8929-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8929-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="a8929-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
