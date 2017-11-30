---
title: "インライン関数 (F#)"
description: "呼び出し元のコードに直接組み込まれている f# インライン関数を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a><span data-ttu-id="8a211-104">インライン関数</span><span class="sxs-lookup"><span data-stu-id="8a211-104">Inline Functions</span></span>

<span data-ttu-id="8a211-105">*インライン関数*関数が呼び出し元のコードに直接統合されています。</span><span class="sxs-lookup"><span data-stu-id="8a211-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="8a211-106">インライン関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="8a211-106">Using Inline Functions</span></span>
<span data-ttu-id="8a211-107">静的な型パラメーターを使用して、型パラメーターでパラメーター化されるすべての関数はインラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a211-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="8a211-108">これは、コンパイラがこれらの型パラメーターを解決できることを保証します。</span><span class="sxs-lookup"><span data-stu-id="8a211-108">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="8a211-109">通常のジェネリック型パラメーターを使用するときに、このような制限はありません。</span><span class="sxs-lookup"><span data-stu-id="8a211-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="8a211-110">以外のメンバーの制約の使用を有効にすると、インライン関数でコードを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="8a211-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="8a211-111">ただし、過剰に使用するインライン関数には、コードがコンパイラの最適化やライブラリ関数の実装の変更を受けに可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8a211-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="8a211-112">このため、他のすべての最適化の手法を試した場合を除き、最適化のインライン関数の使用を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a211-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="8a211-113">関数またはメソッドのインラインを行うことがありますパフォーマンスが向上するは常に大文字と小文字になっていません。</span><span class="sxs-lookup"><span data-stu-id="8a211-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="8a211-114">したがって、こと、指定された関数のインラインを行うには実際にが良い影響を確認するのにパフォーマンスの測定を使用することも必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a211-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="8a211-115">`inline`修飾子は、最上位レベルに、モジュール レベルで、またはクラスで、メソッド レベルでの関数に適用できます。</span><span class="sxs-lookup"><span data-stu-id="8a211-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="8a211-116">次のコード例は、最上位レベル、インライン インスタンス メソッド、およびインラインの静的メソッドで、インライン関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="8a211-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="8a211-117">インライン関数と型の推論</span><span class="sxs-lookup"><span data-stu-id="8a211-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="8a211-118">存在する`inline`型の推論に影響します。</span><span class="sxs-lookup"><span data-stu-id="8a211-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="8a211-119">これは、非インライン関数ことはできませんが、インライン関数できますが静的に解決されるため、型パラメーター。</span><span class="sxs-lookup"><span data-stu-id="8a211-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="8a211-120">次のコード例は、ケースを示しています。 ここで`inline`ため、静的に解決される型パラメーターを持つ関数を使用すると便利です、`float`変換演算子です。</span><span class="sxs-lookup"><span data-stu-id="8a211-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="8a211-121">なし、`inline`修飾子、型の推論はここでは、特定の種類を実行する関数`int`です。</span><span class="sxs-lookup"><span data-stu-id="8a211-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="8a211-122">ただし、`inline`修飾子は、関数が静的に解決される型パラメーターを持つと推論もします。</span><span class="sxs-lookup"><span data-stu-id="8a211-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="8a211-123">`inline`次と修飾子は、型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="8a211-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="8a211-124">したがって、関数への変換をサポートする任意の型を受け取る**float**です。</span><span class="sxs-lookup"><span data-stu-id="8a211-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="8a211-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a211-125">See Also</span></span>
[<span data-ttu-id="8a211-126">関数</span><span class="sxs-lookup"><span data-stu-id="8a211-126">Functions</span></span>](index.md)

[<span data-ttu-id="8a211-127">制約</span><span class="sxs-lookup"><span data-stu-id="8a211-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="8a211-128">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a211-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
