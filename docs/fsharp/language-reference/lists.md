---
title: "リスト (F#)"
description: "F# でリストを同じ型の要素の順序付けられ、変更できない一連の概要を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a1a6075f-064d-4aee-8222-2b59ff16cc12
ms.openlocfilehash: 5802a5a1c48ad05c1765c4c0fa2e8a81a92dee8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="lists"></a><span data-ttu-id="54330-104">表示内容</span><span class="sxs-lookup"><span data-stu-id="54330-104">Lists</span></span>

> [!NOTE]
<span data-ttu-id="54330-105">この記事の API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="54330-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="54330-106">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="54330-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="54330-107">F# のリストは、順序が指定されており変更できない一連の同じ型の要素です。</span><span class="sxs-lookup"><span data-stu-id="54330-107">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="54330-108">リストに対して基本的な操作を実行するには、内の関数を使用して、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)です。</span><span class="sxs-lookup"><span data-stu-id="54330-108">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>


## <a name="creating-and-initializing-lists"></a><span data-ttu-id="54330-109">リストの作成と初期化</span><span class="sxs-lookup"><span data-stu-id="54330-109">Creating and Initializing Lists</span></span>
<span data-ttu-id="54330-110">リストを定義するには、次のコード行に示すように、セミコロンで区切って明示的にリストした要素を角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="54330-110">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="54330-111">要素間に改行を挿入することもできます。その場合はセミコロンの区切り記号を省略できます。</span><span class="sxs-lookup"><span data-stu-id="54330-111">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="54330-112">要素の初期化式が長い場合、各要素にコメントを含める場合は、改行の構文を使用するとコードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="54330-112">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="54330-113">通常、リストの要素はすべて同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="54330-113">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="54330-114">例外として、要素が基本型として指定されているリストには、派生型の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="54330-114">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="54330-115">したがって次に示す例は、`Button` と `CheckBox` の両方が `Control` から派生しているため、受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="54330-115">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="54330-116">また、次のコードで示すように、整数を範囲演算子 (`..`) で区切って示した範囲を使用して、リストの要素を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="54330-116">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="54330-117">空のリストは、間に何も含まない 1 組の角かっこで示します。</span><span class="sxs-lookup"><span data-stu-id="54330-117">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="54330-118">シーケンス式を使用してリストを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="54330-118">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="54330-119">参照してください[シーケンス式](sequences.md#sequence-expressions)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="54330-119">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="54330-120">たとえば、次のコードでは 1 から 10 までの整数の 2 乗のリストが作成されます。</span><span class="sxs-lookup"><span data-stu-id="54330-120">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="54330-121">リストの操作に使用する演算子</span><span class="sxs-lookup"><span data-stu-id="54330-121">Operators for Working with Lists</span></span>
<span data-ttu-id="54330-122">リストに要素を付加するには、`::` (cons) 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="54330-122">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="54330-123">`list1` が `[2; 3; 4]` の場合、次のコードでは `list2` が `[100; 2; 3; 4]` として作成されます。</span><span class="sxs-lookup"><span data-stu-id="54330-123">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="54330-124">互換性のある型を含むリストを連結するには、次のコードに示すように `@` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="54330-124">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="54330-125">`list1` が `[2; 3; 4]` であり、`list2` が `[100; 2; 3; 4 ]` の場合、このコードでは `list3` が `[2; 3; 4; 100; 2; 3; 4]` として作成されます。</span><span class="sxs-lookup"><span data-stu-id="54330-125">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="54330-126">リストに対する操作を実行するための関数では使用、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)です。</span><span class="sxs-lookup"><span data-stu-id="54330-126">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="54330-127">F# のリストは変更できないため、変更操作を行うと、既存のリストが変更されるのではなく、新しいリストが生成されます。</span><span class="sxs-lookup"><span data-stu-id="54330-127">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="54330-128">F# のリストはできるため、リストの先頭のみにアクセスする操作は o (1)、シングル リンク リストとして実装され、要素へのアクセスは O (*n*)。</span><span class="sxs-lookup"><span data-stu-id="54330-128">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>


## <a name="properties"></a><span data-ttu-id="54330-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="54330-129">Properties</span></span>
<span data-ttu-id="54330-130">リスト型では次のプロパティがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="54330-130">The list type supports the following properties:</span></span>

