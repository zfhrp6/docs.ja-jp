---
title: "^= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ee858-102">^= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ee858-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="ee858-103">排他的 OR 代入演算子。</span><span class="sxs-lookup"><span data-stu-id="ee858-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee858-104">コメント</span><span class="sxs-lookup"><span data-stu-id="ee858-104">Remarks</span></span>  
 <span data-ttu-id="ee858-105">次のような形式の式があります。</span><span class="sxs-lookup"><span data-stu-id="ee858-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="ee858-106">これが次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="ee858-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="ee858-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="ee858-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="ee858-108">[^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)は整数オペランドにビット演算排他的 OR 操作を実行し、[ブール](../../../csharp/language-reference/keywords/bool.md) オペランドに論理的 OR 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee858-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="ee858-109">^= 演算子は直接オーバーロードできませんが、ユーザー定義型は [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="ee858-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee858-110">例</span><span class="sxs-lookup"><span data-stu-id="ee858-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ee858-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee858-111">See Also</span></span>  
 [<span data-ttu-id="ee858-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ee858-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ee858-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ee858-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ee858-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="ee858-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
