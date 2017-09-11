---
title: "|= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '|=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
caps.latest.revision: 16
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
ms.openlocfilehash: f1c0a92414739efc2ab091871e80852737fdf931
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="09a3c-102">|= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="09a3c-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="09a3c-103">OR 代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="09a3c-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09a3c-104">コメント</span><span class="sxs-lookup"><span data-stu-id="09a3c-104">Remarks</span></span>  
 <span data-ttu-id="09a3c-105">次のような `|=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="09a3c-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```  
x |= y  
```  
  
 <span data-ttu-id="09a3c-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="09a3c-106">is equivalent to</span></span>  
  
```  
x = x | y  
```  
  
 <span data-ttu-id="09a3c-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="09a3c-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="09a3c-108">[&#124; 演算子](../../../csharp/language-reference/operators/or-operator.md)では、整数のオペランドではビットごとの論理 OR 演算、ブール オペランドでは論理 OR 演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="09a3c-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="09a3c-109">`|=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [&#124; 演算子](../../../csharp/language-reference/operators/or-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="09a3c-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09a3c-110">例</span><span class="sxs-lookup"><span data-stu-id="09a3c-110">Example</span></span>  
 <span data-ttu-id="09a3c-111">[!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="09a3c-111">[!code-cs[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a3c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="09a3c-112">See Also</span></span>  
 <span data-ttu-id="09a3c-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="09a3c-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="09a3c-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="09a3c-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="09a3c-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="09a3c-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

