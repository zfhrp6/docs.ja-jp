---
title: "%= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8da6f-102">%= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8da6f-102">%= Operator (C# Reference)</span></span>
<span data-ttu-id="8da6f-103">剰余代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="8da6f-103">The remainder assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8da6f-104">コメント</span><span class="sxs-lookup"><span data-stu-id="8da6f-104">Remarks</span></span>  
 <span data-ttu-id="8da6f-105">次のような `%=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="8da6f-105">An expression using the `%=` assignment operator, such as</span></span>  
  
```  
x %= y  
```  
  
 <span data-ttu-id="8da6f-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="8da6f-106">is equivalent to</span></span>  
  
```  
x = x % y  
```  
  
 <span data-ttu-id="8da6f-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="8da6f-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="8da6f-108">[% 演算子](../../../csharp/language-reference/operators/modulus-operator.md)は、数値型の除算後の剰余を計算するために事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="8da6f-108">The [% operator](../../../csharp/language-reference/operators/modulus-operator.md) is predefined for numeric types to compute the remainder after division.</span></span>  
  
 <span data-ttu-id="8da6f-109">`%=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [% 演算子](../../../csharp/language-reference/operators/modulus-operator.md)をオーバーロードできます (「[operator (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="8da6f-109">The `%=` operator cannot be overloaded directly, but user-defined types can overload the [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8da6f-110">例</span><span class="sxs-lookup"><span data-stu-id="8da6f-110">Example</span></span>  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8da6f-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8da6f-111">See Also</span></span>  
 [<span data-ttu-id="8da6f-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="8da6f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8da6f-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8da6f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8da6f-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="8da6f-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
