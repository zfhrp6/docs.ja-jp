---
title: "判別共用体 (F#)"
description: "F# を使用する方法を学習判別共用体です。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e2a011-c785-48c8-859f-79df7f3a0e29
ms.openlocfilehash: a374f521bcde7506bb3a9eebb627eaffcd8b94a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="discriminated-unions"></a><span data-ttu-id="0eab3-104">判別共用体</span><span class="sxs-lookup"><span data-stu-id="0eab3-104">Discriminated Unions</span></span>

<span data-ttu-id="0eab3-105">判別共用体は、数多くの名前付きケースのうちのいずれかである可能性がある値をサポートします。ケースの値や型が、それぞれ異なる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-105">Discriminated unions provide support for values that can be one of a number of named cases, possibly each with different values and types.</span></span> <span data-ttu-id="0eab3-106">判別共用体は、異種データ、有効ケースやエラー ケースなどの特殊なケースを持つ可能性のあるデータ、インスタンスごとに型が異なるデータ、小さいオブジェクト階層に対する代替手段などの場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-106">Discriminated unions are useful for heterogeneous data; data that can have special cases, including valid and error cases; data that varies in type from one instance to another; and as an alternative for small object hierarchies.</span></span> <span data-ttu-id="0eab3-107">さらに、再帰的な判別共用体は、ツリー データ構造を表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-107">In addition, recursive discriminated unions are used to represent tree data structures.</span></span>

## <a name="syntax"></a><span data-ttu-id="0eab3-108">構文</span><span class="sxs-lookup"><span data-stu-id="0eab3-108">Syntax</span></span>

```fsharp
[ attributes ]
type type-name =
    | case-identifier1 [of [ fieldname1 : ] type1 [ * [ fieldname2 : ] type2 ...]
    | case-identifier2 [of [fieldname3 : ]type3 [ * [ fieldname4 : ]type4 ...]
...
```

## <a name="remarks"></a><span data-ttu-id="0eab3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="0eab3-109">Remarks</span></span>
<span data-ttu-id="0eab3-110">判別共用体は他の言語の共用体型と似ていますが、異なる点もあります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-110">Discriminated unions are similar to union types in other languages, but there are differences.</span></span> <span data-ttu-id="0eab3-111">C++ の共用体型や Visual Basic のバリアント型と同じように、値に格納されるデータは固定ではありません。複数の異なるオプションのいずれかを格納できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-111">As with a union type in C++ or a variant type in Visual Basic, the data stored in the value is not fixed; it can be one of several distinct options.</span></span> <span data-ttu-id="0eab3-112">これら他の言語の共用体とは異なりただし、使用可能なオプションの指定、*ケース識別子*です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-112">Unlike unions in these other languages, however, each of the possible options is given a *case identifier*.</span></span> <span data-ttu-id="0eab3-113">ケース識別子には、使用できる各種の値の型の名前を指定します。指定した型のオブジェクトは値の型として使用できます。値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-113">The case identifiers are names for the various possible types of values that objects of this type could be; the values are optional.</span></span> <span data-ttu-id="0eab3-114">値を省略する場合は、ケースが列挙型のケースと等しくなります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-114">If values are not present, the case is equivalent to an enumeration case.</span></span> <span data-ttu-id="0eab3-115">値がある場合は、各値に、指定した型の単一値、あるいは同じ型または異なる型の複数のフィールドを集約したタプルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-115">If values are present, each value can either be a single value of a specified type, or a tuple that aggregates multiple fields of the same or different types.</span></span> <span data-ttu-id="0eab3-116">F# 3.1 では、個々のフィールドに名前を付けることができますが、同じケースの他のフィールドに名前が付けられていても、名前は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-116">As of F# 3.1, you can give an individual field a name, but the name is optional, even if other fields in the same case are named.</span></span>

<span data-ttu-id="0eab3-117">たとえば、Shape 型の次のような宣言を検討します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-117">For example, consider the following declaration of a Shape type.</span></span>

