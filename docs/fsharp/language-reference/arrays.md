---
title: 配列 (F#)
description: 作成して、f# のプログラミング言語の配列を使用する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 650321e864556ff0ba8591e09ffa34877c8a39b7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="arrays"></a><span data-ttu-id="b0393-103">配列</span><span class="sxs-lookup"><span data-stu-id="b0393-103">Arrays</span></span>

> [!NOTE]
<span data-ttu-id="b0393-104">API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="b0393-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="b0393-105">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="b0393-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="b0393-106">配列は、0 から始まる一連のデータ要素の、固定サイズの変更可能なコレクションで、その型はすべて同じです。</span><span class="sxs-lookup"><span data-stu-id="b0393-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="b0393-107">配列の作成</span><span class="sxs-lookup"><span data-stu-id="b0393-107">Creating Arrays</span></span>
<span data-ttu-id="b0393-108">配列は複数の方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-108">You can create arrays in several ways.</span></span> <span data-ttu-id="b0393-109">間の連続した値を一覧表示して、小さな配列を作成することができます`[|`と`|]`次の例のように、セミコロンで区切られたとします。</span><span class="sxs-lookup"><span data-stu-id="b0393-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="b0393-110">各要素を別々の行に配置することもでき、その場合は、セミコロンの区切り記号を省略できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="b0393-111">配列の要素の型は、使用されるリテラルから推論され、すべて同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0393-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="b0393-112">次のコードは、1.0 が浮動小数点数で、2 と 3 は整数であるため、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="b0393-113">シーケンス式を使用して配列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0393-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="b0393-114">1 から 10 までの整数の 2 乗の配列を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="b0393-115">すべての要素が 0 に初期化される配列を作成するには、`Array.zeroCreate` を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0393-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a><span data-ttu-id="b0393-116">要素へのアクセス</span><span class="sxs-lookup"><span data-stu-id="b0393-116">Accessing Elements</span></span>

<span data-ttu-id="b0393-117">ドット演算子を使用して配列要素にアクセスすることができます (`.`) と角かっこ (`[`と`]`)。</span><span class="sxs-lookup"><span data-stu-id="b0393-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="b0393-118">配列のインデックスは、0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="b0393-118">Array indexes start at 0.</span></span>

<span data-ttu-id="b0393-119">また、スライス表記を使用して配列の要素にアクセスすることもできます。この方法では、配列のサブ範囲を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="b0393-120">スライス表記の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="b0393-121">スライス表記を使用するときは、配列の新しいコピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0393-121">When slice notation is used, a new copy of the array is created.</span></span>


## <a name="array-types-and-modules"></a><span data-ttu-id="b0393-122">配列の型とモジュール</span><span class="sxs-lookup"><span data-stu-id="b0393-122">Array Types and Modules</span></span>
<span data-ttu-id="b0393-123">F# の配列の型はすべて、.NET Framework 型の <xref:System.Array?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="b0393-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b0393-124">したがって、F# の配列では、<xref:System.Array?displayProperty=nameWithType> で使用できるすべての機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b0393-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b0393-125">ライブラリ モジュール[ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) 1 次元配列の操作をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b0393-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="b0393-126">`Array2D`、`Array3D`、`Array4D` の各モジュールには、それぞれ、2 次元、3 次元、4 次元の配列の操作をサポートする関数があります。</span><span class="sxs-lookup"><span data-stu-id="b0393-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="b0393-127">4 より大きいランクの配列は、<xref:System.Array?displayProperty=nameWithType> を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="b0393-128">単純な関数</span><span class="sxs-lookup"><span data-stu-id="b0393-128">Simple Functions</span></span>
<span data-ttu-id="b0393-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) 要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="b0393-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="b0393-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) 配列の長さを示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="b0393-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) 要素を指定した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b0393-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="b0393-132">これらの関数の使い方を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="b0393-133">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0393-133">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="b0393-134">配列を作成する関数</span><span class="sxs-lookup"><span data-stu-id="b0393-134">Functions That Create Arrays</span></span>

