---
title: ~ 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a4529-102">~ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a4529-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="a4529-103">`~` 演算子は、ビット単位の補数演算をオペランドに実行します。これにより、各ビットが反転します。</span><span class="sxs-lookup"><span data-stu-id="a4529-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="a4529-104">ビット単位の補数演算は [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) に事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="a4529-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4529-105">`~` シンボルもファイナライザーの宣言に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4529-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="a4529-106">詳細については、「[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md)」 (ファイナライザー) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4529-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4529-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a4529-107">Remarks</span></span>  
 <span data-ttu-id="a4529-108">ユーザー定義型は `~` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="a4529-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="a4529-109">詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4529-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="a4529-110">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4529-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4529-111">例</span><span class="sxs-lookup"><span data-stu-id="a4529-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a4529-112">参照</span><span class="sxs-lookup"><span data-stu-id="a4529-112">See Also</span></span>  
 [<span data-ttu-id="a4529-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a4529-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a4529-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a4529-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a4529-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="a4529-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="a4529-116">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="a4529-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