```fsharp
type Shape =
    | Rectangle of width : float * length : float
    | Circle of radius : float
    | Prism of width : float * float * height : float
```

<span data-ttu-id="0eab3-118">前のコードでは、判別共用体の Shape を宣言します。これには四角形、円、およびプリズムの 3 つのケースのいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-118">The preceding code declares a discriminated union Shape, which can have values of any of three cases: Rectangle, Circle, and Prism.</span></span> <span data-ttu-id="0eab3-119">各ケースに異なるフィールド セットがあります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-119">Each case has a different set of fields.</span></span> <span data-ttu-id="0eab3-120">四角形の場合は、2 つの名前付きフィールドがあり、両方とも `float` 型で、幅と長さの名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-120">The Rectangle case has two named fields, both of type `float`, that have the names width and length.</span></span> <span data-ttu-id="0eab3-121">円の場合は、1 つの名前付きフィールドがあり、半径の名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-121">The Circle case has just one named field, radius.</span></span> <span data-ttu-id="0eab3-122">プリズムの場合は、3 つのフィールドを持つ 2 つのどの (幅と高さ) で名前付きフィールドです。</span><span class="sxs-lookup"><span data-stu-id="0eab3-122">The Prism case has three fields, two of which (width and height) are named fields.</span></span> <span data-ttu-id="0eab3-123">名前のないフィールドは、匿名フィールドと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-123">Unnamed fields are referred to as anonymous fields.</span></span>

<span data-ttu-id="0eab3-124">次の例では、名前付きフィールドと匿名フィールドに値を設定してオブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-124">You construct objects by providing values for the named and anonymous fields according to the following examples.</span></span>

```fsharp
let rect = Rectangle(length = 1.3, width = 10.0)
let circ = Circle (1.0)
let prism = Prism(5., 2.0, height = 3.0)
```

<span data-ttu-id="0eab3-125">このコードは、初期化時に名前付きフィールドを使用することも、宣言時のフィールドの順序に依存して各フィールドの値のみを順番に提供することもできることを示します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-125">This code shows that you can either use the named fields in the initialization, or you can rely on the ordering of the fields in the declaration and just provide the values for each field in turn.</span></span> <span data-ttu-id="0eab3-126">前のコードの `rect` のコンストラクターの呼び出しでは名前付きフィールドを使用しますが、`circ` のコンストラクター呼び出しでは順序を使用します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-126">The constructor call for `rect` in the previous code uses the named fields, but the constructor call for `circ` uses the ordering.</span></span> <span data-ttu-id="0eab3-127">`prism` の構造のように、順序付きフィールドと名前付きフィールドを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-127">You can mix the ordered fields and named fields, as in the construction of `prism`.</span></span>

<span data-ttu-id="0eab3-128">`option` 型は、F# コア ライブラリの単純な判別共用体です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-128">The `option` type is a simple discriminated union in the F# core library.</span></span> <span data-ttu-id="0eab3-129">`option` 型は、次のように宣言されます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-129">The `option` type is declared as follows.</span></span>

```fsharp
// The option type is a discriminated union.
type Option<'a> =
    | Some of 'a
    | None
```

<span data-ttu-id="0eab3-130">このコードでは、`Option` 型が、`Some` と `None` の 2 つのケースを持つ判別共用体として指定されています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-130">The previous code specifies that the type `Option` is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="0eab3-131">`Some` ケースには、型が型パラメーター `'a` によって表される 1 つの匿名フィールドで構成される、関連付けられた値があります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-131">The `Some` case has an associated value that consists of one anonymous field whose type is represented by the type parameter `'a`.</span></span> <span data-ttu-id="0eab3-132">`None` ケースには、関連する値はありません。</span><span class="sxs-lookup"><span data-stu-id="0eab3-132">The `None` case has no associated value.</span></span> <span data-ttu-id="0eab3-133">したがって、`option` 型は、なんらかの型の値を持つジェネリック型、または値を持たないジェネリック型を指定します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-133">Thus the `option` type specifies a generic type that either has a value of some type or no value.</span></span> <span data-ttu-id="0eab3-134">また、`Option` 型には小文字の型のエイリアス `option` があり、より一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-134">The type `Option` also has a lowercase type alias, `option`, that is more commonly used.</span></span>

