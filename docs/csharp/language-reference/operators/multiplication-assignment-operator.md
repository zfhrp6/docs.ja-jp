---
title: "*= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
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
ms.openlocfilehash: 2969ba3ce303da591353fd0114dccf752e63f2c3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="67b87-102">*= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="67b87-102">*= Operator (C# Reference)</span></span>
<span data-ttu-id="67b87-103">二項乗算代入演算子です。</span><span class="sxs-lookup"><span data-stu-id="67b87-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67b87-104">コメント</span><span class="sxs-lookup"><span data-stu-id="67b87-104">Remarks</span></span>  
 <span data-ttu-id="67b87-105">次のような `*=` 代入演算子を使用する式があるとします</span><span class="sxs-lookup"><span data-stu-id="67b87-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="67b87-106">上記の式は、次の式と同じです。</span><span class="sxs-lookup"><span data-stu-id="67b87-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="67b87-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="67b87-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="67b87-108">[* 演算子](../../../csharp/language-reference/operators/multiplication-operator.md)は、数値型の乗算のために事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="67b87-108">The [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="67b87-109">`*=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [* 演算子](../../../csharp/language-reference/operators/multiplication-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="67b87-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67b87-110">例</span><span class="sxs-lookup"><span data-stu-id="67b87-110">Example</span></span>  
 <span data-ttu-id="67b87-111">[!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="67b87-111">[!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b87-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="67b87-112">See Also</span></span>  
 <span data-ttu-id="67b87-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="67b87-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="67b87-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="67b87-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="67b87-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="67b87-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

