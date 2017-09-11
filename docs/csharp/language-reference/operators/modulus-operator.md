---
title: "% 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
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
ms.openlocfilehash: 658b04f4bee952a20a7b0a740aa931fe4fad9cdf
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="4740c-102">% 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4740c-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="4740c-103">`%` 演算子は、最初のオペランドを 2 番目のオペランドで除算した後の剰余を計算します。</span><span class="sxs-lookup"><span data-stu-id="4740c-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="4740c-104">すべての数値型には定義済みの剰余演算子があります。</span><span class="sxs-lookup"><span data-stu-id="4740c-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4740c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4740c-105">Remarks</span></span>  
 <span data-ttu-id="4740c-106">ユーザー定義型は `%` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="4740c-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="4740c-107">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="4740c-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4740c-108">例</span><span class="sxs-lookup"><span data-stu-id="4740c-108">Example</span></span>  
 <span data-ttu-id="4740c-109">[!code-cs[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4740c-109">[!code-cs[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="4740c-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4740c-110">Comments</span></span>  
 <span data-ttu-id="4740c-111">double 型に関連する丸めエラーに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4740c-111">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4740c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4740c-112">See Also</span></span>  
 <span data-ttu-id="4740c-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4740c-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4740c-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4740c-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="4740c-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="4740c-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