|<span data-ttu-id="54330-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="54330-131">Property</span></span>|<span data-ttu-id="54330-132">種類</span><span class="sxs-lookup"><span data-stu-id="54330-132">Type</span></span>|<span data-ttu-id="54330-133">説明</span><span class="sxs-lookup"><span data-stu-id="54330-133">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="54330-134">Head</span><span class="sxs-lookup"><span data-stu-id="54330-134">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="54330-135">1 番目の要素。</span><span class="sxs-lookup"><span data-stu-id="54330-135">The first element.</span></span>|
|[<span data-ttu-id="54330-136">空</span><span class="sxs-lookup"><span data-stu-id="54330-136">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="54330-137">該当する型の空のリストを返す静的プロパティ。</span><span class="sxs-lookup"><span data-stu-id="54330-137">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="54330-138">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="54330-138">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="54330-139">リストに要素がない場合は `true` です。</span><span class="sxs-lookup"><span data-stu-id="54330-139">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="54330-140">Item</span><span class="sxs-lookup"><span data-stu-id="54330-140">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="54330-141">指定したインデックスの要素 (起点を 0 とする)。</span><span class="sxs-lookup"><span data-stu-id="54330-141">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="54330-142">長さ</span><span class="sxs-lookup"><span data-stu-id="54330-142">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="54330-143">要素の数。</span><span class="sxs-lookup"><span data-stu-id="54330-143">The number of elements.</span></span>|
|[<span data-ttu-id="54330-144">末尾</span><span class="sxs-lookup"><span data-stu-id="54330-144">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="54330-145">1 番目の要素を除いたリスト。</span><span class="sxs-lookup"><span data-stu-id="54330-145">The list without the first element.</span></span>|
<span data-ttu-id="54330-146">これらのプロパティを使用したいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-146">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a><span data-ttu-id="54330-147">リストの使用</span><span class="sxs-lookup"><span data-stu-id="54330-147">Using Lists</span></span>
<span data-ttu-id="54330-148">リストを使用してプログラミングを行うと、少量のコードで複雑な操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="54330-148">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="54330-149">このセクションでは、関数型プログラミングにおいて重要なリストに対する一般的な操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="54330-149">This section describes common operations on lists that are important to functional programming.</span></span>


### <a name="recursion-with-lists"></a><span data-ttu-id="54330-150">リストを使用した再帰</span><span class="sxs-lookup"><span data-stu-id="54330-150">Recursion with Lists</span></span>
<span data-ttu-id="54330-151">リストは、再帰的なプログラミング技法に非常に適しています。</span><span class="sxs-lookup"><span data-stu-id="54330-151">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="54330-152">リストのすべての要素に対して実行する必要がある操作があるとします。</span><span class="sxs-lookup"><span data-stu-id="54330-152">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="54330-153">この操作を再帰的に実行するには、リストの先頭に対して処理を行った後にリストの後部 (元のリストの最初の要素を除いた要素で構成される、元のリストより小さいリスト) を次の再帰レベルに戻します。</span><span class="sxs-lookup"><span data-stu-id="54330-153">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="54330-154">このような再帰関数を記述するには、パターン マッチで cons 演算子 (`::`) を使用します。これによって、リストの先頭を末尾から分離できます。</span><span class="sxs-lookup"><span data-stu-id="54330-154">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="54330-155">パターン マッチを使用して、リストに対する操作を実行する再帰関数を実装する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-155">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="54330-156">このコードは小さいリストでは問題なく動作しますが、リストが大きくなると、スタックがオーバーフローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54330-156">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="54330-157">次に示すコードは、再帰関数の処理では標準的な技法であるアキュムレータ引数を使用して、このコードを改善したものです。</span><span class="sxs-lookup"><span data-stu-id="54330-157">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="54330-158">アキュムレータ引数を使用すると、関数の後部が再帰的になり、スタック領域を節約できます。</span><span class="sxs-lookup"><span data-stu-id="54330-158">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="54330-159">関数 `RemoveAllMultiples` は、2 つのリストを受け取る再帰関数です。</span><span class="sxs-lookup"><span data-stu-id="54330-159">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="54330-160">1 番目のリストは、倍数を削除する数値が格納されたリストで、2 番目のリストは、数値を削除する元のリストです。</span><span class="sxs-lookup"><span data-stu-id="54330-160">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="54330-161">次の例のコードでは、この再帰関数を使用してリストから素数以外をすべて削除します。その結果、素数のリストが残ります。</span><span class="sxs-lookup"><span data-stu-id="54330-161">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="54330-162">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-162">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="54330-163">モジュール関数</span><span class="sxs-lookup"><span data-stu-id="54330-163">Module Functions</span></span>
<span data-ttu-id="54330-164">[List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)リストの要素にアクセスする機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="54330-164">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="54330-165">先頭の要素には、最も迅速かつ簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="54330-165">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="54330-166">プロパティを使用して[ヘッド](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)またはモジュール関数[List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)です。</span><span class="sxs-lookup"><span data-stu-id="54330-166">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="54330-167">使用して、リストの末尾にアクセスすることができます、[末尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)プロパティまたは[List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601)関数。</span><span class="sxs-lookup"><span data-stu-id="54330-167">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="54330-168">インデックスを使用して要素を見つけ、使用、 [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1)関数。</span><span class="sxs-lookup"><span data-stu-id="54330-168">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="54330-169">`List.nth` はリストを走査します。</span><span class="sxs-lookup"><span data-stu-id="54330-169">`List.nth` traverses the list.</span></span> <span data-ttu-id="54330-170">そのため、これは O (*n*)。</span><span class="sxs-lookup"><span data-stu-id="54330-170">Therefore, it is O(*n*).</span></span> <span data-ttu-id="54330-171">コードで `List.nth` を頻繁に使用する場合は、リストの代わりに配列を使用すると、効果的である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54330-171">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="54330-172">配列での要素のアクセスは O(1) です。</span><span class="sxs-lookup"><span data-stu-id="54330-172">Element access in arrays is O(1).</span></span>


### <a name="boolean-operations-on-lists"></a><span data-ttu-id="54330-173">リストに対するブール演算</span><span class="sxs-lookup"><span data-stu-id="54330-173">Boolean Operations on Lists</span></span>
<span data-ttu-id="54330-174">[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107)関数は、リストのすべての要素があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="54330-174">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="54330-175">[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)関数に適用されるブール値をテスト リストを返しますの要素を`true`いずれかの要素にテストに合格する場合。</span><span class="sxs-lookup"><span data-stu-id="54330-175">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="54330-176">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e)と似ていますが、一連の 2 つのリスト内の要素のペアで動作します。</span><span class="sxs-lookup"><span data-stu-id="54330-176">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="54330-177">`List.exists` を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-177">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="54330-178">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-178">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="54330-179">次の例は、`List.exists2` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="54330-179">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="54330-180">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-180">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="54330-181">使用することができます[List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7)一覧のすべての要素が条件を満たすかどうかをテストするかどうか。</span><span class="sxs-lookup"><span data-stu-id="54330-181">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="54330-182">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-182">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="54330-183">同様に、 [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) 2 つのリストに対応する位置のすべての要素が要素の各ペアを含むブール式を満たすかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="54330-183">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="54330-184">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-184">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="54330-185">リストに対する並べ替え操作</span><span class="sxs-lookup"><span data-stu-id="54330-185">Sort Operations on Lists</span></span>
<span data-ttu-id="54330-186">[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d)、 [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)、および[List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7)関数がリストを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="54330-186">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="54330-187">並べ替え関数は、これら 3 つの関数のどれを使用するかを判断します。</span><span class="sxs-lookup"><span data-stu-id="54330-187">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="54330-188">`List.sort` は、既定の一般的な比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="54330-188">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="54330-189">一般的な比較は、汎用の比較関数に基づくグローバル演算子を使用して、値を比較します。</span><span class="sxs-lookup"><span data-stu-id="54330-189">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="54330-190">この比較は、単純な数値型、タプル、レコード、判別共用体、リスト、配列、および `System.IComparable` を実装する任意の型など、広範な要素型で効率的に動作します。</span><span class="sxs-lookup"><span data-stu-id="54330-190">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="54330-191">`System.IComparable` を実装する型の場合は、汎用的な比較で `System.IComparable.CompareTo()` 関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="54330-191">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="54330-192">また、汎用的な比較は文字列にも使用できますが、カルチャに依存しない並べ替え順序が使用されます。</span><span class="sxs-lookup"><span data-stu-id="54330-192">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="54330-193">関数型のようなサポートされない型には、汎用的な比較を使用できません。</span><span class="sxs-lookup"><span data-stu-id="54330-193">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="54330-194">また、既定の汎用的な比較は、小さい構造の型の場合に最高のパフォーマンスを示します。比較と並べ替えが頻繁に必要な大きい構造の型の場合は、`System.IComparable` を実装し、`System.IComparable.CompareTo()` メソッドを効率的に実装することを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="54330-194">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="54330-195">`List.sortBy` 関数は、並べ替え基準として使用される値を返す関数を受け取り、`List.sortWith` 関数は、比較関数を引数として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="54330-195">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="54330-196">これら 2 つの関数は、比較をサポートしない型を使用するとき、またはカルチャを認識する文字列の場合のように複雑な比較セマンティクスを必要とする比較の場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="54330-196">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="54330-197">次の例は、`List.sort` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="54330-197">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="54330-198">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-198">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="54330-199">次の例は、`List.sortBy` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="54330-199">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="54330-200">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-200">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="54330-201">次の例は、`List.sortWith` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="54330-201">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="54330-202">この例では、カスタムの比較関数 `compareWidgets` を使用して、まず、カスタム型の 1 つのフィールドを比較し、最初のフィールドの値が同じである場合は、さらに別のフィールドを比較しています。</span><span class="sxs-lookup"><span data-stu-id="54330-202">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="54330-203">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-203">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="54330-204">リストに対する検索操作</span><span class="sxs-lookup"><span data-stu-id="54330-204">Search Operations on Lists</span></span>
<span data-ttu-id="54330-205">リストに対するさまざまな検索操作がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="54330-205">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="54330-206">最も単純で、 [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06)、特定の条件に一致する最初の要素を検索することができます。</span><span class="sxs-lookup"><span data-stu-id="54330-206">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="54330-207">次のコード例では、`List.find` を使用して、5 で割り切れる最初の数をリストから検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54330-207">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="54330-208">The result is 5.</span><span class="sxs-lookup"><span data-stu-id="54330-208">The result is 5.</span></span>

<span data-ttu-id="54330-209">最初の要素に変換する必要があります場合、呼び出す[List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2)オプションを返す関数を受け取りを最初のオプションの値を検索、`Some(x)`です。</span><span class="sxs-lookup"><span data-stu-id="54330-209">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="54330-210">`List.pick` は要素を返す代わりに、結果 `x` を返します。</span><span class="sxs-lookup"><span data-stu-id="54330-210">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="54330-211">一致する要素が見つからない場合、`List.pick` は `System.Collections.Generic.KeyNotFoundException` をスローします。</span><span class="sxs-lookup"><span data-stu-id="54330-211">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="54330-212">`List.pick` の使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="54330-212">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="54330-213">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-213">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="54330-214">別の検索操作グループ[List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d)し、関連する関数は、オプション値を返します。</span><span class="sxs-lookup"><span data-stu-id="54330-214">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="54330-215">`List.tryFind` 関数は、条件を満たす要素がリストにある場合は、その最初の要素を返します。条件を満たす要素がない場合は、オプション値 `None` を返します。</span><span class="sxs-lookup"><span data-stu-id="54330-215">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="54330-216">バリエーション[List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec)が見つかった場合、要素自体ではなく、要素のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="54330-216">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="54330-217">これらの関数を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="54330-217">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="54330-218">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-218">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="54330-219">リストに対する算術演算</span><span class="sxs-lookup"><span data-stu-id="54330-219">Arithmetic Operations on Lists</span></span>
<span data-ttu-id="54330-220">Sum や average などの一般的な算術演算が組み込まれて、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)です。</span><span class="sxs-lookup"><span data-stu-id="54330-220">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="54330-221">使用する[List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)、リスト要素の型をサポートする必要があります、`+`演算子ゼロの値があるとします。</span><span class="sxs-lookup"><span data-stu-id="54330-221">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="54330-222">すべての組み込み数値型はこの条件を満たしています。</span><span class="sxs-lookup"><span data-stu-id="54330-222">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="54330-223">使用する[List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)要素の型は、整数型は含まれませんが、浮動小数点型では、剰余のない除算をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="54330-223">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="54330-224">[List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d)と[List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403)関数は、パラメーターとして関数を受け取るし、この関数の結果は、合計や平均の値の計算に使用されます。</span><span class="sxs-lookup"><span data-stu-id="54330-224">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="54330-225">次のコードは、`List.sum`、 `List.sumBy`、および `List.average` の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="54330-225">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="54330-226">出力は `1.000000` になります。</span><span class="sxs-lookup"><span data-stu-id="54330-226">The output is `1.000000`.</span></span>

