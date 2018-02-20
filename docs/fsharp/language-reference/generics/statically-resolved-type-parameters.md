---
title: "静的に解決された型パラメーター (F#)"
description: "F# で使用する方法について静的に解決される型パラメーターは、実行時ではなく、コンパイル時に実際の型に置き換えられています。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b3797415-3e49-4f8a-a8ee-fa614c5721aa
ms.openlocfilehash: 14c629d6223584113af47636495be61decca02ad
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="statically-resolved-type-parameters"></a><span data-ttu-id="be65f-104">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="be65f-104">Statically Resolved Type Parameters</span></span>

<span data-ttu-id="be65f-105">A*静的に解決される型パラメーター*実行時ではなく、コンパイル時に実際の型に置き換えられる型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="be65f-105">A *statically resolved type parameter* is a type parameter that is replaced with an actual type at compile time instead of at run time.</span></span> <span data-ttu-id="be65f-106">これらの前にはキャレット (^) 記号が付きます。</span><span class="sxs-lookup"><span data-stu-id="be65f-106">They are preceded by a caret (^) symbol.</span></span>


## <a name="syntax"></a><span data-ttu-id="be65f-107">構文</span><span class="sxs-lookup"><span data-stu-id="be65f-107">Syntax</span></span>

```
ˆtype-parameter
```

## <a name="remarks"></a><span data-ttu-id="be65f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="be65f-108">Remarks</span></span>
<span data-ttu-id="be65f-109">F# 言語には、異なる 2 種類の型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="be65f-109">In the F# language, there are two distinct kinds of type parameters.</span></span> <span data-ttu-id="be65f-110">1 つ目の種類は、標準のジェネリック型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="be65f-110">The first kind is the standard generic type parameter.</span></span> <span data-ttu-id="be65f-111">これらは、`'T` や `'U` のようにアポストロフィ (') で示されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-111">These are indicated by an apostrophe ('), as in `'T` and `'U`.</span></span> <span data-ttu-id="be65f-112">これらは、他の .NET Framework 言語のジェネリック型パラメーターと同じです。</span><span class="sxs-lookup"><span data-stu-id="be65f-112">They are equivalent to generic type parameters in other .NET Framework languages.</span></span> <span data-ttu-id="be65f-113">もう 1 つの種類は、静的に解決される型パラメーターであり、`^T` や `^U` のようにキャレット記号で示されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-113">The other kind is statically resolved and is indicated by a caret symbol, as in `^T` and `^U`.</span></span>

<span data-ttu-id="be65f-114">静的に解決される型パラメーターは、主にメンバー制約で使用する場合に役立ちます。これは、型引数を使用するために特定のメンバーが必要であることを指定できる制約です。</span><span class="sxs-lookup"><span data-stu-id="be65f-114">Statically resolved type parameters are primarily useful in conjunction with member constraints, which are constraints that allow you to specify that a type argument must have a particular member or members in order to be used.</span></span> <span data-ttu-id="be65f-115">この種の制約を、標準のジェネリック型パラメーターを使用して作成する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="be65f-115">There is no way to create this kind of constraint by using a regular generic type parameter.</span></span>

<span data-ttu-id="be65f-116">2 種類の型パラメーターの類似点と相違点の概要を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="be65f-116">The following table summarizes the similarities and differences between the two kinds of type parameters.</span></span>

