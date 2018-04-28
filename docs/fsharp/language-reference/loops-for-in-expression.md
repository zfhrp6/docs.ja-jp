---
title: 'ループ: for...in 式 (F#)'
description: 参照してくださいか f# データ型.. 式でコンス トラクターをループが使用される列挙可能なコレクション内のパターンの一致を繰り返し処理します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: eaf0f4fc6419d8e0bff46795120ee5e42c4efe1d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forin-expression"></a><span data-ttu-id="1f109-103">ループ: for...in 式</span><span class="sxs-lookup"><span data-stu-id="1f109-103">Loops: for...in Expression</span></span>

<span data-ttu-id="1f109-104">このループ構造は、範囲式、シーケンス、リスト、配列、または列挙型をサポートするその他の構造体などの列挙可能なコレクション内のパターンの一致を反復処理に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f109-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="1f109-105">構文</span><span class="sxs-lookup"><span data-stu-id="1f109-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="1f109-106">コメント</span><span class="sxs-lookup"><span data-stu-id="1f109-106">Remarks</span></span>
<span data-ttu-id="1f109-107">`for...in`式と比較すること、`for each`の他の .NET 言語のステートメントをループ列挙可能なコレクション内の値に使用されているためです。</span><span class="sxs-lookup"><span data-stu-id="1f109-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="1f109-108">ただし、`for...in`も全体のコレクションを反復処理だけではなくコレクションに対する一致するパターンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1f109-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="1f109-109">列挙可能なコレクションとして、またはを使用して、列挙可能な式を指定することができます、`..`演算子、整数型の範囲とします。</span><span class="sxs-lookup"><span data-stu-id="1f109-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="1f109-110">列挙可能なコレクションには、リスト、シーケンス、配列、セット、マップ、およびなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1f109-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="1f109-111">実装する任意の型`System.Collections.IEnumerable`使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f109-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="1f109-112">使用して範囲を表現するときに、`..`演算子を次の構文を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1f109-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="1f109-113">*開始*.</span><span class="sxs-lookup"><span data-stu-id="1f109-113">*start* ..</span></span> <span data-ttu-id="1f109-114">*[完了] します。*</span><span class="sxs-lookup"><span data-stu-id="1f109-114">*finish*</span></span>

<span data-ttu-id="1f109-115">呼ばれるインクリメントを含むバージョンを使用することができます、*スキップ*次のコードのように、します。</span><span class="sxs-lookup"><span data-stu-id="1f109-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="1f109-116">*開始*.</span><span class="sxs-lookup"><span data-stu-id="1f109-116">*start* ..</span></span> <span data-ttu-id="1f109-117">*スキップ*.</span><span class="sxs-lookup"><span data-stu-id="1f109-117">*skip* ..</span></span> <span data-ttu-id="1f109-118">*[完了] します。*</span><span class="sxs-lookup"><span data-stu-id="1f109-118">*finish*</span></span>

<span data-ttu-id="1f109-119">パターンとして整数の範囲と単純なカウンター変数を使用すると通常の動作をイテレーションごとに 1 つのカウンター変数をインクリメントするが、カウンターが代わりにインクリメント skip 値で範囲には、skip 値が含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="1f109-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="1f109-120">パターンに一致した値は、式の本体でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f109-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="1f109-121">コード例を次の例を示します、`for...in`式。</span><span class="sxs-lookup"><span data-stu-id="1f109-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="1f109-122">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="1f109-123">次の例では、単純な変数ではなくタプル パターンを使用する方法とシーケンス、ループする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f109-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="1f109-124">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-124">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="1f109-125">次の例では、単純な整数の範囲内でループする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f109-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="1f109-126">Function1 の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="1f109-127">次の例では、ループ、範囲を範囲の他のすべての要素が含まれている 2 のスキップを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f109-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="1f109-128">出力`function2`のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="1f109-129">次の例では、文字の範囲を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f109-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="1f109-130">出力`function3`のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="1f109-131">次の例では、負の値のスキップ値逆順イテレーションを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f109-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="1f109-132">出力`function4`のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="1f109-133">先頭と範囲の終了には、次のコードのように、関数など、式ことができます。</span><span class="sxs-lookup"><span data-stu-id="1f109-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="1f109-134">出力`function5`この入力には、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="1f109-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="1f109-135">次の例は、ループ内に要素が不要な場合に、ワイルドカード文字 (_) の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="1f109-135">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="1f109-136">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f109-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="1f109-137">`Note` 使用することができます`for...in`シーケンス式およびその他の計算式で、カスタマイズされたバージョンの場合、`for...in`式を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f109-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="1f109-138">詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f109-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="1f109-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f109-139">See Also</span></span>
[<span data-ttu-id="1f109-140">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="1f109-140">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1f109-141">ループ: `for...to` 式</span><span class="sxs-lookup"><span data-stu-id="1f109-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="1f109-142">ループ: `while...do` 式</span><span class="sxs-lookup"><span data-stu-id="1f109-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
