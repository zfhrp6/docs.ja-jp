---
title: "- 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: 19
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
ms.openlocfilehash: 7fabdab8593ff4d721b352b59a45f51721f53eb4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="--operator-c-reference"></a><span data-ttu-id="f7d4a-102">- 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f7d4a-102">- Operator (C# Reference)</span></span>
<span data-ttu-id="f7d4a-103">`-` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-103">The `-` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7d4a-104">コメント</span><span class="sxs-lookup"><span data-stu-id="f7d4a-104">Remarks</span></span>  
 <span data-ttu-id="f7d4a-105">すべての数値型には、単項 `-` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="f7d4a-106">数値型に対する単項 `-` 演算の結果は、オペランドの反転の数値となります。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>  
  
 <span data-ttu-id="f7d4a-107">最初のオペランドから 2 番目のオペランドを減算するために、すべての数値型と列挙型に 2 項 `-` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>  
  
 <span data-ttu-id="f7d4a-108">2 項 `-` 演算子はデリゲート型にも備わっており、その場合、デリゲートの削除が実行されます。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>  
  
 <span data-ttu-id="f7d4a-109">単項 `-` 演算子と 2 項 `-` 演算子は、ユーザー定義型でオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="f7d4a-110">詳細については、「[operator (C# Reference) (operator (C# リファレンス))](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7d4a-110">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7d4a-111">例</span><span class="sxs-lookup"><span data-stu-id="f7d4a-111">Example</span></span>  
 <span data-ttu-id="f7d4a-112">[!code-cs[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f7d4a-112">[!code-cs[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d4a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7d4a-113">See Also</span></span>  
 <span data-ttu-id="f7d4a-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f7d4a-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f7d4a-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f7d4a-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f7d4a-116">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f7d4a-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