<span data-ttu-id="b0393-135">既存の配列を必要とせずに配列を作成できる関数がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="b0393-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="b0393-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) すべての要素を含まない新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="b0393-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) 指定したサイズの配列を作成し、すべての要素を指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b0393-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="b0393-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) ディメンションと、要素を生成する関数を指定、配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="b0393-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) すべての要素が配列の型の値 0 に初期化される配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="b0393-140">これらの関数の例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="b0393-141">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0393-141">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="b0393-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) 既存の配列からコピーされる要素を含む新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="b0393-143">コピーは簡易コピーです。つまり、要素の型が参照型である場合は、参照だけがコピーされ、基になっているオブジェクトはコピーされません。</span><span class="sxs-lookup"><span data-stu-id="b0393-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="b0393-144">これを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="b0393-145">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-145">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="b0393-146">`Test1` という文字列は、最初の配列にのみ表示されます。これは、`firstArray` の参照が、新しい要素を作成する操作によって上書きされるものの、空の文字列への元の参照は影響を受けず、`secondArray` にまだ存在しているためです。</span><span class="sxs-lookup"><span data-stu-id="b0393-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="b0393-147">`Test2` という文字列は、両方の配列で表示されます。これは、`Insert` 型に対する <xref:System.Text.StringBuilder?displayProperty=nameWithType> 操作は基になっている <xref:System.Text.StringBuilder?displayProperty=nameWithType> オブジェクトに影響を与え、このオブジェクトは両方の配列で参照されているためです。</span><span class="sxs-lookup"><span data-stu-id="b0393-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="b0393-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) 配列のサブ範囲から新しい配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="b0393-149">サブ範囲は、開始インデックスと長さで指定します。</span><span class="sxs-lookup"><span data-stu-id="b0393-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="b0393-150">`Array.sub` を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="b0393-151">出力では、サブ配列が要素 5 から開始し、10 個の要素を含むことが示されています。</span><span class="sxs-lookup"><span data-stu-id="b0393-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="b0393-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) 2 つの既存の配列を組み合わせることにより新しい配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="b0393-153">次のコード例**Array.append**です。</span><span class="sxs-lookup"><span data-stu-id="b0393-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="b0393-154">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-154">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="b0393-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) 新しい配列に含める配列の要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="b0393-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="b0393-156">次のコードで `Array.choose` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="b0393-157">配列の要素の型は、オプションの型で返される値の型と一致している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b0393-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="b0393-158">この例では、要素の型は `int` ですが、オプションは多項式関数 `elem*elem - 1` の結果であり、浮動小数点数です。</span><span class="sxs-lookup"><span data-stu-id="b0393-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="b0393-159">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-159">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="b0393-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) 既存の配列の各配列要素で指定された関数を実行し、関数によって生成された要素を収集して、新しい配列に結合します。</span><span class="sxs-lookup"><span data-stu-id="b0393-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="b0393-161">次のコードで `Array.collect` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="b0393-162">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-162">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="b0393-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) 一連の配列を受け取るし、1 つの配列に結合します。</span><span class="sxs-lookup"><span data-stu-id="b0393-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="b0393-164">次のコードで `Array.concat` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="b0393-165">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-165">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="b0393-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) ブール条件関数を受け取りし、条件が true、入力配列の要素のみを含む新しい配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="b0393-167">次のコードで `Array.filter` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="b0393-168">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-168">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="b0393-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) 既存の配列の順序を反転する新しい配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="b0393-170">次のコードで `Array.rev` の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="b0393-171">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-171">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="b0393-172">パイプライン演算子を使用して配列を変換する、配列モジュール内の関数を簡単に組み合わせることができます (`|>`)、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b0393-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="b0393-173">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-173">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="b0393-174">多次元配列</span><span class="sxs-lookup"><span data-stu-id="b0393-174">Multidimensional Arrays</span></span>

