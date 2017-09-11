---
title: "&amp; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d92a860df6fcc9acf14aab4ec558556735ac8aac
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="2bc63-102">&amp; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2bc63-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="2bc63-103">& 演算子には、単項演算子としての働きと 2 項演算子としての働きがあります。</span><span class="sxs-lookup"><span data-stu-id="2bc63-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc63-104">コメント</span><span class="sxs-lookup"><span data-stu-id="2bc63-104">Remarks</span></span>  
 <span data-ttu-id="2bc63-105">単項 & 演算子では、オペランドのアドレスが返されます ([unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストが必要)。</span><span class="sxs-lookup"><span data-stu-id="2bc63-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="2bc63-106">整数型と `bool` には、2 項 & 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="2bc63-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="2bc63-107">整数型の場合、& はオペランドのビットごとの論理 AND を計算します。</span><span class="sxs-lookup"><span data-stu-id="2bc63-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="2bc63-108">`bool` オペランドの場合、& は、そのオペランドの論理 AND を計算します。つまり、結果は、両方のオペランドが `true` の場合にのみ `true` になります。</span><span class="sxs-lookup"><span data-stu-id="2bc63-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="2bc63-109">`&` 演算子は、最初の演算子の値に関係なく、両方の演算子を評価します。</span><span class="sxs-lookup"><span data-stu-id="2bc63-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="2bc63-110">例:</span><span class="sxs-lookup"><span data-stu-id="2bc63-110">For example:</span></span>  
  
 <span data-ttu-id="2bc63-111">[!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bc63-111">[!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="2bc63-112">ユーザー定義型は二項 `&` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="2bc63-112">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2bc63-113">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bc63-113">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="2bc63-114">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="2bc63-114">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bc63-115">例</span><span class="sxs-lookup"><span data-stu-id="2bc63-115">Example</span></span>  
 <span data-ttu-id="2bc63-116">[!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bc63-116">[!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc63-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bc63-117">See Also</span></span>  
 <span data-ttu-id="2bc63-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bc63-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2bc63-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bc63-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="2bc63-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="2bc63-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

