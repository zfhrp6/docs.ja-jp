---
title: '&amp; 演算子 (C# リファレンス)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f26305bfa1e8c9ba45493ad2ab4937d554590911
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="336b0-102">&amp; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="336b0-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="336b0-103">`&` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。</span><span class="sxs-lookup"><span data-stu-id="336b0-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="336b0-104">コメント</span><span class="sxs-lookup"><span data-stu-id="336b0-104">Remarks</span></span>  
 <span data-ttu-id="336b0-105">単項 `&` 演算子では、オペランドのアドレスが返されます ([unsafe](../../../csharp/language-reference/keywords/unsafe.md) コンテキストが必要)。</span><span class="sxs-lookup"><span data-stu-id="336b0-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="336b0-106">整数型と `bool` には、2 項 `&` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="336b0-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="336b0-107">整数型の場合、& はオペランドのビットごとの論理 AND を計算します。</span><span class="sxs-lookup"><span data-stu-id="336b0-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="336b0-108">`bool` オペランドの場合、& は、そのオペランドの論理 AND を計算します。つまり、結果は、両方のオペランドが `true` の場合にのみ `true` になります。</span><span class="sxs-lookup"><span data-stu-id="336b0-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="336b0-109">バイナリ `&` 演算子は、[条件 AND 演算子](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&` とは対照的に、最初の演算子の値に関係なく、両方の演算子を評価します。</span><span class="sxs-lookup"><span data-stu-id="336b0-109">The binary `&` operator evaluates both operators regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="336b0-110">例:</span><span class="sxs-lookup"><span data-stu-id="336b0-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="336b0-111">ユーザー定義型は二項 `&` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="336b0-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="336b0-112">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="336b0-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="336b0-113">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="336b0-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="336b0-114">例</span><span class="sxs-lookup"><span data-stu-id="336b0-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="336b0-115">参照</span><span class="sxs-lookup"><span data-stu-id="336b0-115">See Also</span></span>  
 [<span data-ttu-id="336b0-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="336b0-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="336b0-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="336b0-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="336b0-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="336b0-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
