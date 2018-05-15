---
title: インライン関数 (F#)
description: 呼び出し元のコードに直接組み込まれている f# インライン関数を使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: d265f9b4e828946c510bd8e84b14d5236ab511fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="inline-functions"></a><span data-ttu-id="7a4eb-103">インライン関数</span><span class="sxs-lookup"><span data-stu-id="7a4eb-103">Inline Functions</span></span>

<span data-ttu-id="7a4eb-104">*インライン関数*関数が呼び出し元のコードに直接統合されています。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="7a4eb-105">インライン関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-105">Using Inline Functions</span></span>
<span data-ttu-id="7a4eb-106">静的な型パラメーターを使用して、型パラメーターでパラメーター化されるすべての関数はインラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="7a4eb-107">これは、コンパイラがこれらの型パラメーターを解決できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="7a4eb-108">通常のジェネリック型パラメーターを使用するときに、このような制限はありません。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="7a4eb-109">以外のメンバーの制約の使用を有効にすると、インライン関数でコードを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="7a4eb-110">ただし、過剰に使用するインライン関数には、コードがコンパイラの最適化やライブラリ関数の実装の変更を受けに可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="7a4eb-111">このため、他のすべての最適化の手法を試した場合を除き、最適化のインライン関数の使用を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="7a4eb-112">関数またはメソッドのインラインを行うことがありますパフォーマンスが向上するは常に大文字と小文字になっていません。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="7a4eb-113">したがって、こと、指定された関数のインラインを行うには実際にが良い影響を確認するのにパフォーマンスの測定を使用することも必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="7a4eb-114">`inline`修飾子は、最上位レベルに、モジュール レベルで、またはクラスで、メソッド レベルでの関数に適用できます。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="7a4eb-115">次のコード例は、最上位レベル、インライン インスタンス メソッド、およびインラインの静的メソッドで、インライン関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="7a4eb-116">インライン関数と型の推論</span><span class="sxs-lookup"><span data-stu-id="7a4eb-116">Inline Functions and Type Inference</span></span>
<span data-ttu-id="7a4eb-117">存在する`inline`型の推論に影響します。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="7a4eb-118">これは、非インライン関数ことはできませんが、インライン関数できますが静的に解決されるため、型パラメーター。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="7a4eb-119">次のコード例は、ケースを示しています。 ここで`inline`ため、静的に解決される型パラメーターを持つ関数を使用すると便利です、`float`変換演算子です。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="7a4eb-120">なし、`inline`修飾子、型の推論はここでは、特定の種類を実行する関数`int`です。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="7a4eb-121">ただし、`inline`修飾子は、関数が静的に解決される型パラメーターを持つと推論もします。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="7a4eb-122">`inline`次と修飾子は、型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="7a4eb-123">したがって、関数への変換をサポートする任意の型を受け取る**float**です。</span><span class="sxs-lookup"><span data-stu-id="7a4eb-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="7a4eb-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a4eb-124">See Also</span></span>
[<span data-ttu-id="7a4eb-125">関数</span><span class="sxs-lookup"><span data-stu-id="7a4eb-125">Functions</span></span>](index.md)

[<span data-ttu-id="7a4eb-126">制約</span><span class="sxs-lookup"><span data-stu-id="7a4eb-126">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="7a4eb-127">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a4eb-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
