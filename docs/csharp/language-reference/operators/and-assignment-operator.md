---
title: "&amp;= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 15
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
ms.openlocfilehash: 6dec8de5077c07150ea37b88979e7b59b231d610
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="0bbfe-102">&amp;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0bbfe-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="0bbfe-103">AND 代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="0bbfe-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bbfe-104">コメント</span><span class="sxs-lookup"><span data-stu-id="0bbfe-104">Remarks</span></span>  
 <span data-ttu-id="0bbfe-105">次のような `&=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="0bbfe-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```  
x &= y  
```  
  
 <span data-ttu-id="0bbfe-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="0bbfe-106">is equivalent to</span></span>  
  
```  
x = x & y  
```  
  
 <span data-ttu-id="0bbfe-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="0bbfe-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0bbfe-108">[& 演算子](../../../csharp/language-reference/operators/and-operator.md)では、整数のオペランドではビットごとの論理 AND 演算、`bool` オペランドでは論理 AND 演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="0bbfe-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="0bbfe-109">`&=` 演算子は直接オーバーロードできませんが、[& 演算子](../../../csharp/language-reference/operators/and-operator.md)はユーザー定義型でオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="0bbfe-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bbfe-110">例</span><span class="sxs-lookup"><span data-stu-id="0bbfe-110">Example</span></span>  
 <span data-ttu-id="0bbfe-111">[!code-cs[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bbfe-111">[!code-cs[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bbfe-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bbfe-112">See Also</span></span>  
 <span data-ttu-id="0bbfe-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bbfe-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0bbfe-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bbfe-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="0bbfe-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="0bbfe-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

