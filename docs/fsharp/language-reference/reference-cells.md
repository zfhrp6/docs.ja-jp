---
title: "参照セル (F#)"
description: "F# 参照セルの記憶域の場所を有効にすると、参照セマンティクスを持つ変更可能な値を作成する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 09a0b221-ea21-45c4-bae8-5e4a339750c4
ms.openlocfilehash: c7470c9a36cf2cd24dd89ceffcf6e90c6dc4d2dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reference-cells"></a><span data-ttu-id="aefc2-104">参照セル</span><span class="sxs-lookup"><span data-stu-id="aefc2-104">Reference Cells</span></span>

<span data-ttu-id="aefc2-105">*参照セル*を有効にすると、参照セマンティクスを持つ変更可能な値を作成する記憶域の場所です。</span><span class="sxs-lookup"><span data-stu-id="aefc2-105">*Reference cells* are storage locations that enable you to create mutable values with reference semantics.</span></span>

## <a name="syntax"></a><span data-ttu-id="aefc2-106">構文</span><span class="sxs-lookup"><span data-stu-id="aefc2-106">Syntax</span></span>

```fsharp
ref expression
```

## <a name="remarks"></a><span data-ttu-id="aefc2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="aefc2-107">Remarks</span></span>
<span data-ttu-id="aefc2-108">値をカプセル化する新しい参照セルを作成するには、値の前に `ref` 演算子を指定します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-108">You use the `ref` operator before a value to create a new reference cell that encapsulates the value.</span></span> <span data-ttu-id="aefc2-109">基になる値は変更可能なので、後で変更できます。</span><span class="sxs-lookup"><span data-stu-id="aefc2-109">You can then change the underlying value because it is mutable.</span></span>

<span data-ttu-id="aefc2-110">参照セルは、単なるアドレスではなく、実際の値を保持します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-110">A reference cell holds an actual value; it is not just an address.</span></span> <span data-ttu-id="aefc2-111">`ref` 演算子を使用して参照セルを作成すると、基の値のコピーが、カプセル化された変更可能な値として作成されます。</span><span class="sxs-lookup"><span data-stu-id="aefc2-111">When you create a reference cell by using the `ref` operator, you create a copy of the underlying value as an encapsulated mutable value.</span></span>

<span data-ttu-id="aefc2-112">参照セルを逆参照するには、`!` (感嘆符) 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-112">You can dereference a reference cell by using the `!` (bang) operator.</span></span>

<span data-ttu-id="aefc2-113">次のコード例は、参照セルの宣言と使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aefc2-113">The following code example illustrates the declaration and use of reference cells.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2201.fs)]

<span data-ttu-id="aefc2-114">出力は `50`になります。</span><span class="sxs-lookup"><span data-stu-id="aefc2-114">The output is `50`.</span></span>

<span data-ttu-id="aefc2-115">参照セルは、次のように宣言される `Ref` ジェネリック レコード型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="aefc2-115">Reference cells are instances of the `Ref` generic record type, which is declared as follows.</span></span>

```fsharp
type Ref<'a> =
{ mutable contents: 'a }
```

<span data-ttu-id="aefc2-116">`'a ref` 型は、`Ref<'a>` のシノニムです。</span><span class="sxs-lookup"><span data-stu-id="aefc2-116">The type `'a ref` is a synonym for `Ref<'a>`.</span></span> <span data-ttu-id="aefc2-117">コンパイラと IDE の IntelliSense では、この型について前者が表示されますが、基になる定義は後者です。</span><span class="sxs-lookup"><span data-stu-id="aefc2-117">The compiler and IntelliSense in the IDE display the former for this type, but the underlying definition is the latter.</span></span>

<span data-ttu-id="aefc2-118">`ref` 演算子は、新しい参照セルを作成します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-118">The `ref` operator creates a new reference cell.</span></span> <span data-ttu-id="aefc2-119">次のコードは、`ref` 演算子の宣言です。</span><span class="sxs-lookup"><span data-stu-id="aefc2-119">The following code is the declaration of the `ref` operator.</span></span>

```fsharp
let ref x = { contents = x }
```

<span data-ttu-id="aefc2-120">次の表に、参照セルで使用できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-120">The following table shows the features that are available on the reference cell.</span></span>

