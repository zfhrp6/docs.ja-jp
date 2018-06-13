---
title: '| 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 7b62af53f0d8b7cba29f4496887717f1726eabf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265688"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="83196-102">| 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="83196-102">| Operator (C# Reference)</span></span>
<span data-ttu-id="83196-103">整数型と `bool` には、2 項 `|` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="83196-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="83196-104">整数型の場合、`|` はそのオペランドのビットごとの OR を計算します。</span><span class="sxs-lookup"><span data-stu-id="83196-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="83196-105">`bool` オペランドの場合、`|` は、そのオペランドの論理 OR を計算します。つまり、結果は、両方のオペランドが `false` の場合にのみ `false` になります。</span><span class="sxs-lookup"><span data-stu-id="83196-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83196-106">コメント</span><span class="sxs-lookup"><span data-stu-id="83196-106">Remarks</span></span>  
 <span data-ttu-id="83196-107">ユーザー定義型は `|` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="83196-107">User-defined types can overload the `|` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83196-108">例</span><span class="sxs-lookup"><span data-stu-id="83196-108">Example</span></span>  
 [!code-csharp[csRefOperators#31](../../../csharp/language-reference/operators/codesnippet/CSharp/or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="83196-109">参照</span><span class="sxs-lookup"><span data-stu-id="83196-109">See Also</span></span>  
 [<span data-ttu-id="83196-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="83196-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="83196-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="83196-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83196-112">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="83196-112">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