<span data-ttu-id="54330-227">`List.averageBy` の使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="54330-227">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="54330-228">出力は `5.5` になります。</span><span class="sxs-lookup"><span data-stu-id="54330-228">The output is `5.5`.</span></span>


### <a name="lists-and-tuples"></a><span data-ttu-id="54330-229">リストとタプル</span><span class="sxs-lookup"><span data-stu-id="54330-229">Lists and Tuples</span></span>
<span data-ttu-id="54330-230">タプルを含むリストは、zip 関数および unzip 関数で操作できます。</span><span class="sxs-lookup"><span data-stu-id="54330-230">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="54330-231">これらの関数は、単一値の 2 つのリストを結合してタプルのリストを 1 つ生成したり、タプルの 1 つのリストを分割して単一の値のリストを 2 つ生成したりします。</span><span class="sxs-lookup"><span data-stu-id="54330-231">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="54330-232">最も単純な[List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c)関数が 1 つの要素の 2 つのリストを受け取り、タプルのペアの 1 つのリストを生成します。</span><span class="sxs-lookup"><span data-stu-id="54330-232">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="54330-233">別のバージョン、 [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b)単一の要素の次の 3 つのリストを受け取り、および 3 つの要素を持つタプルの 1 つのリストを生成します。</span><span class="sxs-lookup"><span data-stu-id="54330-233">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="54330-234">次のコード例は、`List.zip` の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54330-234">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="54330-235">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-235">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="54330-236">次のコード例は、`List.zip3` の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54330-236">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="54330-237">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-237">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="54330-238">バージョンでは、対応する unzip [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)と[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)組のリストを行い、最初のリストが格納された最初の組ごとにすべての要素、タプルのリストを返すと、2 番目の一覧には、各タプルの 2 番目の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="54330-238">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="54330-239">使用を次のコード例に示します[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)です。</span><span class="sxs-lookup"><span data-stu-id="54330-239">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="54330-240">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-240">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="54330-241">使用を次のコード例に示します[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)です。</span><span class="sxs-lookup"><span data-stu-id="54330-241">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="54330-242">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-242">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="54330-243">リスト要素に対する操作</span><span class="sxs-lookup"><span data-stu-id="54330-243">Operating on List Elements</span></span>
<span data-ttu-id="54330-244">F# は、リストの要素に対するさまざまな操作をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="54330-244">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="54330-245">最も単純な[List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f)、これにより、一覧の各要素に対して関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="54330-245">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="54330-246">バリエーションを含める[List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40)、2 つのリストの要素に対して演算を実行できます[List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60)と同様にある`List.iter`として各要素のインデックスが渡される点を除いて、各要素に対して呼び出される関数の引数と[List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c)の機能の組み合わせは`List.iter2`と`List.iteri`です。</span><span class="sxs-lookup"><span data-stu-id="54330-246">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="54330-247">次のコード例にこれらの関数を示します。</span><span class="sxs-lookup"><span data-stu-id="54330-247">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="54330-248">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-248">The output is as follows:</span></span>

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="54330-249">リストの要素を変換する他の頻繁に使用される関数は[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)を使用すると、一覧の各要素に関数を適用し、新しいリストに、すべての結果を格納します。</span><span class="sxs-lookup"><span data-stu-id="54330-249">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="54330-250">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57)と[List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8)は複数のリストを受け取るバリエーションです。</span><span class="sxs-lookup"><span data-stu-id="54330-250">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="54330-251">使用することも[List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14)と[List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49)要素に加えて、関数は各要素のインデックスに渡される必要がある場合は、です。</span><span class="sxs-lookup"><span data-stu-id="54330-251">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="54330-252">`List.mapi2` と `List.mapi` の唯一の違いは、`List.mapi2` では 2 つのリストが使用される点です。</span><span class="sxs-lookup"><span data-stu-id="54330-252">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="54330-253">次の例を示しています[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)です。</span><span class="sxs-lookup"><span data-stu-id="54330-253">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="54330-254">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-254">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="54330-255">`List.map2` を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-255">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="54330-256">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-256">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="54330-257">`List.map3` を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-257">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="54330-258">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-258">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="54330-259">`List.mapi` を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-259">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="54330-260">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-260">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="54330-261">`List.mapi2` を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-261">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="54330-262">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-262">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="54330-263">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f)に似ています`List.map`の各要素は、一覧を作成し、これらすべてのリストが最終的な一覧に連結された点を除いて、します。</span><span class="sxs-lookup"><span data-stu-id="54330-263">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="54330-264">次のコードでは、リストの各要素が 3 つの値を生成します。</span><span class="sxs-lookup"><span data-stu-id="54330-264">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="54330-265">これらすべてが 1 つのリストに集約されます。</span><span class="sxs-lookup"><span data-stu-id="54330-265">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="54330-266">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-266">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="54330-267">使用することも[List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248)、ブール条件を受け取り、条件を特定の条件を満たす要素のみで構成される新しいリストを生成します。</span><span class="sxs-lookup"><span data-stu-id="54330-267">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="54330-268">結果のリストは `[2; 4; 6]` です。</span><span class="sxs-lookup"><span data-stu-id="54330-268">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="54330-269">Map と filter を組み合わせた[List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d)変換し、同時に要素を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="54330-269">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="54330-270">`List.choose` は、オプションを返す関数をリストの各要素に適用し、関数がオプション値 `Some` を返す要素の結果から成る新しいリストを返します。</span><span class="sxs-lookup"><span data-stu-id="54330-270">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="54330-271">次のコードでは、`List.choose` を使用して、最初の文字が大文字の単語を単語のリストから選択しています。</span><span class="sxs-lookup"><span data-stu-id="54330-271">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="54330-272">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54330-272">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="54330-273">複数のリストに対する操作</span><span class="sxs-lookup"><span data-stu-id="54330-273">Operating on Multiple Lists</span></span>
<span data-ttu-id="54330-274">複数のリストを結合できます。</span><span class="sxs-lookup"><span data-stu-id="54330-274">Lists can be joined together.</span></span> <span data-ttu-id="54330-275">参加するには 2 つのリストを 1 つを使用して[List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)です。</span><span class="sxs-lookup"><span data-stu-id="54330-275">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="54330-276">参加するには複数の 2 つのリストを使用して[List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)です。</span><span class="sxs-lookup"><span data-stu-id="54330-276">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a><span data-ttu-id="54330-277">フォールド操作とスキャン操作</span><span class="sxs-lookup"><span data-stu-id="54330-277">Fold and Scan Operations</span></span>
<span data-ttu-id="54330-278">リストの操作の中には、リストのすべての要素間の依存関係を伴うものがあります。</span><span class="sxs-lookup"><span data-stu-id="54330-278">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="54330-279">フォールド操作とスキャン操作はのように、`List.iter`と`List.map`各要素に対して関数を呼び出す場合、これらの操作と呼ばれる追加のパラメーターを提供する、*アキュムレータ*情報を保持します。計算。</span><span class="sxs-lookup"><span data-stu-id="54330-279">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="54330-280">リストに対して計算を実行するには、`List.fold` を使用します。</span><span class="sxs-lookup"><span data-stu-id="54330-280">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="54330-281">使用を次のコード例に示します[List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0)さまざまな操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="54330-281">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="54330-282">リストが走査されます。アキュムレータ `acc`は、計算の進行に伴って渡される値です。</span><span class="sxs-lookup"><span data-stu-id="54330-282">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="54330-283">1 番目の引数はアキュムレータとリスト要素を受け取り、そのリスト要素に対する計算の中間結果を返します。</span><span class="sxs-lookup"><span data-stu-id="54330-283">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="54330-284">2 番目の引数はアキュムレータの初期値です。</span><span class="sxs-lookup"><span data-stu-id="54330-284">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="54330-285">関数名に数字が付いている関数は、複数のリストを操作するバージョンです。</span><span class="sxs-lookup"><span data-stu-id="54330-285">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="54330-286">たとえば、 [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) 2 つのリストに対して計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="54330-286">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="54330-287">次の例は、`List.fold2` の使い方を示しています。</span><span class="sxs-lookup"><span data-stu-id="54330-287">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="54330-288">`List.fold`および[List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8)で異なる`List.fold`、余分なパラメーターの最終的な値を返しますが、`List.scan`余分なパラメーターの (と共に最終的な値) の中間値の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="54330-288">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="54330-289">これらの関数が含まれています逆引きバリエーションの 1 つ、たとえば、 [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)順序が異なりますリストの走査順序と引数の順序。</span><span class="sxs-lookup"><span data-stu-id="54330-289">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="54330-290">また、`List.fold`と`List.foldBack`のバリエーションがある[List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)と[List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)、同じ長さの 2 つのリストを受け取る。</span><span class="sxs-lookup"><span data-stu-id="54330-290">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="54330-291">各要素に対して実行される関数では、両方のリストの対応する要素を使用して操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="54330-291">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="54330-292">2 つのリストの要素の型が同じである必要はありません。たとえば、次の例では、一方のリストには銀行口座の取引金額が格納され、もう一方のリストには取引の種類 (預け入れまたは引き出し) が格納されています。</span><span class="sxs-lookup"><span data-stu-id="54330-292">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="54330-293">合計のような計算の場合は、結果が走査の順序に依存しないため、`List.fold` と `List.foldBack` のどちらを使用しても、同じ結果になります。</span><span class="sxs-lookup"><span data-stu-id="54330-293">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="54330-294">次の例では、`List.foldBack` を使用してリストの要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="54330-294">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="54330-295">次の例では、銀行口座の例に戻ります。</span><span class="sxs-lookup"><span data-stu-id="54330-295">The following example returns to the bank account example.</span></span> <span data-ttu-id="54330-296">今度は、利息を計算する新しい取引の種類が追加されています。</span><span class="sxs-lookup"><span data-stu-id="54330-296">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="54330-297">取引の順序によって期末残高が異なります。</span><span class="sxs-lookup"><span data-stu-id="54330-297">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="54330-298">関数は、 [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b)のようなもの`List.fold`と`List.scan`する点を除いて、別のアキュムレータを受け渡すのではなく`List.reduce`の代わりに、要素型の 2 つの引数を受け取る関数を受け取ります1 回、およびこれらの引数の 1 つがアキュムレータ計算の中間結果の保存ととして機能します。</span><span class="sxs-lookup"><span data-stu-id="54330-298">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="54330-299">`List.reduce` は、初めに最初の 2 つのリスト要素に対して演算を実行し、次にその演算の結果と次の要素を合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="54330-299">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="54330-300">独自の型を持つ別のアキュムレータがないため、`List.reduce` を `List.fold` の代わりに使用できるのは、アキュムレータと要素が同じ型を持つ場合だけです。</span><span class="sxs-lookup"><span data-stu-id="54330-300">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="54330-301">`List.reduce` を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="54330-301">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="54330-302">指定されたリストに要素がない場合、`List.reduce` は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="54330-302">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="54330-303">次のコードでは、ラムダ式の最初の呼び出しで引数 2 と 4 を受け取って 6 を返し、次の呼び出しで引数 6 と 10 を受け取るので、結果が 16 になります。</span><span class="sxs-lookup"><span data-stu-id="54330-303">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="54330-304">リストと他のコレクション型との変換</span><span class="sxs-lookup"><span data-stu-id="54330-304">Converting Between Lists and Other Collection Types</span></span>
<span data-ttu-id="54330-305">`List` モジュールには、シーケンスと配列との間で両方向の変換を行うための関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="54330-305">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="54330-306">シーケンスの間に変換する[List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0)または[List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)です。</span><span class="sxs-lookup"><span data-stu-id="54330-306">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="54330-307">または配列に変換する[List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547)または[List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)です。</span><span class="sxs-lookup"><span data-stu-id="54330-307">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>


### <a name="additional-operations"></a><span data-ttu-id="54330-308">その他の操作</span><span class="sxs-lookup"><span data-stu-id="54330-308">Additional Operations</span></span>
<span data-ttu-id="54330-309">リストに追加の操作については、ライブラリのリファレンス トピックを参照してください。 [Collections.List モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="54330-309">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>


## <a name="see-also"></a><span data-ttu-id="54330-310">関連項目</span><span class="sxs-lookup"><span data-stu-id="54330-310">See Also</span></span>
[<span data-ttu-id="54330-311">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="54330-311">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="54330-312">F# の型</span><span class="sxs-lookup"><span data-stu-id="54330-312">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="54330-313">シーケンス</span><span class="sxs-lookup"><span data-stu-id="54330-313">Sequences</span></span>](sequences.md)

[<span data-ttu-id="54330-314">配列</span><span class="sxs-lookup"><span data-stu-id="54330-314">Arrays</span></span>](arrays.md)

[<span data-ttu-id="54330-315">オプション</span><span class="sxs-lookup"><span data-stu-id="54330-315">Options</span></span>](options.md)
