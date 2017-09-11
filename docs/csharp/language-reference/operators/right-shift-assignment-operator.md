---
title: "&gt;&gt;= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 14
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
ms.openlocfilehash: 64f387e475681ffc76f113435ba090b40780dda3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="dd23d-102">&gt;&gt;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dd23d-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="dd23d-103">右シフト代入演算子。</span><span class="sxs-lookup"><span data-stu-id="dd23d-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd23d-104">コメント</span><span class="sxs-lookup"><span data-stu-id="dd23d-104">Remarks</span></span>  
 <span data-ttu-id="dd23d-105">次のような形式の式があります。</span><span class="sxs-lookup"><span data-stu-id="dd23d-105">An expression of the form</span></span>  
  
```  
x >>= y  
```  
  
 <span data-ttu-id="dd23d-106">これが次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="dd23d-106">is evaluated as</span></span>  
  
```  
x = x >> y  
```  
  
 <span data-ttu-id="dd23d-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="dd23d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="dd23d-108">[>> 演算子](../../../csharp/language-reference/operators/right-shift-operator.md)は、`y` で指定された量だけ `x` を右にシフトします。</span><span class="sxs-lookup"><span data-stu-id="dd23d-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="dd23d-109">>>= 演算子は直接オーバーロードできませんが、ユーザー定義型は [>> 演算子](../../../csharp/language-reference/operators/right-shift-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="dd23d-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd23d-110">例</span><span class="sxs-lookup"><span data-stu-id="dd23d-110">Example</span></span>  
 <span data-ttu-id="dd23d-111">[!code-cs[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dd23d-111">[!code-cs[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd23d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd23d-112">See Also</span></span>  
 <span data-ttu-id="dd23d-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd23d-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="dd23d-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dd23d-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="dd23d-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="dd23d-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

