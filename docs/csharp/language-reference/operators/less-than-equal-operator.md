---
title: "&lt;= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
caps.latest.revision: 16
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
ms.openlocfilehash: 931843783888a844d9f90f273b2362d327e8ccbc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="de8f4-102">&lt;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="de8f4-102">&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="de8f4-103">すべての数値型と列挙型で "以下" 関係演算子 (`<=`) が定義されます。これは、最初のオペランドが 2 番目のオペランドと等しいか、それより小さい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="de8f4-103">All numeric and enumeration types define a "less than or equal" relational operator (`<=`) that returns `true` if the first operand is less than or equal to the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de8f4-104">コメント</span><span class="sxs-lookup"><span data-stu-id="de8f4-104">Remarks</span></span>  
 <span data-ttu-id="de8f4-105">ユーザー定義型は `<=` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="de8f4-105">User-defined types can overload the `<=` operator.</span></span> <span data-ttu-id="de8f4-106">詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de8f4-106">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="de8f4-107">`<=` をオーバーロードする場合は、[>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="de8f4-107">If `<=` is overloaded, [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="de8f4-108">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="de8f4-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de8f4-109">例</span><span class="sxs-lookup"><span data-stu-id="de8f4-109">Example</span></span>  
 <span data-ttu-id="de8f4-110">[!code-cs[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="de8f4-110">[!code-cs[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8f4-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="de8f4-111">See Also</span></span>  
 <span data-ttu-id="de8f4-112">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="de8f4-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="de8f4-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="de8f4-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="de8f4-114">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="de8f4-114">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="de8f4-115">explicit</span><span class="sxs-lookup"><span data-stu-id="de8f4-115">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)

