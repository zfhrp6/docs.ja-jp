---
title: F# コードのガイドラインを書式設定
description: F# コードを書式設定するためのガイドラインを説明します。
ms.date: 05/14/2018
ms.openlocfilehash: 6c8e4059fd4bf1e7450118a6df02609217c4f4db
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231510"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="68281-103">F# コードのガイドラインを書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-103">F# code formatting guidelines</span></span>

<span data-ttu-id="68281-104">この記事は、f# コードが実行されるように、コードを書式設定する方法のガイドラインを提供しています。</span><span class="sxs-lookup"><span data-stu-id="68281-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="68281-105">通常、読みやすくとして表示</span><span class="sxs-lookup"><span data-stu-id="68281-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="68281-106">Visual Studio のツールおよび他のエディターの書式設定によって適用される規則に従って、</span><span class="sxs-lookup"><span data-stu-id="68281-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="68281-107">その他のコードをオンラインに似ています</span><span class="sxs-lookup"><span data-stu-id="68281-107">Similar to other code online</span></span>

<span data-ttu-id="68281-108">これらのガイドラインに基づいています[f# の書式設定規則に包括的なガイド](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)によって[Anh 場を南 Phan](https://github.com/dungpa)です。</span><span class="sxs-lookup"><span data-stu-id="68281-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="68281-109">インデントの一般的な規則</span><span class="sxs-lookup"><span data-stu-id="68281-109">General rules for indentation</span></span>

<span data-ttu-id="68281-110">F# で既定では、重要なホワイト スペースを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-110">F# uses significant whitespace by default.</span></span> <span data-ttu-id="68281-111">次のガイドラインについては、これをかけることがいくつかの課題を使い分ける方法に関してガイダンスを提供するものです。</span><span class="sxs-lookup"><span data-stu-id="68281-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="68281-112">スペースを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-112">Using spaces</span></span>

<span data-ttu-id="68281-113">インデントが必要な場合は、スペース、タブではなくを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="68281-114">少なくとも 1 つの領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="68281-114">At least one space is required.</span></span> <span data-ttu-id="68281-115">組織がインデントに使用する空白文字の数を指定するコーディング規則を作成できます。インデントを設定する各レベルのインデントの 2 つ、3 つまたは 4 つのスペースが一般的です。</span><span class="sxs-lookup"><span data-stu-id="68281-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="68281-116">**インデントあたり 4 つのスペースはお勧めします。**</span><span class="sxs-lookup"><span data-stu-id="68281-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="68281-117">ただし、プログラムのインデントは主観的な問題。</span><span class="sxs-lookup"><span data-stu-id="68281-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="68281-118">バリエーションは、[ok] が最初の規則に従う必要がありますは*インデントの整合性*です。</span><span class="sxs-lookup"><span data-stu-id="68281-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="68281-119">一般的に受け入れられるインデントのスタイルを選択し、コードベース全体にわたって体系的に使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="68281-120">空白行を書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-120">Formatting blank lines</span></span>

* <span data-ttu-id="68281-121">独立した最上位関数やクラスの定義を 2 つの空白行でします。</span><span class="sxs-lookup"><span data-stu-id="68281-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="68281-122">クラスの内部でメソッドの定義は、単一の空白行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="68281-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="68281-123">余分な空白行は、関連する関数のグループを区切るための (慎重) に使用できます。</span><span class="sxs-lookup"><span data-stu-id="68281-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="68281-124">空白行は、一連の関連する困らせる (たとえば、一連のダミー実装) の間で省略可能です。</span><span class="sxs-lookup"><span data-stu-id="68281-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="68281-125">論理的なセクションを示すために、適度関数では、空白行を使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="68281-126">コメントの書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-126">Formatting comments</span></span>

<span data-ttu-id="68281-127">通常、ML スタイル ブロックのコメントを複数のダブル スラッシュ コメントを選びます。</span><span class="sxs-lookup"><span data-stu-id="68281-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="68281-128">インライン コメントは、最初の文字を大文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="68281-129">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="68281-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="68281-130">クラス バインド、式バインドおよびバインド パターンの値と関数のキャメル ケースを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="68281-131">すべての名前をキャメル ケースを使用する許容される f# スタイルには、ローカル変数として、またはにパターン マッチと関数定義がバインドされているし、共通です。</span><span class="sxs-lookup"><span data-stu-id="68281-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="68281-132">クラスのローカルにバインドされた関数は、キャメル ケースを使用してもする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="68281-133">モジュール バインド パブリック関数のキャメル ケースを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="68281-134">モジュール バインド関数が、パブリック API の一部では、キャメル ケースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="68281-135">内部およびプライベートのモジュール バインド値や関数のキャメル ケースを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="68281-136">キャメル ケースを使用して、プライベート モジュール バインド値を次のようにします。</span><span class="sxs-lookup"><span data-stu-id="68281-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="68281-137">スクリプトでアドホック関数</span><span class="sxs-lookup"><span data-stu-id="68281-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="68281-138">モジュールまたは型の内部実装を構成する値</span><span class="sxs-lookup"><span data-stu-id="68281-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="68281-139">パラメーターのキャメル ケースを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-139">Use camelCase for parameters</span></span>

<span data-ttu-id="68281-140">すべてのパラメーターは、.NET の名前付け規則に従ってキャメル ケースを使用してください。</span><span class="sxs-lookup"><span data-stu-id="68281-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="68281-141">PascalCase モジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-141">Use PascalCase for modules</span></span>

<span data-ttu-id="68281-142">(最上位レベル、内部、プライベート、入れ子になった) のすべてのモジュールは PascalCase を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="68281-143">型の宣言、メンバー、およびラベルの PascalCase を使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="68281-144">クラス、インターフェイス、構造体、列挙体、デリゲート、レコード、および判別共用体はすべての名前は PascalCase です。</span><span class="sxs-lookup"><span data-stu-id="68281-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="68281-145">型およびレコード、判別共用体のラベル内のメンバーは、PascalCase を使用してもする必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="68281-146">.NET の組み込みのコンス トラクターに対して PascalCase を使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="68281-147">名前空間、例外、イベント、およびプロジェクト/`.dll`名では、PascalCase も使用してください。</span><span class="sxs-lookup"><span data-stu-id="68281-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="68281-148">だけでなくこれにより、他の .NET 言語から消費にコンシューマーをより自然な感覚も発生する可能性が .NET の名前付け規則と一致します。</span><span class="sxs-lookup"><span data-stu-id="68281-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="68281-149">名前にアンダー スコアを回避します。</span><span class="sxs-lookup"><span data-stu-id="68281-149">Avoid underscores in names</span></span>

<span data-ttu-id="68281-150">従来、一部の f# ライブラリは、名前にアンダー スコアを使用するがします。</span><span class="sxs-lookup"><span data-stu-id="68281-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="68281-151">ただし、これが不要になった広く受け入れられて、.NET の名前付け規則と衝突するために一部です。</span><span class="sxs-lookup"><span data-stu-id="68281-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="68281-152">つまり、f# プログラマによってアンダー スコアを使用頻度の高い、および使用して部分的履歴上の理由から、許容範囲は、点が重要です。</span><span class="sxs-lookup"><span data-stu-id="68281-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="68281-153">ただし、スタイルが多くの場合、それを使用するかどうかを選択する他のユーザーによって我慢しなければならないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68281-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="68281-154">いくつかの例外には、アンダー スコアが非常に一般的であるネイティブなコンポーネントとの相互運用が含まれます。</span><span class="sxs-lookup"><span data-stu-id="68281-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="68281-155">標準の f# 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-155">Use standard F# operators</span></span>

<span data-ttu-id="68281-156">次の演算子は、f# の標準ライブラリで定義され、対応を定義する代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="68281-157">読みやすく理解し慣用コードを作成する傾向がありますが、これらの演算子を使用するをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="68281-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="68281-158">開発者向けの背景 OCaml またはその他の関数型プログラミング言語では、さまざまな表現方法に慣れて可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68281-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="68281-159">次の一覧は、推奨の f# 演算子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="68281-159">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="68281-160">ジェネリックのプレフィックスの構文を使用します (`Foo<T>`) 後置構文方が優先的 (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="68281-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="68281-161">F# でジェネリック型の名前付けの両方、後置 ML スタイルを継承 (など、 `int list`) プレフィックス .NET スタイルだけでなく (たとえば、 `list<int>`)。</span><span class="sxs-lookup"><span data-stu-id="68281-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="68281-162">4 つの特定の型を除く、.NET のスタイルを使用するには。</span><span class="sxs-lookup"><span data-stu-id="68281-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="68281-163">F# では、一覧の後置形式を使用して:`int list`なく`list<int>`です。</span><span class="sxs-lookup"><span data-stu-id="68281-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="68281-164">F# オプションは、後置形式を使用して:`int option`なく`option<int>`です。</span><span class="sxs-lookup"><span data-stu-id="68281-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="68281-165">F# の配列、構文の名前を使用`int[]`なく`int array`または`array<int>`です。</span><span class="sxs-lookup"><span data-stu-id="68281-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="68281-166">参照セルを使用して`int ref`なく`ref<int>`または`Ref<int>`です。</span><span class="sxs-lookup"><span data-stu-id="68281-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="68281-167">他のすべての種類では、前置形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="68281-168">共用体の宣言を判別する書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-168">Formatting discriminated union declarations</span></span>

<span data-ttu-id="68281-169">インデント`|`で 4 つのスペースの種類の定義。</span><span class="sxs-lookup"><span data-stu-id="68281-169">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

<span data-ttu-id="68281-170">インスタンス化された判別共用体に複数の行に分割するは、インデントの新しいスコープ含まれているデータを与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-170">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="68281-171">閉じかっこは、新しい行にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="68281-171">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a><span data-ttu-id="68281-172">組の書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-172">Formatting tuples</span></span>

<span data-ttu-id="68281-173">組のインスタンス化はかっこで囲まれた、する必要があり、区切るコンマ内で従う必要がありますを 1 つのスペースで例: `(1, 2)`、`(x, y, z)`です。</span><span class="sxs-lookup"><span data-stu-id="68281-173">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="68281-174">組のパターンに一致するでは、かっこを省略する場合は、一般に受け入れられた例外です。</span><span class="sxs-lookup"><span data-stu-id="68281-174">A commonly accepted exception is to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a><span data-ttu-id="68281-175">レコードを書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-175">Formatting records</span></span>

<span data-ttu-id="68281-176">短いレコードは、1 つの行に記述できます。</span><span class="sxs-lookup"><span data-stu-id="68281-176">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="68281-177">長いレコードは、ラベルの新しい行を使用してください。</span><span class="sxs-lookup"><span data-stu-id="68281-177">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="68281-178">開始トークンを配置する、同じ行で、新しい行の終わりトークンも問題ありません。</span><span class="sxs-lookup"><span data-stu-id="68281-178">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
    Boss1 = "Jeffrey"
    Boss2 = "Jeffrey"
    Boss3 = "Jeffrey"
    Boss4 = "Jeffrey"
    Boss5 = "Jeffrey"
    Boss6 = "Jeffrey"
    Boss7 = "Jeffrey"
    Boss8 = "Jeffrey"
    Lackeys = ["Zippy"; "George"; "Bungle"]
}
```

<span data-ttu-id="68281-179">リストと配列の要素の場合と同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="68281-179">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="68281-180">書式設定のリストと配列</span><span class="sxs-lookup"><span data-stu-id="68281-180">Formatting lists and arrays</span></span>

<span data-ttu-id="68281-181">書き込む`x :: l`前後に空白、`::`演算子 (`::`スペースで囲まれたため、挿入演算子は、) と`[1; 2; 3]`(`;`のため後にスペースを区切り記号である)。</span><span class="sxs-lookup"><span data-stu-id="68281-181">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="68281-182">常に 2 つの個別の中かっこのような演算子の間に少なくとも 1 つの領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-182">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="68281-183">たとえば、間に空白のままにして、`[`と`{`です。</span><span class="sxs-lookup"><span data-stu-id="68281-183">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="68281-184">リストと複数行にわたって配列は、レコードと同様のルールを従います。</span><span class="sxs-lookup"><span data-stu-id="68281-184">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="68281-185">書式設定の if 式</span><span class="sxs-lookup"><span data-stu-id="68281-185">Formatting if expressions</span></span>

<span data-ttu-id="68281-186">条件のインデントは、それらを構成する式のサイズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="68281-186">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="68281-187">場合`cond`、`e1`と`e2`は小さく、単にそれを 1 つの行に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="68281-187">If `cond`, `e1` and `e2` are small, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="68281-188">場合`e1`と`cond`は、小さなが`e2`大き。</span><span class="sxs-lookup"><span data-stu-id="68281-188">If `e1` and `cond` are small, but `e2` is large:</span></span>

```fsharp
if cond then e1
else
    e2
```

<span data-ttu-id="68281-189">場合`e1`と`cond`が大きいと`e2`小さ。</span><span class="sxs-lookup"><span data-stu-id="68281-189">If `e1` and `cond` are large and `e2` is small:</span></span>

```fsharp
if cond then
    e1
else e2
```

<span data-ttu-id="68281-190">すべての式が大きい場合は。</span><span class="sxs-lookup"><span data-stu-id="68281-190">If all the expressions are large:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="68281-191">複数の条件で`elif`と`else`と同じスコープでインデント、 `if`:</span><span class="sxs-lookup"><span data-stu-id="68281-191">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="68281-192">パターン マッチング</span><span class="sxs-lookup"><span data-stu-id="68281-192">Pattern matching constructs</span></span>

<span data-ttu-id="68281-193">使用して、`|`インデントなしで、一致した文字列の各句。</span><span class="sxs-lookup"><span data-stu-id="68281-193">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="68281-194">式が短い場合は、各部分式が単純な場合は 1 行の使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="68281-194">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="68281-195">パターン マッチングの矢印の右の式が大きすぎる場合、次の行のインデントを設定した 1 つのステップに移動、 `match` /`|`です。</span><span class="sxs-lookup"><span data-stu-id="68281-195">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="68281-196">パターン マッチにより、開始、匿名の関数の`function`は、通常はインデントされません離れすぎています。</span><span class="sxs-lookup"><span data-stu-id="68281-196">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="68281-197">たとえば、次のように 1 つのスコープをインデントも可能です。</span><span class="sxs-lookup"><span data-stu-id="68281-197">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="68281-198">パターン マッチで定義されている関数で`let`または`let rec`の開始後にインデントされた 4 つのスペースをする必要があります`let`場合でも、`function`キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="68281-198">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="68281-199">矢印の配置はお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="68281-199">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="68281-200">書式設定やり直して/式</span><span class="sxs-lookup"><span data-stu-id="68281-200">Formatting try/with expressions</span></span>

<span data-ttu-id="68281-201">例外の種類で一致するパターンと同じレベルにインデントする`with`です。</span><span class="sxs-lookup"><span data-stu-id="68281-201">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="68281-202">関数パラメーターのアプリケーションを書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-202">Formatting function parameter application</span></span>

<span data-ttu-id="68281-203">一般に、関数パラメーターのほとんどのアプリケーションは、同じ行に行われます。</span><span class="sxs-lookup"><span data-stu-id="68281-203">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="68281-204">新しい行に関数にパラメーターを適用する場合は、1 つのスコープでインデントします。</span><span class="sxs-lookup"><span data-stu-id="68281-204">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="68281-205">同じガイドラインは、関数の引数としてラムダ式の適用されます。</span><span class="sxs-lookup"><span data-stu-id="68281-205">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="68281-206">ラムダ式の本体の本文には、別の行が持つ、1 つのスコープでインデント</span><span class="sxs-lookup"><span data-stu-id="68281-206">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="68281-207">ただし、ラムダ式の本体が 1 つ以上の行の場合は、別の関数にファクタリング アウトを検討してくださいではなく、単一の引数として関数に適用される複数行コンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="68281-207">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="68281-208">挿入演算子を書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-208">Formatting infix operators</span></span>

<span data-ttu-id="68281-209">スペースで別の演算子。</span><span class="sxs-lookup"><span data-stu-id="68281-209">Separate operators by spaces.</span></span> <span data-ttu-id="68281-210">このルールの明確な例外は、`!`と`.`演算子。</span><span class="sxs-lookup"><span data-stu-id="68281-210">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="68281-211">挿入辞式では、[ok] を同じ列に編成します。</span><span class="sxs-lookup"><span data-stu-id="68281-211">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="68281-212">パイプライン演算子を書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-212">Formatting pipeline operators</span></span>

<span data-ttu-id="68281-213">パイプライン`|>`演算子は、上で動作する式の下に移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68281-213">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="68281-214">モジュールの書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-214">Formatting modules</span></span>

<span data-ttu-id="68281-215">モジュールを基準としたローカル モジュール内のコードのインデントを設定する必要がありますが、最上位レベルのモジュール内のコードにインデントする必要がありますされません。</span><span class="sxs-lookup"><span data-stu-id="68281-215">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="68281-216">Namespace 要素は、インデントする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="68281-216">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="68281-217">オブジェクトの式とインターフェイスの書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-217">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="68281-218">同じ方法では、オブジェクトの式とインターフェイスを揃える必要があります`member`4 つのスペースの後にインデントします。</span><span class="sxs-lookup"><span data-stu-id="68281-218">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a><span data-ttu-id="68281-219">式内の空白文字の書式設定</span><span class="sxs-lookup"><span data-stu-id="68281-219">Formatting whitespace in expressions</span></span>

<span data-ttu-id="68281-220">F# の式内の余分な空白文字を避けてください。</span><span class="sxs-lookup"><span data-stu-id="68281-220">Avoid extraneous whitespace in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="68281-221">名前付き引数もない領域を囲む、 `=`:</span><span class="sxs-lookup"><span data-stu-id="68281-221">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
