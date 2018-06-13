---
title: '&gt;&gt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: ccc3f688d985b9e35404550f0c53a7acf8095dd5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171419"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="f7d7a-102">&gt;&gt;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f7d7a-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="f7d7a-103">右シフト代入演算子。</span><span class="sxs-lookup"><span data-stu-id="f7d7a-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7d7a-104">コメント</span><span class="sxs-lookup"><span data-stu-id="f7d7a-104">Remarks</span></span>  
 <span data-ttu-id="f7d7a-105">次のような形式の式があります。</span><span class="sxs-lookup"><span data-stu-id="f7d7a-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="f7d7a-106">これが次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="f7d7a-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="f7d7a-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="f7d7a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f7d7a-108">[>> 演算子](../../../csharp/language-reference/operators/right-shift-operator.md)は、`y` で指定された量だけ `x` を右にシフトします。</span><span class="sxs-lookup"><span data-stu-id="f7d7a-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="f7d7a-109">>>= 演算子は直接オーバーロードできませんが、ユーザー定義型は [>> 演算子](../../../csharp/language-reference/operators/right-shift-operator.md)をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="f7d7a-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7d7a-110">例</span><span class="sxs-lookup"><span data-stu-id="f7d7a-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f7d7a-111">参照</span><span class="sxs-lookup"><span data-stu-id="f7d7a-111">See Also</span></span>  
 [<span data-ttu-id="f7d7a-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f7d7a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f7d7a-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f7d7a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f7d7a-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f7d7a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
