---
title: '&lt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 24bf274bfcb0a8e19a79aafb3bd7920054044be0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271163"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="2b12b-102">&lt;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2b12b-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="2b12b-103">すべての数値型と列挙型で "以下" 関係演算子 (`<=`) が定義されます。これは、最初のオペランドが 2 番目のオペランドと等しいか、それより小さい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="2b12b-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b12b-104">コメント</span><span class="sxs-lookup"><span data-stu-id="2b12b-104">Remarks</span></span>  
 <span data-ttu-id="2b12b-105">ユーザー定義型は `<=` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="2b12b-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="2b12b-106">詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b12b-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="2b12b-107">`<=` をオーバーロードする場合は、[>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b12b-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="2b12b-108">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b12b-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b12b-109">例</span><span class="sxs-lookup"><span data-stu-id="2b12b-109">Example</span></span>  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2b12b-110">参照</span><span class="sxs-lookup"><span data-stu-id="2b12b-110">See Also</span></span>  
 [<span data-ttu-id="2b12b-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2b12b-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2b12b-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2b12b-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2b12b-113">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="2b12b-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="2b12b-114">explicit</span><span class="sxs-lookup"><span data-stu-id="2b12b-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
