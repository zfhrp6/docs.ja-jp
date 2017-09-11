---
title: "&lt; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: 14
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
ms.openlocfilehash: 5d90a8e549b54fc229ac3ae5bb8f30ce3b55c0d4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="f1537-102">&lt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f1537-102">&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="f1537-103">すべての数値型と列挙型で "より小さい" 関係演算子 (`<`) が定義されます。これは、最初のオペランドが 2 番目のオペランドより小さい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="f1537-103">All numeric and enumeration types define a "less than" relational operator (`<`) that returns `true` if the first operand is less than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1537-104">コメント</span><span class="sxs-lookup"><span data-stu-id="f1537-104">Remarks</span></span>  
 <span data-ttu-id="f1537-105">ユーザー定義型は `<` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="f1537-105">User-defined types can overload the `<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="f1537-106">`<` をオーバーロードする場合は、[>](../../../csharp/language-reference/operators/greater-than-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1537-106">If `<` is overloaded, [>](../../../csharp/language-reference/operators/greater-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="f1537-107">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="f1537-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1537-108">例</span><span class="sxs-lookup"><span data-stu-id="f1537-108">Example</span></span>  
 <span data-ttu-id="f1537-109">[!code-cs[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f1537-109">[!code-cs[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1537-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1537-110">See Also</span></span>  
 <span data-ttu-id="f1537-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1537-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f1537-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1537-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f1537-113">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f1537-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

