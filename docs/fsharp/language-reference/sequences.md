---
title: シーケンス (F#)
description: 大規模な順序付けられたデータのコレクションがあるが、必ずしもすべての要素を使用する必要がないときに、f# シーケンスを使用する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a3521037112d40998ed00cd6fed376882c2f2c88
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="sequences"></a><span data-ttu-id="46e61-103">シーケンス</span><span class="sxs-lookup"><span data-stu-id="46e61-103">Sequences</span></span>

> [!NOTE]
<span data-ttu-id="46e61-104">この記事の API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="46e61-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="46e61-105">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="46e61-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="46e61-106">A*シーケンス*論理一連の要素は、すべての 1 つの型。</span><span class="sxs-lookup"><span data-stu-id="46e61-106">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="46e61-107">シーケンスは、大規模な順序付けられたデータのコレクションがあるが、すべての要素を使用する予定がない場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="46e61-107">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="46e61-108">シーケンスは、すべての要素を使用ない状況でリストよりも優れたパフォーマンスを提供できるように、個々 のシーケンスを要素としてのみ計算が必要です。</span><span class="sxs-lookup"><span data-stu-id="46e61-108">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="46e61-109">シーケンスがによって表される、`seq<'T>`エイリアスの種類の`System.Collections.Generic.IEnumerable`します。</span><span class="sxs-lookup"><span data-stu-id="46e61-109">Sequences are represented by the `seq<'T>` type, which is an alias for `System.Collections.Generic.IEnumerable`.</span></span> <span data-ttu-id="46e61-110">そのため、すべて .NET Framework の型を実装する`System.IEnumerable`シーケンスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="46e61-110">Therefore, any .NET Framework type that implements `System.IEnumerable` can be used as a sequence.</span></span> <span data-ttu-id="46e61-111">[Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)シーケンスに関する操作のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="46e61-111">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="46e61-112">シーケンス式</span><span class="sxs-lookup"><span data-stu-id="46e61-112">Sequence Expressions</span></span>
<span data-ttu-id="46e61-113">A*シーケンス式*シーケンスに評価される式を指定します。</span><span class="sxs-lookup"><span data-stu-id="46e61-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="46e61-114">シーケンス式では、いくつかの形式を実行できます。</span><span class="sxs-lookup"><span data-stu-id="46e61-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="46e61-115">最も単純な形式では、範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="46e61-115">The simplest form specifies a range.</span></span> <span data-ttu-id="46e61-116">たとえば、 `seq { 1 .. 5 }` 1 と 5 のエンドポイントを含む、5 つの要素を格納するシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="46e61-117">ことができますも増分を指定 (または減少) 2 つの二重のピリオドの間です。</span><span class="sxs-lookup"><span data-stu-id="46e61-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="46e61-118">たとえば、次のコードは、10 の倍数のシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="46e61-119">シーケンス式は、f# の式、シーケンスの値を生成するのに構成されています。</span><span class="sxs-lookup"><span data-stu-id="46e61-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="46e61-120">使用できる、`yield`シーケンスの一部となる値を生成するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="46e61-120">They can use the `yield` keyword to produce values that become part of the sequence.</span></span>

<span data-ttu-id="46e61-121">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="46e61-121">Following is an example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="46e61-122">使用することができます、`->`演算子の代わりに`yield`、省略した場合、`do`キーワード、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="46e61-122">You can use the `->` operator instead of `yield`, in which case you can omit the `do` keyword, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="46e61-123">次のコードは、グリッドを表す配列インデックスと共に座標ペアの一覧を生成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-123">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="46e61-124">`if`シーケンスで使用される式はフィルターです。</span><span class="sxs-lookup"><span data-stu-id="46e61-124">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="46e61-125">たとえば、関数がある場合、唯一の素数のシーケンスを生成する`isprime`型の`int -> bool`、次のように、シーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-125">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="46e61-126">使用すると`yield`または`->`イテレーションでは、各イテレーションが想定されて、シーケンスの単一の要素を生成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-126">When you use `yield` or `->` in an iteration, each iteration is expected to generate a single element of the sequence.</span></span> <span data-ttu-id="46e61-127">各イテレーションでは、要素のシーケンスを生成する場合を使用して`yield!`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-127">If each iteration produces a sequence of elements, use `yield!`.</span></span> <span data-ttu-id="46e61-128">その場合は、各反復処理で生成された要素は、最後のシーケンスを生成するために連結されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-128">In that case, the elements generated on each iteration are concatenated to produce the final sequence.</span></span>

<span data-ttu-id="46e61-129">シーケンス式で同時に複数の式を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="46e61-129">You can combine multiple expressions together in a sequence expression.</span></span> <span data-ttu-id="46e61-130">それぞれの式によって生成された要素の連結は次の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="46e61-130">The elements generated by each expression are concatenated together.</span></span> <span data-ttu-id="46e61-131">例については、このトピックの「例」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46e61-131">For an example, see the "Examples" section of this topic.</span></span>

## <a name="examples"></a><span data-ttu-id="46e61-132">使用例</span><span class="sxs-lookup"><span data-stu-id="46e61-132">Examples</span></span>
<span data-ttu-id="46e61-133">最初の例では、イテレーション、フィルター、および配列を生成する yield を含むシーケンス式を使用します。</span><span class="sxs-lookup"><span data-stu-id="46e61-133">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="46e61-134">このコードは、1 から 100 のコンソールに含まれる素数のシーケンスを出力します。</span><span class="sxs-lookup"><span data-stu-id="46e61-134">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="46e61-135">次のコードでは`yield`それぞれの 2 つの要因と製品で構成される 3 つの要素の組で構成される乗算テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-135">The following code uses `yield` to create a multiplication table that consists of tuples of three elements, each consisting of two factors and the product.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="46e61-136">次の例で使用する`yield!`を個々 のシーケンスを 1 つの最終シーケンスに結合します。</span><span class="sxs-lookup"><span data-stu-id="46e61-136">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="46e61-137">この場合、バイナリ ツリーの各サブツリーのシーケンスは、最後のシーケンスを生成するために、再帰関数で連結されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-137">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a><span data-ttu-id="46e61-138">シーケンスの使用</span><span class="sxs-lookup"><span data-stu-id="46e61-138">Using Sequences</span></span>
<span data-ttu-id="46e61-139">シーケンスと同じ機能の多くをサポートして[一覧](lists.md)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-139">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="46e61-140">シーケンスは、グループ化やキー生成関数を使用してカウントなどの操作もサポートします。</span><span class="sxs-lookup"><span data-stu-id="46e61-140">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="46e61-141">シーケンスは、サブシーケンスを抽出するため、さまざまな関数もサポートします。</span><span class="sxs-lookup"><span data-stu-id="46e61-141">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="46e61-142">リスト、配列、セット、およびマップなど、多くのデータ型は暗黙的にシーケンスためにが列挙可能なコレクションです。</span><span class="sxs-lookup"><span data-stu-id="46e61-142">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="46e61-143">合わせて引数のどの共通の f# データ型では、さらに任意の .NET Framework データ型を実装するには、シーケンスを受け取る関数`System.Collections.Generic.IEnumerable<'T>`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-143">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET Framework data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="46e61-144">リストを受け取り、リストを受け取ることができますのみで、引数として関数を比較してください。</span><span class="sxs-lookup"><span data-stu-id="46e61-144">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="46e61-145">型`seq<'T>`の型の省略形は、`IEnumerable<'T>`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-145">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="46e61-146">つまり、任意の型を実装するジェネリック`System.Collections.Generic.IEnumerable<'T>`、設定を含む配列、リスト、およびと互換性のある f#、およびも .NET Framework コレクション型の大半を内の対応付け、`seq`を入力し、シーケンスが必要な場所で使用することができます。</span><span class="sxs-lookup"><span data-stu-id="46e61-146">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET Framework collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>


## <a name="module-functions"></a><span data-ttu-id="46e61-147">モジュール関数</span><span class="sxs-lookup"><span data-stu-id="46e61-147">Module Functions</span></span>
<span data-ttu-id="46e61-148">[Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)で、 [Microsoft.FSharp.Collections 名前空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)シーケンスを操作するための関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="46e61-148">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="46e61-149">これらの関数は、すべてこれらの型の列挙可能では、シーケンスとして処理することができますのでに、リスト、配列、マップ、およびセット同様を使用します。</span><span class="sxs-lookup"><span data-stu-id="46e61-149">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>


## <a name="creating-sequences"></a><span data-ttu-id="46e61-150">シーケンスの作成</span><span class="sxs-lookup"><span data-stu-id="46e61-150">Creating Sequences</span></span>
<span data-ttu-id="46e61-151">シーケンスは、前述のように、シーケンス式を使用して、または特定の機能を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="46e61-151">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="46e61-152">使用して、空のシーケンスを作成することができます[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)を使用して 1 つだけ指定した要素のシーケンスを作成することも[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-152">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="46e61-153">使用することができます[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)対象の要素が提供する関数を使用して作成されたシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-153">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="46e61-154">また、サイズを指定するには、シーケンスの。</span><span class="sxs-lookup"><span data-stu-id="46e61-154">You also provide a size for the sequence.</span></span> <span data-ttu-id="46e61-155">この関数は、同じように[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)ただし、要素は、シーケンスの反復処理が完了するまでは作成されません。</span><span class="sxs-lookup"><span data-stu-id="46e61-155">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="46e61-156">次のコードは、`Seq.init` の使用例です。</span><span class="sxs-lookup"><span data-stu-id="46e61-156">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="46e61-157">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="46e61-157">The output is</span></span>

```
0 10 20 30 40
```

<span data-ttu-id="46e61-158">使用して[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)と[Seq.ofList&#60;' T&#62;関数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)、配列とリストからシーケンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="46e61-158">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="46e61-159">ただし、変換することも配列とリスト シーケンスにキャスト演算子を使用しています。</span><span class="sxs-lookup"><span data-stu-id="46e61-159">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="46e61-160">両方の手法は、次のコードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-160">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="46e61-161">使用して[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)、シーケンスを作成するにはで定義されているなど、弱く型指定されたコレクションから`System.Collections`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-161">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="46e61-162">このような弱く型指定されたコレクションの要素型である`System.Object`と非ジェネリックを使用して列挙`System.Collections.Generic.IEnumerable&#96;1`型です。</span><span class="sxs-lookup"><span data-stu-id="46e61-162">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="46e61-163">次のコードの使用例`Seq.cast`に変換する、`System.Collections.ArrayList`シーケンスにします。</span><span class="sxs-lookup"><span data-stu-id="46e61-163">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="46e61-164">使用して無限シーケンスを定義することができます、 [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)関数。</span><span class="sxs-lookup"><span data-stu-id="46e61-164">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="46e61-165">このようなシーケンスでは、要素のインデックスからの各要素を生成する関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="46e61-165">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="46e61-166">レイジー評価; のために無限シーケンスも有効であります。要素は、必要に応じて、指定した関数を呼び出すことによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-166">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="46e61-167">次のコード例では、浮動小数点数のここでは、代替の一連の連続した整数の 2 乗の逆数無限シーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-167">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="46e61-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)状態を受け取り、シーケンスの後続の各要素を生成するためにそれを変換計算関数のシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="46e61-169">状態は、各要素が計算されたように変更できますおよび各要素の計算に使用されている値だけです。</span><span class="sxs-lookup"><span data-stu-id="46e61-169">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="46e61-170">2 番目の引数`Seq.unfold`シーケンスを開始するために使用される初期値です。</span><span class="sxs-lookup"><span data-stu-id="46e61-170">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="46e61-171">`Seq.unfold` 返すことによって、シーケンスを終了することにより、状態のオプションの種類を使用して、`None`値。</span><span class="sxs-lookup"><span data-stu-id="46e61-171">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="46e61-172">次のコードは、2 つのシーケンスの例を示しています。`seq1`と`fib`、により生成されて、`unfold`操作します。</span><span class="sxs-lookup"><span data-stu-id="46e61-172">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="46e61-173">最初、 `seq1`、100 までの番号を持つ単純なシーケンスだけです。</span><span class="sxs-lookup"><span data-stu-id="46e61-173">The first, `seq1`, is just a simple sequence with numbers up to 100.</span></span> <span data-ttu-id="46e61-174">2 番目、`fib`を使用して`unfold`フィボナッチ シーケンスを計算します。</span><span class="sxs-lookup"><span data-stu-id="46e61-174">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="46e61-175">フィボナッチ シーケンス内の各要素は、前の 2 つのフィボナッチ数の合計であるために、状態値は、前の 2 つの数値のシーケンスで構成される組です。</span><span class="sxs-lookup"><span data-stu-id="46e61-175">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="46e61-176">初期値は`(1,1)`シーケンス内の最初の 2 つの番号。</span><span class="sxs-lookup"><span data-stu-id="46e61-176">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="46e61-177">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46e61-177">The output is as follows:</span></span>

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="46e61-178">次のコードでは、ここで説明されている生成および無限シーケンスの値を計算シーケンス モジュール関数の多くを使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="46e61-178">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="46e61-179">コードを実行するまで数分をかかります。</span><span class="sxs-lookup"><span data-stu-id="46e61-179">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a><span data-ttu-id="46e61-180">検索と要素の検索</span><span class="sxs-lookup"><span data-stu-id="46e61-180">Searching and Finding Elements</span></span>
<span data-ttu-id="46e61-181">シーケンスがリストで使用できる機能をサポートします[Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)、 [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)、 [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)、 [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)、 。[Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)、 [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)、および[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-181">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="46e61-182">これらの関数のシーケンスで利用可能なバージョンでは、最大の検索対象の要素にのみ、シーケンスを評価します。</span><span class="sxs-lookup"><span data-stu-id="46e61-182">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="46e61-183">例については、次を参照してください。[一覧](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-183">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>


## <a name="obtaining-subsequences"></a><span data-ttu-id="46e61-184">サブシーケンスの取得</span><span class="sxs-lookup"><span data-stu-id="46e61-184">Obtaining Subsequences</span></span>
<span data-ttu-id="46e61-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)と[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)はフィルター処理とを選択するまで発生しませんシーケンスの要素を評価する点を除いて、リストの使用できる対応する関数と同様にします。</span><span class="sxs-lookup"><span data-stu-id="46e61-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="46e61-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)別のシーケンスからシーケンスを作成しますが、シーケンスの指定した要素数を制限します。</span><span class="sxs-lookup"><span data-stu-id="46e61-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="46e61-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)指定数のシーケンスの先頭からの要素のみを含む新しいシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="46e61-188">指定するためより少ないシーケンスの要素がある場合`Seq.take`スロー、`System.InvalidOperationException`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-188">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="46e61-189">違い`Seq.take`と`Seq.truncate`される`Seq.truncate`要素の数が指定した数よりも少ない場合はエラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="46e61-189">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="46e61-190">次のコードの動作を示しの間で違い`Seq.truncate`と`Seq.take`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-190">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="46e61-191">出力、エラーが発生する前に次に示します。</span><span class="sxs-lookup"><span data-stu-id="46e61-191">The output, before the error occurs, is as follows.</span></span>

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="46e61-192">使用して[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)、述語関数 (ブール関数) を指定し、述語は、元のシーケンスの要素から成る別のシーケンスからシーケンスを作成する`true`が停止します述語を返す最初の要素の前に`false`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-192">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="46e61-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)別のシーケンスの最初の要素の指定した数をスキップして残りの要素を返すシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="46e61-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="46e61-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)述部を返す限り、別のシーケンスの最初の要素をスキップするシーケンスを返します`true`、述語がを返す対象の最初の要素で始まる残りの要素を返します`false`.</span><span class="sxs-lookup"><span data-stu-id="46e61-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="46e61-195">次のコード例の動作を示していますの間で違い`Seq.takeWhile`、 `Seq.skip`、および`Seq.skipWhile`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-195">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="46e61-196">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46e61-196">The output is as follows.</span></span>

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="46e61-197">変換するシーケンス</span><span class="sxs-lookup"><span data-stu-id="46e61-197">Transforming Sequences</span></span>
<span data-ttu-id="46e61-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)入力シーケンスの連続する要素が組にグループ化の新しいシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="46e61-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)に似ています`Seq.pairwise`組のシーケンスを生成するには、代わりに、一連の隣接する要素のコピーを含む配列を生成する点を除いて、(、*ウィンドウ*) のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="46e61-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="46e61-200">各配列には、隣接する要素の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="46e61-200">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="46e61-201">次のコード例は、`Seq.windowed` の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="46e61-201">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="46e61-202">ここでは、ウィンドウ内の要素の数は 3 です。</span><span class="sxs-lookup"><span data-stu-id="46e61-202">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="46e61-203">この例では`printSeq`、上記のコード例で定義されています。</span><span class="sxs-lookup"><span data-stu-id="46e61-203">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="46e61-204">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46e61-204">The output is as follows.</span></span>

<span data-ttu-id="46e61-205">最初のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="46e61-205">Initial sequence:</span></span>

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="46e61-206">複数のシーケンスでの操作</span><span class="sxs-lookup"><span data-stu-id="46e61-206">Operations with Multiple Sequences</span></span>
<span data-ttu-id="46e61-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)と[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) 2 または 3 つのシーケンスを取得し、一連の組を生成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="46e61-208">これらの関数は、対応する使用可能な関数のように、[一覧](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-208">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="46e61-209">1 つのシーケンスを 2 つ以上のシーケンスを区切るための対応する機能はありません。</span><span class="sxs-lookup"><span data-stu-id="46e61-209">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="46e61-210">リストに、シーケンスを変換しを使用してシーケンスのこの機能が必要な場合[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-210">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>


## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="46e61-211">並べ替え、比較、およびグループ化</span><span class="sxs-lookup"><span data-stu-id="46e61-211">Sorting, Comparing, and Grouping</span></span>
<span data-ttu-id="46e61-212">リストのサポートされている並べ替え関数は、シーケンスとも動作します。</span><span class="sxs-lookup"><span data-stu-id="46e61-212">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="46e61-213">これが含まれます[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)と[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-213">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="46e61-214">これらの関数は、シーケンス全体を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="46e61-214">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="46e61-215">使用して 2 つのシーケンスを比較する、 [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)関数。</span><span class="sxs-lookup"><span data-stu-id="46e61-215">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="46e61-216">関数は、一連の要素をさらに、比較し、最初の等しくないペアを検出したときに停止します。</span><span class="sxs-lookup"><span data-stu-id="46e61-216">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="46e61-217">他の要素は、比較には影響しません。</span><span class="sxs-lookup"><span data-stu-id="46e61-217">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="46e61-218">`Seq.compareWith` の使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="46e61-218">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="46e61-219">コードでは、最初の要素のみが計算され、検査、され、結果は-1 を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="46e61-219">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="46e61-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)と呼ばれる値を生成する関数を受け取り、*キー*要素ごとにします。</span><span class="sxs-lookup"><span data-stu-id="46e61-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="46e61-221">キーは、各要素の各要素に対してこの関数を呼び出すことによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-221">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="46e61-222">`Seq.countBy` キーの値とキーの各値を生成した要素の数のカウントを格納しているシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="46e61-222">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="46e61-223">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46e61-223">The output is as follows.</span></span>

```
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="46e61-224">前の出力は、34 要素を 1、キーを生成した元のシーケンスの 33 生成値をキー 2、および 33 生成値をキーの 0 があったことを示しています。</span><span class="sxs-lookup"><span data-stu-id="46e61-224">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="46e61-225">呼び出して、シーケンスの要素をグループ化できます[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-225">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="46e61-226">`Seq.groupBy` シーケンスとの要素からキーを生成する関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="46e61-226">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="46e61-227">関数は、シーケンスの各要素に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-227">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="46e61-228">`Seq.groupBy` 組、それぞれの組の最初の要素がキーで、2 つ目は、そのキーを生成する要素のシーケンスのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="46e61-228">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="46e61-229">次のコード例は、の使用を示しています。`Seq.groupBy`を 0、1、および 2 は、個別のキー値を持つ 3 つのグループに 1 から 100 までの番号のシーケンスをパーティション分割します。</span><span class="sxs-lookup"><span data-stu-id="46e61-229">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="46e61-230">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46e61-230">The output is as follows.</span></span>

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="46e61-231">呼び出すことによって、重複する要素を除去するシーケンスを作成する[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-231">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="46e61-232">使用することもできます[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)、各要素に対して呼び出されるキー生成関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="46e61-232">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="46e61-233">結果のシーケンスには、固有のキーのある、元のシーケンスの要素が含まれています。以前の要素に重複するキーを生成後の要素は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-233">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="46e61-234">`Seq.distinct` の使用方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="46e61-234">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="46e61-235">`Seq.distinct` バイナリの番号を表すシーケンスを生成して、表示のみの個別の要素には 0 および 1 で示されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-235">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="46e61-236">次のコード例`Seq.distinctBy`から負または正の数値を含むシーケンスを開始して、キー生成関数として absolute value 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="46e61-236">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="46e61-237">結果のシーケンスには負の数が、シーケンスで先に表示され、そのためを同じの絶対パスを持つ正の数値の代わりに、選択するために、シーケンス内の負の数値に対応するすべての正の数値がありません。値、またはキー。</span><span class="sxs-lookup"><span data-stu-id="46e61-237">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="46e61-238">読み取り専用とキャッシュされたシーケンス</span><span class="sxs-lookup"><span data-stu-id="46e61-238">Readonly and Cached Sequences</span></span>
<span data-ttu-id="46e61-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)シーケンスの読み取り専用コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="46e61-240">`Seq.readonly` 配列などの読み取り/書き込みコレクションがあり、元のコレクションを変更したくない場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="46e61-240">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="46e61-241">この関数は、データのカプセル化を保持するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="46e61-241">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="46e61-242">次のコード例では、配列を含む型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="46e61-242">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="46e61-243">プロパティは、配列を見せますが、配列を返す代わりを使用して、配列から作成されたシーケンスを返します`Seq.readonly`です。</span><span class="sxs-lookup"><span data-stu-id="46e61-243">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="46e61-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)シーケンスの保存されているバージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="46e61-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="46e61-245">使用して`Seq.cache`またはシーケンスの再評価時に回避する、シーケンスを使用して複数のスレッドがあるが、各要素の操作が 1 回だけしたことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46e61-245">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="46e61-246">複数のスレッドによって使用されているシーケンスがある場合を列挙し、元のシーケンスの値を計算する 1 つのスレッドを持つことができ、残りのスレッドは、キャッシュされたシーケンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="46e61-246">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>


## <a name="performing-computations-on-sequences"></a><span data-ttu-id="46e61-247">シーケンスに対する計算の実行</span><span class="sxs-lookup"><span data-stu-id="46e61-247">Performing Computations on Sequences</span></span>
<span data-ttu-id="46e61-248">単純な算術演算などは、リストのような[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)、 [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)、 [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)、 [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)のようにします。</span><span class="sxs-lookup"><span data-stu-id="46e61-248">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="46e61-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)、 [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)、および[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)はリストの使用可能な対応する関数と同様にします。</span><span class="sxs-lookup"><span data-stu-id="46e61-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="46e61-250">シーケンスは、リストをサポートするこれらの関数のすべてのバリエーションのサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="46e61-250">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="46e61-251">詳細と例については、次を参照してください。[一覧](lists.md)です。</span><span class="sxs-lookup"><span data-stu-id="46e61-251">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46e61-252">関連項目</span><span class="sxs-lookup"><span data-stu-id="46e61-252">See Also</span></span>
[<span data-ttu-id="46e61-253">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="46e61-253">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="46e61-254">F# の型</span><span class="sxs-lookup"><span data-stu-id="46e61-254">F# Types</span></span>](fsharp-types.md)