|<span data-ttu-id="aefc2-121">演算子、メンバー、またはフィールド</span><span class="sxs-lookup"><span data-stu-id="aefc2-121">Operator, member, or field</span></span>|<span data-ttu-id="aefc2-122">説明</span><span class="sxs-lookup"><span data-stu-id="aefc2-122">Description</span></span>|<span data-ttu-id="aefc2-123">型</span><span class="sxs-lookup"><span data-stu-id="aefc2-123">Type</span></span>|<span data-ttu-id="aefc2-124">定義</span><span class="sxs-lookup"><span data-stu-id="aefc2-124">Definition</span></span>|
|--------------------------|-----------|----|----------|
|<span data-ttu-id="aefc2-125">`!` (逆参照演算子)</span><span class="sxs-lookup"><span data-stu-id="aefc2-125">`!` (dereference operator)</span></span>|<span data-ttu-id="aefc2-126">基になる値を返します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-126">Returns the underlying value.</span></span>|`'a ref -> 'a`|`let (!) r = r.contents`|
|<span data-ttu-id="aefc2-127">`:=` (代入演算子)</span><span class="sxs-lookup"><span data-stu-id="aefc2-127">`:=` (assignment operator)</span></span>|<span data-ttu-id="aefc2-128">基になる値を変更します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-128">Changes the underlying value.</span></span>|`'a ref -> 'a -> unit`|`let (:=) r x = r.contents <- x`|
|<span data-ttu-id="aefc2-129">`ref` (演算子)</span><span class="sxs-lookup"><span data-stu-id="aefc2-129">`ref` (operator)</span></span>|<span data-ttu-id="aefc2-130">新しい参照セルに値をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-130">Encapsulates a value into a new reference cell.</span></span>|`'a -> 'a ref`|`let ref x = { contents = x }`|
|<span data-ttu-id="aefc2-131">`Value` (プロパティ)</span><span class="sxs-lookup"><span data-stu-id="aefc2-131">`Value` (property)</span></span>|<span data-ttu-id="aefc2-132">基になる値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-132">Gets or sets the underlying value.</span></span>|`unit -> 'a`|`member x.Value = x.contents`|
|<span data-ttu-id="aefc2-133">`contents` (レコード フィールド)</span><span class="sxs-lookup"><span data-stu-id="aefc2-133">`contents` (record field)</span></span>|<span data-ttu-id="aefc2-134">基になる値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-134">Gets or sets the underlying value.</span></span>|`'a`|`let ref x = { contents = x }`|
<span data-ttu-id="aefc2-135">基になる値にアクセスする方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="aefc2-135">There are several ways to access the underlying value.</span></span> <span data-ttu-id="aefc2-136">逆参照演算子 (`!`) によって返される値は、代入可能な値ではありません。</span><span class="sxs-lookup"><span data-stu-id="aefc2-136">The value returned by the dereference operator (`!`) is not an assignable value.</span></span> <span data-ttu-id="aefc2-137">したがって、基になる値を変更する場合は、代わりに代入演算子 (`:=`) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aefc2-137">Therefore, if you are modifying the underlying value, you must use the assignment operator (`:=`) instead.</span></span>

<span data-ttu-id="aefc2-138">`Value` プロパティと `contents` フィールドは、いずれも代入可能な値です。</span><span class="sxs-lookup"><span data-stu-id="aefc2-138">Both the `Value` property and the `contents` field are assignable values.</span></span> <span data-ttu-id="aefc2-139">したがって、次のコードに示すように、これらを使用して基になる値にアクセスしたり、基になる値を変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="aefc2-139">Therefore, you can use these to either access or change the underlying value, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2203.fs)]

<span data-ttu-id="aefc2-140">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aefc2-140">The output is as follows.</span></span>

```
10
10
11
12
```

<span data-ttu-id="aefc2-141">`contents` フィールドは、他のバージョンの ML との互換性のために用意されており、コンパイル中に警告を生成します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-141">The field `contents` is provided for compatibility with other versions of ML and will produce a warning during compilation.</span></span> <span data-ttu-id="aefc2-142">この警告を無効にするには、`--mlcompatibility` コンパイラ オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-142">To disable the warning, use the `--mlcompatibility` compiler option.</span></span> <span data-ttu-id="aefc2-143">詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aefc2-143">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="aefc2-144">次のコードは、パラメーターの引き渡しでの参照セルの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aefc2-144">The following code illustrates the use of reference cells in parameter passing.</span></span> <span data-ttu-id="aefc2-145">インクリメンタ型には、メソッド パラメーターの型に byref を含むパラメーターを受け取るインクリメントがあります。</span><span class="sxs-lookup"><span data-stu-id="aefc2-145">The Incrementor type has a method Increment that takes a parameter that includes byref in the parameter type.</span></span> <span data-ttu-id="aefc2-146">Byref パラメーター型で渡すことを示すこと呼び出し元必要があります参照セルまたは指定した型の典型的な変数のアドレスでこのケースの整数です。残りのコードを両方の引数の型とインクリメントを呼び出す方法と参照セル (ref myDelta1) を作成する変数で、ref 演算子の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-146">The byref in the parameter type indicates that callers must pass a reference cell or the address of a typical variable of the specified type, in this case int. The remaining code illustrates how to call Increment with both of these types of arguments, and shows the use of the ref operator on a variable to create a reference cell (ref myDelta1).</span></span> <span data-ttu-id="aefc2-147">次に、アドレス演算子 (&amp;) を使用して適切な引数を生成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aefc2-147">It then shows the use of the address-of operator (&amp;) to generate an appropriate argument.</span></span> <span data-ttu-id="aefc2-148">最後に、インクリメント メソッドは、使用すると、バインドを使用して宣言されている参照セルを使用して、もう一度呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aefc2-148">Finally, the Increment method is called again by using a reference cell that is declared by using a let binding.</span></span> <span data-ttu-id="aefc2-149">コードの最後の行は、の使い方を説明します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-149">The final line of code demonstrates the use of the !</span></span> <span data-ttu-id="aefc2-150">印刷用に参照セルを逆参照演算子。</span><span class="sxs-lookup"><span data-stu-id="aefc2-150">operator to dereference the reference cell for printing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2204.fs)]

