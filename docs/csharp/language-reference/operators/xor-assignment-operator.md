---
title: ^= 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: b868f2cdbfa8a80f89a12e6194a30154481f0b07
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cfa90-102">^= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cfa90-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="cfa90-103">排他的 OR 代入演算子。</span><span class="sxs-lookup"><span data-stu-id="cfa90-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfa90-104">コメント</span><span class="sxs-lookup"><span data-stu-id="cfa90-104">Remarks</span></span>  
 <span data-ttu-id="cfa90-105">次のような形式の式があります。</span><span class="sxs-lookup"><span data-stu-id="cfa90-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="cfa90-106">これが次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="cfa90-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="cfa90-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="cfa90-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="cfa90-108">[^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)は整数オペランドにビット演算排他的 OR 操作を実行し、[ブール](../../../csharp/language-reference/keywords/bool.md) オペランドに論理的 OR 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="cfa90-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="cfa90-109">^= 演算子は直接オーバーロードできませんが、ユーザー定義型は [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="cfa90-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfa90-110">例</span><span class="sxs-lookup"><span data-stu-id="cfa90-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cfa90-111">参照</span><span class="sxs-lookup"><span data-stu-id="cfa90-111">See Also</span></span>  
 [<span data-ttu-id="cfa90-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="cfa90-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cfa90-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cfa90-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cfa90-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="cfa90-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