|<span data-ttu-id="be65f-117">機能</span><span class="sxs-lookup"><span data-stu-id="be65f-117">Feature</span></span>|<span data-ttu-id="be65f-118">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="be65f-118">Generic</span></span>|<span data-ttu-id="be65f-119">静的に解決される</span><span class="sxs-lookup"><span data-stu-id="be65f-119">Statically resolved</span></span>|
|-------|-------|-------------------|
|<span data-ttu-id="be65f-120">構文</span><span class="sxs-lookup"><span data-stu-id="be65f-120">Syntax</span></span>|<span data-ttu-id="be65f-121">`'T`, `'U`</span><span class="sxs-lookup"><span data-stu-id="be65f-121">`'T`, `'U`</span></span>|<span data-ttu-id="be65f-122">`^T`, `^U`</span><span class="sxs-lookup"><span data-stu-id="be65f-122">`^T`, `^U`</span></span>|
|<span data-ttu-id="be65f-123">解決時期</span><span class="sxs-lookup"><span data-stu-id="be65f-123">Resolution time</span></span>|<span data-ttu-id="be65f-124">実行時</span><span class="sxs-lookup"><span data-stu-id="be65f-124">Run time</span></span>|<span data-ttu-id="be65f-125">コンパイル時</span><span class="sxs-lookup"><span data-stu-id="be65f-125">Compile time</span></span>|
|<span data-ttu-id="be65f-126">メンバー制約</span><span class="sxs-lookup"><span data-stu-id="be65f-126">Member constraints</span></span>|<span data-ttu-id="be65f-127">メンバー制約では使用できません。</span><span class="sxs-lookup"><span data-stu-id="be65f-127">Cannot be used with member constraints.</span></span>|<span data-ttu-id="be65f-128">メンバー制約で使用できます。</span><span class="sxs-lookup"><span data-stu-id="be65f-128">Can be used with member constraints.</span></span>|
|<span data-ttu-id="be65f-129">コード生成</span><span class="sxs-lookup"><span data-stu-id="be65f-129">Code generation</span></span>|<span data-ttu-id="be65f-130">標準のジェネリック型パラメーターを持つ型 (またはメソッド) では、単一のジェネリック型またはジェネリック メソッドが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-130">A type (or method) with standard generic type parameters results in the generation of a single generic type or method.</span></span>|<span data-ttu-id="be65f-131">各型で必要とされる、型およびメソッドの複数のインスタンス化が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-131">Multiple instantiations of types and methods are generated, one for each type that is needed.</span></span>|
|<span data-ttu-id="be65f-132">型での使用</span><span class="sxs-lookup"><span data-stu-id="be65f-132">Use with types</span></span>|<span data-ttu-id="be65f-133">型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="be65f-133">Can be used on types.</span></span>|<span data-ttu-id="be65f-134">型では使用できません。</span><span class="sxs-lookup"><span data-stu-id="be65f-134">Cannot be used on types.</span></span>|
|<span data-ttu-id="be65f-135">インライン関数での使用</span><span class="sxs-lookup"><span data-stu-id="be65f-135">Use with inline functions</span></span>|<span data-ttu-id="be65f-136">いいえ。</span><span class="sxs-lookup"><span data-stu-id="be65f-136">No.</span></span> <span data-ttu-id="be65f-137">標準のジェネリック型パラメーターではインライン関数をパラメーター化できません。</span><span class="sxs-lookup"><span data-stu-id="be65f-137">An inline function cannot be parameterized with a standard generic type parameter.</span></span>|<span data-ttu-id="be65f-138">はい。</span><span class="sxs-lookup"><span data-stu-id="be65f-138">Yes.</span></span> <span data-ttu-id="be65f-139">静的に解決される型パラメーターは、インライン以外の関数またはメソッドでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="be65f-139">Statically resolved type parameters cannot be used on functions or methods that are not inline.</span></span>|

<span data-ttu-id="be65f-140">多数の F# コア ライブラリ関数 (特に演算子) には、静的に解決される型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="be65f-140">Many F# core library functions, especially operators, have statically resolved type parameters.</span></span> <span data-ttu-id="be65f-141">これらの関数および演算子はインラインであり、数値の計算に効率的なコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-141">These functions and operators are inline, and result in efficient code generation for numeric computations.</span></span>

<span data-ttu-id="be65f-142">演算子を使用するインライン メソッドおよび関数、または静的に解決される型パラメーターを持つ他の関数を使用するインライン メソッドおよび関数では、それらのメソッドおよび関数自体でも静的に解決される型パラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="be65f-142">Inline methods and functions that use operators, or use other functions that have statically resolved type parameters, can also use statically resolved type parameters themselves.</span></span> <span data-ttu-id="be65f-143">多くの場合、型推論では、それらのインライン関数が静的に解決される型パラメーターを持つと推論されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-143">Often, type inference infers such inline functions to have statically resolved type parameters.</span></span> <span data-ttu-id="be65f-144">静的に解決される型パラメーターを持つと推論される演算子の定義を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="be65f-144">The following example illustrates an operator definition that is inferred to have a statically resolved type parameter.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet401.fs)]

