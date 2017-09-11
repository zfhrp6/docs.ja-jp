---
title: "&amp;&amp; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
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
ms.openlocfilehash: 1da61947cbc85e5b3045513e99e013d1e4fae4b3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="07334-102">&amp;&amp; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="07334-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="07334-103">条件 AND 演算子 (`&&`) では `bool` オペランドの論理 AND が実行されますが、2 番目のオペランドは必要な場合にのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="07334-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07334-104">コメント</span><span class="sxs-lookup"><span data-stu-id="07334-104">Remarks</span></span>  
 <span data-ttu-id="07334-105">次の演算は、</span><span class="sxs-lookup"><span data-stu-id="07334-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="07334-106">次の演算に対応しています。</span><span class="sxs-lookup"><span data-stu-id="07334-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="07334-107">ただし `x` が `false` の場合は、AND 演算の結果は `y` の値に関係なく `false` となるため、`y` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="07334-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="07334-108">これは、"ショートサーキット" 評価と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="07334-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="07334-109">条件 AND 演算子はオーバーロードできませんが、通常の論理演算子、[true](../../../csharp/language-reference/keywords/true.md) 演算子、[false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、条件論理演算子の制約付きのオーバーロードとも見なされます。</span><span class="sxs-lookup"><span data-stu-id="07334-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07334-110">例</span><span class="sxs-lookup"><span data-stu-id="07334-110">Example</span></span>  
 <span data-ttu-id="07334-111">次の例では、2 番目の `if` ステートメントの条件式で最初のオペランドのみが評価されます。これは、このオペランドが `false` を返すからです。</span><span class="sxs-lookup"><span data-stu-id="07334-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 <span data-ttu-id="07334-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="07334-112">[!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="07334-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="07334-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="07334-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="07334-114">See Also</span></span>  
 <span data-ttu-id="07334-115">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="07334-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="07334-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="07334-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="07334-117">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="07334-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