<span data-ttu-id="0eab3-135">ケース識別子は、判別共用体型のコンストラクターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-135">The case identifiers can be used as constructors for the discriminated union type.</span></span> <span data-ttu-id="0eab3-136">たとえば、`option` 型の値を作成するには、次のようなコードが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-136">For example, the following code is used to create values of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2001.fs)]

<span data-ttu-id="0eab3-137">ケース識別子は、パターン マッチ式でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-137">The case identifiers are also used in pattern matching expressions.</span></span> <span data-ttu-id="0eab3-138">パターン マッチ式では、個別のケースに関連付けられる値に対して識別子が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-138">In a pattern matching expression, identifiers are provided for the values associated with the individual cases.</span></span> <span data-ttu-id="0eab3-139">たとえば、次のコードの `x` は、`Some` 型の `option` ケースと関連付けられた値が指定された識別子です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-139">For example, in the following code, `x` is the identifier given the value that is associated with the `Some` case of the `option` type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2002.fs)]

<span data-ttu-id="0eab3-140">パターン一致式では、名前付きフィールドを使用して判別共用体一致を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-140">In pattern matching expressions, you can use named fields to specify discriminated union matches.</span></span> <span data-ttu-id="0eab3-141">前に宣言された Shape 型には、次のコードに示すように、フィールドの値を抽出するために名前付きフィールドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-141">For the Shape type that was declared previously, you can use the named fields as the following code shows to extract the values of the fields.</span></span>

```fsharp
let getShapeHeight shape =
    match shape with
    | Rectangle(height = h) -> h
    | Circle(radius = r) -> 2. * r
    | Prism(height = h) -> h
```

<span data-ttu-id="0eab3-142">通常は、共用体の名前で、修飾せずにケース識別子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-142">Normally, the case identifiers can be used without qualifying them with the name of the union.</span></span> <span data-ttu-id="0eab3-143">常に、共用体の名前で修飾する名を使用する場合は、適用、 [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)属性を共用体の型定義。</span><span class="sxs-lookup"><span data-stu-id="0eab3-143">If you want the name to always be qualified with the name of the union, you can apply the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute to the union type definition.</span></span>

### <a name="unwrapping-discriminated-unions"></a><span data-ttu-id="0eab3-144">判別共用体のラップを解除</span><span class="sxs-lookup"><span data-stu-id="0eab3-144">Unwrapping Discriminated Unions</span></span>

<span data-ttu-id="0eab3-145">F# で判別共用体でよく使用されますドメイン モデリングを 1 つの型をラップします。</span><span class="sxs-lookup"><span data-stu-id="0eab3-145">In F# Discriminated Unions are often used in domain-modeling for wrapping a single type.</span></span> <span data-ttu-id="0eab3-146">パターン一致も使用して基になる値を抽出する簡単です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-146">It's easy to extract the underlying value via pattern matching as well.</span></span> <span data-ttu-id="0eab3-147">1 つのケースに一致する式を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0eab3-147">You don't need to use a match expression for a single case:</span></span>
```fsharp
let ([UnionCaseName] [values]) = [UnionValue]
```

<span data-ttu-id="0eab3-148">この動作を次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-148">The following example demonstrates this:</span></span>

```fsharp
type ShaderProgram = | ShaderProgram of id:int

let someMethodUsingShaderProgram shaderProgram =
    let (ShaderProgram id) = shaderProgram
    // Use the unwrapped value
    ..
```

## <a name="struct-discriminated-unions"></a><span data-ttu-id="0eab3-149">判別共用体の構造体</span><span class="sxs-lookup"><span data-stu-id="0eab3-149">Struct Discriminated Unions</span></span>