<span data-ttu-id="b0393-175">多次元配列を作成できますが、多次元配列リテラルを記述するための構文はありません。</span><span class="sxs-lookup"><span data-stu-id="b0393-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="b0393-176">演算子を使用して[ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236)の配列要素のシーケンスのシーケンスから配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="b0393-177">シーケンスには、配列リテラルまたはリスト リテラルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="b0393-178">たとえば、次のコードでは 2 次元の配列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0393-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="b0393-179">関数を使用することもできます。 [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b)関数は次の 3 つおよび 4 つの次元の配列の使用可能な、および同様、2 次元の配列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="b0393-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="b0393-180">これらの関数は、要素の作成に使用する関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b0393-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="b0393-181">関数を指定する代わりに、初期値に設定された要素を含む 2 次元配列を作成するには、使用、 [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804)関数で使用可能なも最大で 4 つのディメンションの配列。</span><span class="sxs-lookup"><span data-stu-id="b0393-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="b0393-182">次のコード例では、まず、目的の要素を含む複数の配列から成る 1 つの配列を作成し、次に、`Array2D.init` を使用して目的の 2 次元配列を生成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="b0393-183">配列インデックスとスライス構文は、4 ランクまでの配列に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="b0393-184">複数の次元でインデックスを指定するときに使用するコンマ、インデックスを分割するのに次のコード例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b0393-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
<span data-ttu-id="b0393-185">2 次元配列の型は `<type>[,]` として書き出され (`int[,]`、`double[,]` など)、3 次元配列の型は `<type>[,,]` として書き出されます。このように、次元が高くなるにつれ、書き出される型が変わります。</span><span class="sxs-lookup"><span data-stu-id="b0393-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="b0393-186">1 次元配列で使用できる関数のサブセットのうち、多次元配列でも使用できるのは一部だけです。</span><span class="sxs-lookup"><span data-stu-id="b0393-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="b0393-187">詳細については、次を参照してください。 [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)、 [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d)、 [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)、および[ `Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="b0393-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="b0393-188">配列スライスと多次元配列</span><span class="sxs-lookup"><span data-stu-id="b0393-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="b0393-189">2 次元配列 (行列) では、範囲を指定し、ワイルドカードを使用して、サブ行列を抽出できます (`*`) 行全体または列を指定する文字。</span><span class="sxs-lookup"><span data-stu-id="b0393-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="b0393-190">F# 3.1 では、多次元配列を同じまたは低い次元のサブ配列に多次元配列を分解することができます。</span><span class="sxs-lookup"><span data-stu-id="b0393-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="b0393-191">たとえば、単一の行または列を指定して、行列からベクターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="b0393-192">このスライス構文は、要素アクセス演算子およびオーバーロードされた `GetSlice` メソッドを実装する型に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="b0393-193">たとえば、次のコードは、F# 2D 配列をラップし、配列のインデックスのサポートを提供する項目プロパティを実装し、3 つのバージョンの `GetSlice` を実装するマトリックス型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="b0393-194">マトリックス型のテンプレートとしてこのコードの使用が可能であれば、このセクションで説明するすべてのスライスの操作を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0393-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart = 
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish = 
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart = 
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish = 
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="b0393-195">配列に対するブール条件</span><span class="sxs-lookup"><span data-stu-id="b0393-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="b0393-196">関数は、 [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9)と[ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e)それぞれ 1 つまたは 2 つの配列の要素をテストします。</span><span class="sxs-lookup"><span data-stu-id="b0393-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="b0393-197">これらの関数は、テスト用の関数を受け取り、要素 (または `true` の場合は要素のペア) のうち、条件を満たす要素がある場合は `Array.exists2` を返します。</span><span class="sxs-lookup"><span data-stu-id="b0393-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="b0393-198">次のコードは、`Array.exists` と `Array.exists2` の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b0393-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="b0393-199">これらの例では、ただ 1 つの引数 (この場合は関数引数) を適用することで、新しい関数を作成しています。</span><span class="sxs-lookup"><span data-stu-id="b0393-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="b0393-200">このコードによる出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-200">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="b0393-201">同様に、関数は、 [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4)のすべての要素がブール条件を満たすかどうかを決定する配列をテストします。</span><span class="sxs-lookup"><span data-stu-id="b0393-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="b0393-202">バリエーション[ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9)を同じ長さの 2 つの配列の要素を含むブール関数を使用して、同じことがします。</span><span class="sxs-lookup"><span data-stu-id="b0393-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="b0393-203">これらの関数の使い方を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="b0393-204">これらの例の出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b0393-204">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="b0393-205">配列の検索</span><span class="sxs-lookup"><span data-stu-id="b0393-205">Searching Arrays</span></span>

<span data-ttu-id="b0393-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) ブール関数を受け取り、関数が返されますの最初の要素を返します`true`、発生させるか、<xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType>条件を満たす要素が存在しない場合。</span><span class="sxs-lookup"><span data-stu-id="b0393-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="b0393-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) 同様に、`Array.find`要素自体ではなく、要素のインデックスを返します点を除き、します。</span><span class="sxs-lookup"><span data-stu-id="b0393-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="b0393-208">次のコードでは、`Array.find` と `Array.findIndex` を使用して、完全平方かつ完全立方である値を探しています。</span><span class="sxs-lookup"><span data-stu-id="b0393-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="b0393-209">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0393-209">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="b0393-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) 同様に、`Array.find`ことを除き、その結果、オプション型でありを返します、`None`要素が存在しない場合。</span><span class="sxs-lookup"><span data-stu-id="b0393-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="b0393-211">一致する要素が配列内にあるかどうかわからない場合は、`Array.tryFind` ではなく、`Array.find` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="b0393-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="b0393-212">同様に、 [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a)に似ています[ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)いる点を除いて、オプションの種類は、戻り値。</span><span class="sxs-lookup"><span data-stu-id="b0393-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="b0393-213">要素が見つからない場合、オプションは `None` です。</span><span class="sxs-lookup"><span data-stu-id="b0393-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="b0393-214">`Array.tryFind` を使用したコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="b0393-215">このコードでは、前に示したコードを利用しています。</span><span class="sxs-lookup"><span data-stu-id="b0393-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="b0393-216">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0393-216">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="b0393-217">使用して[ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e)を見つけるだけでなく、要素を変換する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="b0393-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="b0393-218">この関数の結果は、変換した要素をオプションの値として返した最初の要素になります。該当する要素が見つからない場合は、`None` を返します。</span><span class="sxs-lookup"><span data-stu-id="b0393-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="b0393-219">`Array.tryPick` の使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="b0393-220">この例では、ラムダ式の代わりに、複数のローカル ヘルパー関数を定義することでコードを簡単にしています。</span><span class="sxs-lookup"><span data-stu-id="b0393-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="b0393-221">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0393-221">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="b0393-222">配列に対する計算の実行</span><span class="sxs-lookup"><span data-stu-id="b0393-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="b0393-223">[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e)関数は、配列内の各要素の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="b0393-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="b0393-224">この関数を使用できるのは、整数による正確な除算がサポートされている要素型だけです。そのため、浮動小数点型では使用できますが、整数型では使用できません。</span><span class="sxs-lookup"><span data-stu-id="b0393-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="b0393-225">[ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54)関数は、各要素に対して関数の呼び出しの結果の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="b0393-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="b0393-226">整数型の配列の場合は、`Array.averageBy` を使用し、この関数で各要素を浮動小数点型に変換して計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0393-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="b0393-227">使用して[ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b)または[ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd)要素の型がサポートされている場合、最大値または最小の要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="b0393-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="b0393-228">同様に、 [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045)と[ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f)を最初に実行する、比較をサポートする型に変換する関数を許可します。</span><span class="sxs-lookup"><span data-stu-id="b0393-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="b0393-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) 配列の要素を追加し、 [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b)各要素に対して関数を呼び出し、結果を加算します。</span><span class="sxs-lookup"><span data-stu-id="b0393-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="b0393-230">配列内の各要素に関数を実行するには、戻り値を格納することがなく、 [ `Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)です。</span><span class="sxs-lookup"><span data-stu-id="b0393-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="b0393-231">同じ長さの 2 つの配列に関連する関数、 [ `Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc)です。</span><span class="sxs-lookup"><span data-stu-id="b0393-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="b0393-232">場合は、関数の結果の配列を保持する必要がありますを使用して[ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45)または[ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c)、一度に 2 つの配列で動作します。</span><span class="sxs-lookup"><span data-stu-id="b0393-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="b0393-233">バリエーション[ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486)と[ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405)計算に関与する要素のインデックスを使用する以外の場合も同様です[ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4)および[ `Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)です。</span><span class="sxs-lookup"><span data-stu-id="b0393-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="b0393-234">関数は、 [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09)、 [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c)、 [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d)、 [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9)、 [`Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)、および[ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad)アルゴリズム配列のすべての要素を実行します。</span><span class="sxs-lookup"><span data-stu-id="b0393-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="b0393-235">同様に、 [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79)と[ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) 2 つの配列に対して計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="b0393-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="b0393-236">同じ名前の関数に対応している計算を実行するこれらの関数、 [List モジュール](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)です。</span><span class="sxs-lookup"><span data-stu-id="b0393-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="b0393-237">使用例については、次を参照してください。[一覧](lists.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0393-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="b0393-238">配列の変更</span><span class="sxs-lookup"><span data-stu-id="b0393-238">Modifying Arrays</span></span>

<span data-ttu-id="b0393-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) 要素を指定した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="b0393-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="b0393-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) 指定した値に配列の要素の範囲を設定します。</span><span class="sxs-lookup"><span data-stu-id="b0393-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="b0393-241">`Array.fill` のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b0393-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="b0393-242">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b0393-242">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="b0393-243">使用することができます[ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667)配列は 1 つのサブセクションを別の配列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="b0393-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="b0393-244">他の型との相互変換</span><span class="sxs-lookup"><span data-stu-id="b0393-244">Converting to and from Other Types</span></span>

<span data-ttu-id="b0393-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) リストから配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="b0393-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) シーケンスから配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b0393-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="b0393-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) および[ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4)配列型から他のこれらのコレクション型に変換します。</span><span class="sxs-lookup"><span data-stu-id="b0393-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="b0393-248">配列の並べ替え</span><span class="sxs-lookup"><span data-stu-id="b0393-248">Sorting Arrays</span></span>

<span data-ttu-id="b0393-249">使用して[ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312)を汎用的な比較関数を使用して配列を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="b0393-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="b0393-250">使用して[ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) 、値を生成する関数を指定すると呼ばれる、*キー*、汎用的な比較関数のキーを使用して並べ替えにします。</span><span class="sxs-lookup"><span data-stu-id="b0393-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="b0393-251">使用して[ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95)カスタム比較関数を提供する場合。</span><span class="sxs-lookup"><span data-stu-id="b0393-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="b0393-252">`Array.sort`、`Array.sortBy`、および `Array.sortWith` は、いずれも、並べ替えた配列を新しい配列として返します。</span><span class="sxs-lookup"><span data-stu-id="b0393-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="b0393-253">バリエーション[ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0)、 [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)、および[ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b)新しいパスワードを返さず、代わりに、既存の配列を変更します。</span><span class="sxs-lookup"><span data-stu-id="b0393-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="b0393-254">配列とタプル</span><span class="sxs-lookup"><span data-stu-id="b0393-254">Arrays and Tuples</span></span>

<span data-ttu-id="b0393-255">関数は、 [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187)と[ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48)タプルのペアの配列を配列のその逆の組に変換します。</span><span class="sxs-lookup"><span data-stu-id="b0393-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="b0393-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) および[ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677)が 3 つの要素の組または組の 3 つの配列を操作する点を除いてに似ています。</span><span class="sxs-lookup"><span data-stu-id="b0393-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="b0393-257">配列に対する並列計算</span><span class="sxs-lookup"><span data-stu-id="b0393-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="b0393-258">モジュール[ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09)配列に対して並列計算を実行するための関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0393-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="b0393-259">このモジュールは、Version 4 より前の .NET Framework を対象とするアプリケーションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b0393-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0393-260">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0393-260">See Also</span></span>
[<span data-ttu-id="b0393-261">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="b0393-261">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="b0393-262">F# です。型</span><span class="sxs-lookup"><span data-stu-id="b0393-262">F#; Types</span></span>](fsharp-types.md)
