---
title: "&gt; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
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
ms.openlocfilehash: 5b4eb1f6fcca311fc772e4dbe0ce0391201af3de
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="887be-102">&gt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="887be-102">&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="887be-103">すべての数値型と列挙型で "より大きい" 関係演算子 (`>`) が定義されます。これは、最初のオペランドが 2 番目のオペランドより大きい場合に `true` を返し、それ以外の場合、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="887be-103">All numeric and enumeration types define a "greater than" relational operator (`>`) that returns `true` if the first operand is greater than the second, `false` otherwise.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="887be-104">コメント</span><span class="sxs-lookup"><span data-stu-id="887be-104">Remarks</span></span>  
 <span data-ttu-id="887be-105">ユーザー定義型は `>` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="887be-105">User-defined types can overload the `>` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="887be-106">`>` をオーバーロードする場合は、[<](../../../csharp/language-reference/operators/less-than-operator.md) もオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="887be-106">If `>` is overloaded, [<](../../../csharp/language-reference/operators/less-than-operator.md) must also be overloaded.</span></span> <span data-ttu-id="887be-107">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="887be-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="887be-108">例</span><span class="sxs-lookup"><span data-stu-id="887be-108">Example</span></span>  
 <span data-ttu-id="887be-109">[!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="887be-109">[!code-cs[csRefOperators#29](../../../csharp/language-reference/operators/codesnippet/CSharp/greater-than-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887be-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="887be-110">See Also</span></span>  
 <span data-ttu-id="887be-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="887be-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="887be-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="887be-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="887be-113">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="887be-113">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="887be-114">explicit</span><span class="sxs-lookup"><span data-stu-id="887be-114">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)

