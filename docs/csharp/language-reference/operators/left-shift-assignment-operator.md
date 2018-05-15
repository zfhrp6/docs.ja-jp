---
title: '&lt;&lt;= 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 9e2dbf693f7bee16c2ce97ccc7d52a318b8a3906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="0ede4-102">&lt;&lt;= 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0ede4-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="0ede4-103">左シフト代入演算子。</span><span class="sxs-lookup"><span data-stu-id="0ede4-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ede4-104">コメント</span><span class="sxs-lookup"><span data-stu-id="0ede4-104">Remarks</span></span>  
 <span data-ttu-id="0ede4-105">次のような形式の式があります。</span><span class="sxs-lookup"><span data-stu-id="0ede4-105">An expression of the form</span></span>  
  
```  
x <<= y  
```  
  
 <span data-ttu-id="0ede4-106">これが次のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="0ede4-106">is evaluated as</span></span>  
  
```  
x = x << y  
```  
  
 <span data-ttu-id="0ede4-107">ただし、`x` が評価されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="0ede4-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0ede4-108">[<< 演算子](../../../csharp/language-reference/operators/left-shift-operator.md) は、`y` で指定されたビット数だけ `x` を左にシフトします。</span><span class="sxs-lookup"><span data-stu-id="0ede4-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="0ede4-109">`<<=` 演算子は直接オーバーロードできませんが、ユーザー定義型は [<< 演算子](../../../csharp/language-reference/operators/left-shift-operator.md) をオーバーロードできます (「[operator](../../../csharp/language-reference/keywords/operator.md)」参照)。</span><span class="sxs-lookup"><span data-stu-id="0ede4-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ede4-110">例</span><span class="sxs-lookup"><span data-stu-id="0ede4-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0ede4-111">参照</span><span class="sxs-lookup"><span data-stu-id="0ede4-111">See Also</span></span>  
 [<span data-ttu-id="0ede4-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="0ede4-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0ede4-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0ede4-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0ede4-114">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="0ede4-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