<span data-ttu-id="0eab3-150">4.1 以降では f#、構造体としての判別共用体も表すことができます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-150">Starting with F# 4.1, you can also represent Discriminated Unions as structs.</span></span>  <span data-ttu-id="0eab3-151">これは、`[<Struct>]`属性。</span><span class="sxs-lookup"><span data-stu-id="0eab3-151">This is done with the `[<Struct>]` attribute.</span></span>

```fsharp
[<Struct>]
type SingleCase = Case of string

[<Struct>]
type Multicase =
    | Case1 of string
    | Case2 of int
    | Case3 of double
```

<span data-ttu-id="0eab3-152">値の型は、これらの種類を参照しないため、ある余分な判別共用体の参照を持つ比較の考慮事項。</span><span class="sxs-lookup"><span data-stu-id="0eab3-152">Because these are value types and not reference types, there are extra considerations compared with reference discriminated unions:</span></span>

1. <span data-ttu-id="0eab3-153">これらは、値の型としてコピーされ、値型のセマンティクスを持ちます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-153">They are copied as value types and have value type semantics.</span></span>
2. <span data-ttu-id="0eab3-154">判別共用体 multicase 構造体を再帰的な種類の定義を使用できません。</span><span class="sxs-lookup"><span data-stu-id="0eab3-154">You cannot use a recursive type definition with a multicase struct Discriminated Union.</span></span>
3. <span data-ttu-id="0eab3-155">判別共用体の multicase 構造体のケース一意の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-155">You must provide unique case names for a multicase struct Discriminated Union.</span></span>

## <a name="using-discriminated-unions-instead-of-object-hierarchies"></a><span data-ttu-id="0eab3-156">オブジェクト階層ではなく、判別共用体を使用する場合</span><span class="sxs-lookup"><span data-stu-id="0eab3-156">Using Discriminated Unions Instead of Object Hierarchies</span></span>
<span data-ttu-id="0eab3-157">多くの場合、小さいオブジェクト階層をさらに簡単に表すために判別共用体を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-157">You can often use a discriminated union as a simpler alternative to a small object hierarchy.</span></span> <span data-ttu-id="0eab3-158">たとえば、円や正方形などの派生型を持つ `Shape` 基底クラスの代わりに、次の判別共用体を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-158">For example, the following discriminated union could be used instead of a `Shape` base class that has derived types for circle, square, and so on.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2003.fs)]

<span data-ttu-id="0eab3-159">オブジェクト指向の実装で使用される、面積や周を計算するための仮想メソッドの代わりに、パターン マッチを使用して、これらの量を計算するための適切な式に分岐できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-159">Instead of a virtual method to compute an area or perimeter, as you would use in an object-oriented implementation, you can use pattern matching to branch to appropriate formulas to compute these quantities.</span></span> <span data-ttu-id="0eab3-160">次の例では、図形に応じて、異なる数式を使用して面積を計算しています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-160">In the following example, different formulas are used to compute the area, depending on the shape.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2004.fs)]

<span data-ttu-id="0eab3-161">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0eab3-161">The output is as follows:</span></span>

```
Area of circle that has radius 15.000000: 706.858347
Area of square that has side 10.000000: 100.000000
Area of rectangle that has height 5.000000 and width 10.000000 is 50.000000
```

