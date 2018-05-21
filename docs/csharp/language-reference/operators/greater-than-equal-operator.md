---
title: '&gt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 02d9de34bf0293194f3a72bd5901d047e4cc5b2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="c928d-102">&gt;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c928d-102">&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="c928d-103">すべての数値型と列挙型で "以上" 関係演算子 `>=` が定義されます。これは、最初のオペランドが 2 番目のオペランドと等しいか、それより大きい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="c928d-103">All numeric and enumeration types define a "greater than or equal" relational operator, `>=` that returns `true` if the first operand is greater than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c928d-104">コメント</span><span class="sxs-lookup"><span data-stu-id="c928d-104">Remarks</span></span>  
 <span data-ttu-id="c928d-105">ユーザー定義型は `>=` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="c928d-105">User-defined types can overload the `>=` operator.</span></span> <span data-ttu-id="c928d-106">詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c928d-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="c928d-107">`>=` をオーバーロードする場合は、[<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c928d-107">If `>=` is overloaded, [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="c928d-108">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c928d-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c928d-109">例</span><span class="sxs-lookup"><span data-stu-id="c928d-109">Example</span></span>  
 [!code-csharp[csRefOperators#39](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c928d-110">参照</span><span class="sxs-lookup"><span data-stu-id="c928d-110">See Also</span></span>  
 [<span data-ttu-id="c928d-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="c928d-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c928d-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c928d-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c928d-113">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="c928d-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
