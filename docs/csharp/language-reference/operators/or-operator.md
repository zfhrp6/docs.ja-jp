---
title: "| 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
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
ms.openlocfilehash: 7524e246df35154ac04e46f2b43edded71be34b1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="d02bc-102">| 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d02bc-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="d02bc-103">整数型と `bool` には、2 項 `|` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="d02bc-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="d02bc-104">整数型の場合、`|` はそのオペランドのビットごとの OR を計算します。</span><span class="sxs-lookup"><span data-stu-id="d02bc-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="d02bc-105">`bool` オペランドの場合、`|` は、そのオペランドの論理 OR を計算します。つまり、結果は、両方のオペランドが `false` の場合にのみ `false` になります。</span><span class="sxs-lookup"><span data-stu-id="d02bc-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d02bc-106">コメント</span><span class="sxs-lookup"><span data-stu-id="d02bc-106">Remarks</span></span>  
 <span data-ttu-id="d02bc-107">ユーザー定義型は `|` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="d02bc-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d02bc-108">例</span><span class="sxs-lookup"><span data-stu-id="d02bc-108">Example</span></span>  
 <span data-ttu-id="d02bc-109">[!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d02bc-109">[!code-cs[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02bc-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d02bc-110">See Also</span></span>  
 <span data-ttu-id="d02bc-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d02bc-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d02bc-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d02bc-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d02bc-113">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="d02bc-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