## <a name="using-discriminated-unions-for-tree-data-structures"></a><span data-ttu-id="0eab3-162">ツリー データ構造への判別共用体の使用</span><span class="sxs-lookup"><span data-stu-id="0eab3-162">Using Discriminated Unions for Tree Data Structures</span></span>
<span data-ttu-id="0eab3-163">判別共用体は再帰的に使用できます。つまり、共用体自体を 1 つ以上のケースの型に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-163">Discriminated unions can be recursive, meaning that the union itself can be included in the type of one or more cases.</span></span> <span data-ttu-id="0eab3-164">再帰的な判別共用体を使用してツリー構造を作成でき、このツリー構造をプログラミング言語での式のモデル化に使用できます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-164">Recursive discriminated unions can be used to create tree structures, which are used to model expressions in programming languages.</span></span> <span data-ttu-id="0eab3-165">次のコードでは、再帰的な判別共用体を使用して、バイナリ ツリーのデータ構造を作成しています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-165">In the following code, a recursive discriminated union is used to create a binary tree data structure.</span></span> <span data-ttu-id="0eab3-166">この共用体を構成する 2 つのケースは、整数値および左と右のサブツリーを持つノードである `Node` と、ツリーを終了する `Tip` です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-166">The union consists of two cases, `Node`, which is a node with an integer value and left and right subtrees, and `Tip`, which terminates the tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2005.fs)]

<span data-ttu-id="0eab3-167">このコードでは、`resultSumTree` の値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-167">In the previous code, `resultSumTree` has the value 10.</span></span> <span data-ttu-id="0eab3-168">次の図は、`myTree` のツリー構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-168">The following illustration shows the tree structure for `myTree`.</span></span>

![myTree のツリー構造](../media/TreeStructureDiagram.png)

<span data-ttu-id="0eab3-170">判別共用体は、ツリーのノードが異種の場合でも、問題なく機能します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-170">Discriminated unions work well if the nodes in the tree are heterogeneous.</span></span> <span data-ttu-id="0eab3-171">次のコードの `Expression` 型は、数と変数の加算と乗算をサポートする簡単なプログラミング言語での式の抽象構文ツリーを表します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-171">In the following code, the type `Expression` represents the abstract syntax tree of an expression in a simple programming language that supports addition and multiplication of numbers and variables.</span></span> <span data-ttu-id="0eab3-172">共用体の一部のケースは再帰的ではなく、数 (`Number`) または変数 (`Variable`) を表します。</span><span class="sxs-lookup"><span data-stu-id="0eab3-172">Some of the union cases are not recursive and represent either numbers (`Number`) or variables (`Variable`).</span></span> <span data-ttu-id="0eab3-173">他のケースは再帰的で、演算 (`Add` および `Multiply`) を表し、オペランドも式です。</span><span class="sxs-lookup"><span data-stu-id="0eab3-173">Other cases are recursive, and represent operations (`Add` and `Multiply`), where the operands are also expressions.</span></span> <span data-ttu-id="0eab3-174">`Evaluate` 関数では、match 式を使用して再帰的に構文ツリーを処理しています。</span><span class="sxs-lookup"><span data-stu-id="0eab3-174">The `Evaluate` function uses a match expression to recursively process the syntax tree.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2006.fs)]

<span data-ttu-id="0eab3-175">このコードを実行すると、`result` の値は 5 になります。</span><span class="sxs-lookup"><span data-stu-id="0eab3-175">When this code is executed, the value of `result` is 5.</span></span>

## <a name="common-attributes"></a><span data-ttu-id="0eab3-176">共通の属性</span><span class="sxs-lookup"><span data-stu-id="0eab3-176">Common Attributes</span></span>

<span data-ttu-id="0eab3-177">次の属性は、判別共用体でよく見られます。</span><span class="sxs-lookup"><span data-stu-id="0eab3-177">The following attributes are commonly seen in discriminated unions:</span></span>

* `[RequireQualifiedAccess]`
* `[NoEquality]`
* `[NoComparison]`
* <span data-ttu-id="0eab3-178">`[Struct]`(F# 4.1 以降)</span><span class="sxs-lookup"><span data-stu-id="0eab3-178">`[Struct]` (F# 4.1 and higher)</span></span>

## <a name="see-also"></a><span data-ttu-id="0eab3-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="0eab3-179">See Also</span></span>
[<span data-ttu-id="0eab3-180">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="0eab3-180">F# Language Reference</span></span>](index.md)
