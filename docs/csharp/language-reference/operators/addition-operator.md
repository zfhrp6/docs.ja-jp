---
title: "+ 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
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
ms.openlocfilehash: 5455375148f1924c7fe1cdb10e7924abb83a1565
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="6d2c3-102">+ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6d2c3-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="6d2c3-103">`+` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d2c3-104">コメント</span><span class="sxs-lookup"><span data-stu-id="6d2c3-104">Remarks</span></span>  
 <span data-ttu-id="6d2c3-105">すべての数値型には、単項 `+` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="6d2c3-106">数値型に対する単項 `+` 演算の結果は、単にそのオペランドの値になります。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="6d2c3-107">数値型と文字列型には、2 項 `+` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="6d2c3-108">数値型の場合、+ の 2 つのオペランドの合計が計算されます。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="6d2c3-109">一方または両方のオペランドが文字列型である場合、+ は、そのオペランドの文字列表現を連結します。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="6d2c3-110">2 項 `+` 演算子はデリゲート型にも備わっており、その場合、デリゲートの連結が実行されます。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="6d2c3-111">単項 `+` 演算子と 2 項 `+` 演算子は、ユーザー定義型でオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="6d2c3-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="6d2c3-113">詳細については、「[operator (C# Reference) (operator (C# リファレンス))](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d2c3-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d2c3-114">例</span><span class="sxs-lookup"><span data-stu-id="6d2c3-114">Example</span></span>  
 <span data-ttu-id="6d2c3-115">[!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d2c3-115">[!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6d2c3-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6d2c3-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d2c3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d2c3-117">See Also</span></span>  
 <span data-ttu-id="6d2c3-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d2c3-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6d2c3-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d2c3-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6d2c3-120">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d2c3-120">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="6d2c3-121">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6d2c3-121">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)

