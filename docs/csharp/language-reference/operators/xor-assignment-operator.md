---
title: "^= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
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
ms.openlocfilehash: 33b0dccf5031809bb4fcb73d0f7d6a344accdea3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="bca6b-102">^= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bca6b-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="bca6b-103">排他的 OR 代入演算子。</span><span class="sxs-lookup"><span data-stu-id="bca6b-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca6b-104">コメント</span><span class="sxs-lookup"><span data-stu-id="bca6b-104">Remarks</span></span>  
 <span data-ttu-id="bca6b-105">次のような形式の式があります。</span><span class="sxs-lookup"><span data-stu-id="bca6b-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="bca6b-106">これが次として評価されます。</span><span class="sxs-lookup"><span data-stu-id="bca6b-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="bca6b-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="bca6b-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="bca6b-108">[^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)は整数オペランドにビット演算排他的 OR 操作を実行し、[ブール](../../../csharp/language-reference/keywords/bool.md) オペランドに論理的 OR 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="bca6b-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="bca6b-109">^= 演算子は直接オーバーロードできませんが、ユーザー定義型は [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="bca6b-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca6b-110">例</span><span class="sxs-lookup"><span data-stu-id="bca6b-110">Example</span></span>  
 <span data-ttu-id="bca6b-111">[!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bca6b-111">[!code-cs[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca6b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bca6b-112">See Also</span></span>  
 <span data-ttu-id="bca6b-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bca6b-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bca6b-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bca6b-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="bca6b-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="bca6b-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

