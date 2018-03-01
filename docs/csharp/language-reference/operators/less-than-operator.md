---
title: "&lt; 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="1e7ab-102">&lt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1e7ab-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="1e7ab-103">すべての数値型と列挙型で "より小さい" 関係演算子 (`<`) が定義されます。これは、最初のオペランドが 2 番目のオペランドより小さい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="1e7ab-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e7ab-104">コメント</span><span class="sxs-lookup"><span data-stu-id="1e7ab-104">Remarks</span></span>  
 <span data-ttu-id="1e7ab-105">ユーザー定義型は `<` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="1e7ab-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1e7ab-106">`<` をオーバーロードする場合は、[>](../../../csharp/language-reference/operators/greater-than-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e7ab-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="1e7ab-107">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="1e7ab-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e7ab-108">例</span><span class="sxs-lookup"><span data-stu-id="1e7ab-108">Example</span></span>  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1e7ab-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e7ab-109">See Also</span></span>  
 [<span data-ttu-id="1e7ab-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="1e7ab-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1e7ab-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1e7ab-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1e7ab-112">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="1e7ab-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
