---
title: "&lt;&lt; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
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
ms.openlocfilehash: 4e6ad17232ec4eb087ca300342331af6a30789b1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="3d850-102">&lt;&lt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="3d850-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="3d850-103">左シフト演算子 (`<<`) は、最初のオペランドを 2 番目のオペランドで指定されたビット数だけ左にシフトします。</span><span class="sxs-lookup"><span data-stu-id="3d850-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="3d850-104">2 番目のオペランドの型は、[int](../../../csharp/language-reference/keywords/int.md) または事前に定義された `int` への暗黙的な数値変換を持つ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d850-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d850-105">コメント</span><span class="sxs-lookup"><span data-stu-id="3d850-105">Remarks</span></span>  
 <span data-ttu-id="3d850-106">最初のオペランドが [int](../../../csharp/language-reference/keywords/int.md) または [uint](../../../csharp/language-reference/keywords/uint.md) (32 ビット値) である場合、シフト数は、2 番目のオペランドの下位 5 ビットで指定されます。</span><span class="sxs-lookup"><span data-stu-id="3d850-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="3d850-107">つまり、実際のシフト数は、0 - 31 ビットです。</span><span class="sxs-lookup"><span data-stu-id="3d850-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="3d850-108">最初のオペランドが [long](../../../csharp/language-reference/keywords/long.md) または [ulong](../../../csharp/language-reference/keywords/ulong.md) (64 ビット値) である場合、シフト数は、2 番目のオペランドの下位 6 ビットで指定されます。</span><span class="sxs-lookup"><span data-stu-id="3d850-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="3d850-109">つまり、実際のシフト数は、0 - 63 ビットです。</span><span class="sxs-lookup"><span data-stu-id="3d850-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="3d850-110">シフトが破棄された後に最初のオペランドの型の範囲内に含まれないすべての上位ビットおよび下位の空のビットはゼロで埋められます。</span><span class="sxs-lookup"><span data-stu-id="3d850-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="3d850-111">シフト演算ではオーバーフローは発生しません。</span><span class="sxs-lookup"><span data-stu-id="3d850-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="3d850-112">ユーザー定義型は、`<<` 演算子をオーバーロードすることができます (「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照)。最初のオペランドの型は、ユーザー定義型である必要があり、2 番目のオペランドの型は `int` でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="3d850-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="3d850-113">二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="3d850-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d850-114">例</span><span class="sxs-lookup"><span data-stu-id="3d850-114">Example</span></span>  
 <span data-ttu-id="3d850-115">[!code-cs[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3d850-115">[!code-cs[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]</span></span>  
  
## <a name="comments"></a><span data-ttu-id="3d850-116">コメント</span><span class="sxs-lookup"><span data-stu-id="3d850-116">Comments</span></span>  
 <span data-ttu-id="3d850-117">1 と 33 は同じ下位 5 ビットを持つため、`i<<1` と `i<<33` は、同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="3d850-117">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d850-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d850-118">See Also</span></span>  
 <span data-ttu-id="3d850-119">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d850-119">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="3d850-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d850-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3d850-121">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="3d850-121">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