<span data-ttu-id="aefc2-151">参照渡しする方法の詳細については、次を参照してください。[パラメーターと引数](parameters-and-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="aefc2-151">For more information about how to pass by reference, see [Parameters and Arguments](parameters-and-arguments.md).</span></span>

>[!NOTE]
<span data-ttu-id="aefc2-152">C# プログラマでは、その ref 異なる動作を f# で c# では、知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="aefc2-152">C# programmers should know that ref works differently in F# than it does in C#.</span></span> <span data-ttu-id="aefc2-153">など、ref 引数を渡すときに使用するが、同じ効果 f# と c# ではします。</span><span class="sxs-lookup"><span data-stu-id="aefc2-153">For example, the use of ref when you pass an argument does not have the same effect in F# as it does in C#.</span></span>

## <a name="consuming-c-ref-returns"></a><span data-ttu-id="aefc2-154">使用 (C#)`ref`を返します</span><span class="sxs-lookup"><span data-stu-id="aefc2-154">Consuming C# `ref` returns</span></span>

<span data-ttu-id="aefc2-155">使用できる 4.1 以降では f#、 `ref` c# で生成されるを返します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-155">Starting with F# 4.1, you can consume `ref` returns generated in C#.</span></span>  <span data-ttu-id="aefc2-156">このような呼び出しの結果は、`byref<_>`ポインター。</span><span class="sxs-lookup"><span data-stu-id="aefc2-156">The result of such a call is a `byref<_>` pointer.</span></span>

<span data-ttu-id="aefc2-157">次の c# メソッド:</span><span class="sxs-lookup"><span data-stu-id="aefc2-157">The following C# method:</span></span>

```csharp
namespace RefReturns
{
    public static class RefClass
    {
        public static ref int Find(int val, int[] vals)
        {
            for (int i = 0; i < vals.Length; i++)
            {
                if (vals[i] == val)
                {
                    return ref numbers[i]; // Returns the location, not the value
                }
            }

            throw new IndexOutOfRangeException($"{nameof(number)} not found");
        }
    }
}
```

<span data-ttu-id="aefc2-158">透過的にによって呼び出し可能 f# ない特殊な構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-158">Can be transparently called by F# with no special syntax:</span></span>

```fsharp
open RefReturns

let consumeRefReturn() =
    let result = RefClass.Find(3, [| 1; 2; 3; 4; 5 |]) // 'result' is of type 'byref<int>'.
    ()
```

<span data-ttu-id="aefc2-159">かかる場合があります関数を宣言することも、`ref`など、入力として返します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-159">You can also declare functions which could take a `ref` return as input, for example:</span></span>

```fsharp
let f (x: byref<int>) = &x
```

<span data-ttu-id="aefc2-160">現在を生成する方法はありません、 `ref` f# で c# で消費されるを返します。</span><span class="sxs-lookup"><span data-stu-id="aefc2-160">There is currently no way to generate a `ref` return in F# which could be consumed in C#.</span></span>

## <a name="see-also"></a><span data-ttu-id="aefc2-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="aefc2-161">See Also</span></span>
[<span data-ttu-id="aefc2-162">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="aefc2-162">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="aefc2-163">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="aefc2-163">Parameters and Arguments</span></span>](parameters-and-arguments.md)

[<span data-ttu-id="aefc2-164">シンボルと演算子のリファレンス</span><span class="sxs-lookup"><span data-stu-id="aefc2-164">Symbol and Operator Reference</span></span>](symbol-and-operator-reference/index.md)
