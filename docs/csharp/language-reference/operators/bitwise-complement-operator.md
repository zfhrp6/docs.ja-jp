---
title: "~ 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9b0cabcb101fce8422b1390ec8c4cb3b3849631
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9afb1-102">~ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9afb1-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="9afb1-103">`~` 演算子は、ビット単位の補数演算をオペランドに実行します。これにより、各ビットが反転します。</span><span class="sxs-lookup"><span data-stu-id="9afb1-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="9afb1-104">ビット単位の補数演算は [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) に事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="9afb1-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9afb1-105">`~` シンボルもファイナライザーの宣言に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9afb1-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="9afb1-106">詳細については、「[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md)」 (ファイナライザー) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9afb1-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9afb1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="9afb1-107">Remarks</span></span>  
 <span data-ttu-id="9afb1-108">ユーザー定義型は `~` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="9afb1-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="9afb1-109">詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9afb1-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="9afb1-110">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="9afb1-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9afb1-111">例</span><span class="sxs-lookup"><span data-stu-id="9afb1-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9afb1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9afb1-112">See Also</span></span>  
 [<span data-ttu-id="9afb1-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="9afb1-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9afb1-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9afb1-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9afb1-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="9afb1-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="9afb1-116">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="9afb1-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
