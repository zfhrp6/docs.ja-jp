---
title: "/= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
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
ms.openlocfilehash: 5e105bf11f5413d77d62be4177ed22ba420312c3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="f72f6-102">/= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f72f6-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="f72f6-103">除算代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="f72f6-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f72f6-104">コメント</span><span class="sxs-lookup"><span data-stu-id="f72f6-104">Remarks</span></span>  
 <span data-ttu-id="f72f6-105">次のような `/=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="f72f6-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="f72f6-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="f72f6-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="f72f6-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="f72f6-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f72f6-108">[/ 演算子](../../../csharp/language-reference/operators/division-operator.md)は、数値型の除算のために事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="f72f6-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="f72f6-109">`/=` 演算子は直接オーバーロードできませんが、ユーザー定義型では [/ 演算子](../../../csharp/language-reference/operators/division-operator.md)をオーバーロードできます。(「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="f72f6-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="f72f6-110">すべての複合代入演算子において、二項演算子をオーバーロードすると、同等の複合代入が暗黙的にオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="f72f6-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f72f6-111">例</span><span class="sxs-lookup"><span data-stu-id="f72f6-111">Example</span></span>  
 <span data-ttu-id="f72f6-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f72f6-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72f6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f72f6-113">See Also</span></span>  
 <span data-ttu-id="f72f6-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f72f6-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f72f6-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f72f6-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f72f6-116">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f72f6-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