<span data-ttu-id="be65f-145">解決された `(+@)` の型は、`(+)` および `(*)` の使用に基づいており、これらの両方では型推論によって、静的に解決される型パラメーターによるメンバー制約が推論されます。</span><span class="sxs-lookup"><span data-stu-id="be65f-145">The resolved type of `(+@)` is based on the use of both `(+)` and `(*)`, both of which cause type inference to infer member constraints on the statically resolved type parameters.</span></span> <span data-ttu-id="be65f-146">F# インタープリターに表示される解決された型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be65f-146">The resolved type, as shown in the F# interpreter, is as follows.</span></span>

```fsharp
^a -> ^c -> ^d
when (^a or ^b) : (static member ( + ) : ^a * ^b -> ^d) and
(^a or ^c) : (static member ( * ) : ^a * ^c -> ^b)
```

<span data-ttu-id="be65f-147">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="be65f-147">The output is as follows.</span></span>

```
2
1.500000
```

<span data-ttu-id="be65f-148">4.1 以降では F# で、静的に解決される型のパラメーター シグネチャ内の具体的な型名も指定できます。</span><span class="sxs-lookup"><span data-stu-id="be65f-148">Starting with F# 4.1, you can also specify concrete type names in statically resolved type parameter signatures.</span></span>  <span data-ttu-id="be65f-149">言語の以前のバージョンでは、型名は実際には、コンパイラによって推論できませんでしたが、シグネチャでは実際には指定できません。</span><span class="sxs-lookup"><span data-stu-id="be65f-149">In previous versions of the language, the type name could actually be inferred by the compiler, but could not actually be specified in the signature.</span></span>  <span data-ttu-id="be65f-150">F# 4.1、時点で静的に解決される型のパラメーター シグネチャで具体的な型名を指定することも可能性があります。</span><span class="sxs-lookup"><span data-stu-id="be65f-150">As of F# 4.1, you may also specify concrete type names in statically resolved type parameter signatures.</span></span> <span data-ttu-id="be65f-151">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="be65f-151">Here's an example:</span></span>

```fsharp
type CFunctor() = 
      static member inline fmap (f: ^a -> ^b, a: ^a list) = List.map f a
      static member inline fmap (f: ^a -> ^b, a: ^a option) =
        match a with
        | None -> None
        | Some x -> Some (f x)

      // default implementation of replace
      static member inline replace< ^a, ^b, ^c, ^d, ^e when ^a :> CFunctor and (^a or ^d): (static member fmap: (^b -> ^c) * ^d -> ^e) > (a, f) =
        ((^a or ^d) : (static member fmap : (^b -> ^c) * ^d -> ^e) (konst a, f))

      // call overridden replace if present
      static member inline replace< ^a, ^b, ^c when ^b: (static member replace: ^a * ^b -> ^c)>(a: ^a, f: ^b) =
        (^b : (static member replace: ^a * ^b -> ^c) (a, f))

let inline replace_instance< ^a, ^b, ^c, ^d when (^a or ^c): (static member replace: ^b * ^c -> ^d)> (a: ^b, f: ^c) =
      ((^a or ^c): (static member replace: ^b * ^c -> ^d) (a, f))

// Note the concrete type 'CFunctor' specified in the signature
let inline replace (a: ^a) (f: ^b): ^a0 when (CFunctor or  ^b): (static member replace: ^a *  ^b ->  ^a0) =
    replace_instance<CFunctor, _, _, _> (a, f)
```

## <a name="see-also"></a><span data-ttu-id="be65f-152">参照</span><span class="sxs-lookup"><span data-stu-id="be65f-152">See Also</span></span>
[<span data-ttu-id="be65f-153">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="be65f-153">Generics</span></span>](index.md)

[<span data-ttu-id="be65f-154">型推論</span><span class="sxs-lookup"><span data-stu-id="be65f-154">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="be65f-155">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="be65f-155">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="be65f-156">制約</span><span class="sxs-lookup"><span data-stu-id="be65f-156">Constraints</span></span>](constraints.md)

[<span data-ttu-id="be65f-157">インライン関数</span><span class="sxs-lookup"><span data-stu-id="be65f-157">Inline Functions</span></span>](../functions/inline-functions.md)
