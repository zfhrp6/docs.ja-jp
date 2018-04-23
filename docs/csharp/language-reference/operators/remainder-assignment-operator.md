---
title: '%= 演算子 (C# リファレンス)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 864b96dcf16e4756cd0e74a6e02297660e72357e
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bf4b5-102">%= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bf4b5-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="bf4b5-103">剰余代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="bf4b5-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf4b5-104">コメント</span><span class="sxs-lookup"><span data-stu-id="bf4b5-104">Remarks</span></span>  
 <span data-ttu-id="bf4b5-105">次のような `%=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="bf4b5-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="bf4b5-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="bf4b5-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="bf4b5-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="bf4b5-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="bf4b5-108">[% 演算子](../../../csharp/language-reference/operators/remainder-operator.md)は、数値型の除算後の剰余を計算するために事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="bf4b5-108">The [% operator](../../../csharp/language-reference/operators/remainder-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="bf4b5-109">`%=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [% 演算子](../../../csharp/language-reference/operators/remainder-operator.md)をオーバーロードできます (「[operator (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="bf4b5-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf4b5-110">例</span><span class="sxs-lookup"><span data-stu-id="bf4b5-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bf4b5-111">参照</span><span class="sxs-lookup"><span data-stu-id="bf4b5-111">See Also</span></span>  
 [<span data-ttu-id="bf4b5-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="bf4b5-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bf4b5-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="bf4b5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bf4b5-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="bf4b5-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
