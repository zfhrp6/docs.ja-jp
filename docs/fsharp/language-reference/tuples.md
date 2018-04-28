---
title: タプル (F#)
description: F# タプル、名前のないが、順序付けられた、可能性のある異なる型の値のグループ化について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9710f4996a952fdeaab07a30916215f27969e1a3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="tuples"></a><span data-ttu-id="f082f-103">タプル</span><span class="sxs-lookup"><span data-stu-id="f082f-103">Tuples</span></span>

<span data-ttu-id="f082f-104">A*組*名前のないが、順序付けられた、可能性のある異なる型の値のグループです。</span><span class="sxs-lookup"><span data-stu-id="f082f-104">A *tuple* is a grouping of unnamed but ordered values, possibly of different types.</span></span>  <span data-ttu-id="f082f-105">参照型または構造体の組はできますか。</span><span class="sxs-lookup"><span data-stu-id="f082f-105">Tuples can either be reference types or structs.</span></span>

## <a name="syntax"></a><span data-ttu-id="f082f-106">構文</span><span class="sxs-lookup"><span data-stu-id="f082f-106">Syntax</span></span>

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a><span data-ttu-id="f082f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f082f-107">Remarks</span></span>
<span data-ttu-id="f082f-108">各*要素*前の構文では有効な f# 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f082f-108">Each *element* in the previous syntax can be any valid F# expression.</span></span>

## <a name="examples"></a><span data-ttu-id="f082f-109">使用例</span><span class="sxs-lookup"><span data-stu-id="f082f-109">Examples</span></span>
<span data-ttu-id="f082f-110">組には、ペア 3 要素、やなど、同じまたは異なる型のなどがあります。</span><span class="sxs-lookup"><span data-stu-id="f082f-110">Examples of tuples include pairs, triples, and so on, of the same or different types.</span></span> <span data-ttu-id="f082f-111">いくつかの例は、次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="f082f-111">Some examples are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a><span data-ttu-id="f082f-112">個々 の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="f082f-112">Obtaining Individual Values</span></span>
<span data-ttu-id="f082f-113">使えばパターン マッチにアクセスしたり、タプル要素の名前を割り当てる、次のコードに示すようにできます。</span><span class="sxs-lookup"><span data-stu-id="f082f-113">You can use pattern matching to access and assign names for tuple elements, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

<span data-ttu-id="f082f-114">外部のパターン マッチを使用して、組を分解することができますも、`match`を介して式`let`バインド。</span><span class="sxs-lookup"><span data-stu-id="f082f-114">You can also deconstruct a tuple via pattern matching outside of a `match` expression via  `let` binding:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

<span data-ttu-id="f082f-115">パターンを作成できますまたは関数への入力としての組が一致します。</span><span class="sxs-lookup"><span data-stu-id="f082f-115">Or you can pattern match on tuples as inputs to functions:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

<span data-ttu-id="f082f-116">タプルの 1 つだけの要素を必要がある場合、必要としない値の新しい名前を作成しないようにする、ワイルドカード文字 (アンダー スコア) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f082f-116">If you need only one element of the tuple, the wildcard character (the underscore) can be used to avoid creating a new name for a value that you do not need.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

<span data-ttu-id="f082f-117">構造体の組に参照組内の要素のコピーも簡単です。</span><span class="sxs-lookup"><span data-stu-id="f082f-117">Copying elements from a reference tuple into a struct tuple is also simple:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

<span data-ttu-id="f082f-118">関数は、`fst`と`snd`(組のみを参照)、最初を返し、2 番目のタプル要素のそれぞれします。</span><span class="sxs-lookup"><span data-stu-id="f082f-118">The functions `fst` and `snd` (reference tuples only) return the first and second elements of a tuple, respectively.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

<span data-ttu-id="f082f-119">3 つの 3 番目の要素を返す組み込み関数はありませんが、次のように簡単に記述いずれか。</span><span class="sxs-lookup"><span data-stu-id="f082f-119">There is no built-in function that returns the third element of a triple, but you can easily write one as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

<span data-ttu-id="f082f-120">一般に、パターン マッチを使用して個々 のタプル要素にアクセスすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f082f-120">Generally, it is better to use pattern matching to access individual tuple elements.</span></span>

## <a name="using-tuples"></a><span data-ttu-id="f082f-121">組の使用</span><span class="sxs-lookup"><span data-stu-id="f082f-121">Using Tuples</span></span>
<span data-ttu-id="f082f-122">組は、次の例で示すように、関数から複数の値を返す便利な手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f082f-122">Tuples provide a convenient way to return multiple values from a function, as shown in the following example.</span></span> <span data-ttu-id="f082f-123">この例では、整数の除算を実行し、結果を丸め、タプルのペアの最初のメンバーとして操作と、ペアの 2 番目のメンバーとして残りの部分を返します。</span><span class="sxs-lookup"><span data-stu-id="f082f-123">This example performs integer division and returns the rounded result of the operation as a first member of a tuple pair and the remainder as a second member of the pair.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

<span data-ttu-id="f082f-124">暗黙的なカリー化関数の引数は、通常の関数の構文で指定されるを避けたい場合に、組を関数の引数として使用もできます。</span><span class="sxs-lookup"><span data-stu-id="f082f-124">Tuples can also be used as function arguments when you want to avoid the implicit currying of function arguments that is implied by the usual function syntax.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

<span data-ttu-id="f082f-125">関数を定義するには、通常の構文`let sum a b = a + b`次のコードに示すように、関数の最初の引数の部分的なアプリケーションである関数を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="f082f-125">The usual syntax for defining the function `let sum a b = a + b` enables you to define a function that is the partial application of the first argument of the function, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

<span data-ttu-id="f082f-126">パラメーターとしての組を使用するには、カリー化と無効になります。</span><span class="sxs-lookup"><span data-stu-id="f082f-126">Using a tuple as the parameter disables currying.</span></span> <span data-ttu-id="f082f-127">詳細についてを参照してください「部分的なアプリケーションの引数」[関数](functions/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="f082f-127">For more information, see "Partial Application of Arguments" in [Functions](functions/index.md).</span></span>

## <a name="names-of-tuple-types"></a><span data-ttu-id="f082f-128">タプルの型の名前</span><span class="sxs-lookup"><span data-stu-id="f082f-128">Names of Tuple Types</span></span>
<span data-ttu-id="f082f-129">使用する組のある型の名前を記述するときに、`*`要素を区切る記号。</span><span class="sxs-lookup"><span data-stu-id="f082f-129">When you write out the name of a type that is a tuple, you use the `*` symbol to separate elements.</span></span> <span data-ttu-id="f082f-130">構成される組の`int`、 `float`、および`string`など`(10, 10.0, "ten")`型が次のように書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="f082f-130">For a tuple that consists of an `int`, a `float`, and a `string`, such as `(10, 10.0, "ten")`, the type would be written as follows.</span></span>

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a><span data-ttu-id="f082f-131">C# の組との相互運用</span><span class="sxs-lookup"><span data-stu-id="f082f-131">Interoperation with C# Tuples</span></span>

<span data-ttu-id="f082f-132">C# 7.0 では、組を言語で導入されました。</span><span class="sxs-lookup"><span data-stu-id="f082f-132">C# 7.0 introduced tuples to the language.</span></span>  <span data-ttu-id="f082f-133">C# 内の組構造体と f# の構造体のタプルに同じです。</span><span class="sxs-lookup"><span data-stu-id="f082f-133">Tuples in C# are structs, and are equivalent to struct tuples in F#.</span></span>  <span data-ttu-id="f082f-134">C# と相互運用する必要がある場合は、構造体の組を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f082f-134">If you need to interoperate with C#, you must use struct tuples.</span></span>

<span data-ttu-id="f082f-135">これは簡単に行えます。</span><span class="sxs-lookup"><span data-stu-id="f082f-135">This is easy to do.</span></span>  <span data-ttu-id="f082f-136">たとえば、c# のクラスに組を渡すし、これは、組でも、その結果を使用する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="f082f-136">For example, imagine you have to pass a tuple to a C# class and then consume its result, which is also a tuple:</span></span>

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

<span data-ttu-id="f082f-137">F# コードで、パラメーターとして構造体の組を渡すし、構造体タプルとして結果を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f082f-137">In your F# code, you can then pass a struct tuple as the parameter and consume the result as a struct tuple.</span></span>

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a><span data-ttu-id="f082f-138">参照の組と構造体の組の間で変換します。</span><span class="sxs-lookup"><span data-stu-id="f082f-138">Converting between Reference Tuples and Struct Tuples</span></span>

<span data-ttu-id="f082f-139">参照の組と構造体の組は、完全に別の基になる表現であるために、暗黙的に変換できることはできません。</span><span class="sxs-lookup"><span data-stu-id="f082f-139">Because Reference Tuples and Struct Tuples have a completely different underlying representation, they are not implicitly convertible.</span></span>  <span data-ttu-id="f082f-140">つまり、次のようなコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="f082f-140">That is, code such as the following won't compile:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

<span data-ttu-id="f082f-141">パターンを作成する必要があります 1 つの組が一致し、他の構成要素を構築します。</span><span class="sxs-lookup"><span data-stu-id="f082f-141">You must pattern match on one tuple and construct the other with the constituent parts.</span></span>  <span data-ttu-id="f082f-142">例えば:</span><span class="sxs-lookup"><span data-stu-id="f082f-142">For example:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a><span data-ttu-id="f082f-143">参照の組をコンパイルした形式</span><span class="sxs-lookup"><span data-stu-id="f082f-143">Compiled Form of Reference Tuples</span></span>
<span data-ttu-id="f082f-144">コンパイル時に、タプルの形式を説明します。</span><span class="sxs-lookup"><span data-stu-id="f082f-144">This section explains the form of tuples when they're compiled.</span></span>  <span data-ttu-id="f082f-145">ここにある情報は、.NET Framework 3.5 を対象としている場合を除き、読み取りに必要なまたは下限はありません。</span><span class="sxs-lookup"><span data-stu-id="f082f-145">The information here isn't necessary to read unless you are targeting .NET Framework 3.5 or lower.</span></span>

<span data-ttu-id="f082f-146">組はすべての名前付き、いくつかのジェネリック型の 1 つのオブジェクトにコンパイル`System.Tuple`アリティ、または型パラメーターの数のオーバー ロードです。</span><span class="sxs-lookup"><span data-stu-id="f082f-146">Tuples are compiled into objects of one of several generic types, all named `System.Tuple`, that are overloaded on the arity, or number of type parameters.</span></span> <span data-ttu-id="f082f-147">タプル型は、c# または Visual Basic などの他の言語から表示するときに、またはを f# の構成要素に対応していないツールを使用しているときに、このフォームに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f082f-147">Tuple types appear in this form when you view them from another language, such as C# or Visual Basic, or when you are using a tool that is not aware of F# constructs.</span></span> <span data-ttu-id="f082f-148">`Tuple`型は .NET Framework 4 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="f082f-148">The `Tuple` types were introduced in .NET Framework 4.</span></span> <span data-ttu-id="f082f-149">コンパイラのバージョンを使用して、.NET Framework の以前のバージョンを対象とする場合[System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) 2.0 のバージョンの f# コア ライブラリからです。</span><span class="sxs-lookup"><span data-stu-id="f082f-149">If you are targeting an earlier version of the .NET Framework, the compiler uses versions of [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) from the 2.0 version of the F# Core Library.</span></span> <span data-ttu-id="f082f-150">このライブラリ内の型は、2.0、3.0、および 3.5、.NET Framework のバージョンを対象とするアプリケーションでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="f082f-150">The types in this library are used only for applications that target the 2.0, 3.0, and 3.5 versions of the .NET Framework.</span></span> <span data-ttu-id="f082f-151">型の転送は .NET Framework 2.0 と .NET Framework 4 の F# でのコンポーネント間でのバイナリの互換性を確保するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f082f-151">Type forwarding is used to ensure binary compatibility between .NET Framework 2.0 and .NET Framework 4 F# components.</span></span>

### <a name="compiled-form-of-struct-tuples"></a><span data-ttu-id="f082f-152">構造体の組をコンパイルした形式</span><span class="sxs-lookup"><span data-stu-id="f082f-152">Compiled Form of Struct Tuples</span></span>

<span data-ttu-id="f082f-153">構造体の組 (たとえば、 `struct (x, y)`)、参照の組から基本的に異なります。</span><span class="sxs-lookup"><span data-stu-id="f082f-153">Struct tuples (for example, `struct (x, y)`), are fundamentally different from reference tuples.</span></span>  <span data-ttu-id="f082f-154">コンパイル、<xref:System.ValueTuple>アリティ、または型パラメーターの数によってオーバー ロードされた型。</span><span class="sxs-lookup"><span data-stu-id="f082f-154">They are compiled into the <xref:System.ValueTuple> type, overloaded by arity, or the number of type parameters.</span></span>  <span data-ttu-id="f082f-155">これらと同じ[c# 7.0 組](../../csharp/tuples.md)と[Visual Basic 2017 組](../../visual-basic/programming-guide/language-features/data-types/tuples.md)、双方向の相互運用とします。</span><span class="sxs-lookup"><span data-stu-id="f082f-155">They are equivalent to [C# 7.0 Tuples](../../csharp/tuples.md) and [Visual Basic 2017 Tuples](../../visual-basic/programming-guide/language-features/data-types/tuples.md), and interoperate bidirectionally.</span></span>

## <a name="see-also"></a><span data-ttu-id="f082f-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="f082f-156">See Also</span></span>
[<span data-ttu-id="f082f-157">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="f082f-157">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f082f-158">F# の型</span><span class="sxs-lookup"><span data-stu-id="f082f-158">F# Types</span></span>](fsharp-types.md)
