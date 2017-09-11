---
title: "~ 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
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
ms.openlocfilehash: ffbfc379b7c021ccd8fbed9b796aa9fda6618b55
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="aff02-102">~ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="aff02-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="aff02-103">`~` 演算子は、ビット単位の補数演算をオペランドに実行します。これにより、各ビットが反転します。</span><span class="sxs-lookup"><span data-stu-id="aff02-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="aff02-104">ビット単位の補数演算は [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) に事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="aff02-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff02-105">`~` シンボルもファイナライザーの宣言に使用されます。</span><span class="sxs-lookup"><span data-stu-id="aff02-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="aff02-106">詳細については、「[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md)」 (ファイナライザー) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aff02-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff02-107">コメント</span><span class="sxs-lookup"><span data-stu-id="aff02-107">Remarks</span></span>  
 <span data-ttu-id="aff02-108">ユーザー定義型は `~` 演算子をオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="aff02-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="aff02-109">詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aff02-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="aff02-110">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="aff02-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aff02-111">例</span><span class="sxs-lookup"><span data-stu-id="aff02-111">Example</span></span>  
 <span data-ttu-id="aff02-112">[!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="aff02-112">[!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff02-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="aff02-113">See Also</span></span>  
 <span data-ttu-id="aff02-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="aff02-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="aff02-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="aff02-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="aff02-116">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="aff02-116">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="aff02-117">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="aff02-117">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

