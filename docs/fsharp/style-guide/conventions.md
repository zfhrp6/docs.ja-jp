---
title: F# でのコーディング規則
description: F# コードを記述する場合は、一般的なガイドラインと表現方法を説明します。
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457983"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="7f663-103">F# でのコーディング規則</span><span class="sxs-lookup"><span data-stu-id="7f663-103">F# coding conventions</span></span>

<span data-ttu-id="7f663-104">大規模な f# 使用経験から、次の規則が策定コードベースです。</span><span class="sxs-lookup"><span data-stu-id="7f663-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="7f663-105">[優れた f# コードの 5 つの原則](index.md#five-principles-of-good-f-code)各推奨事項の基盤となっています。</span><span class="sxs-lookup"><span data-stu-id="7f663-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="7f663-106">関連している、 [f# コンポーネントのデザイン ガイドライン](component-design-guidelines.md)、f#、コードだけでなくコンポーネント ライブラリなどの該当するが、します。</span><span class="sxs-lookup"><span data-stu-id="7f663-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="7f663-107">コードの整理</span><span class="sxs-lookup"><span data-stu-id="7f663-107">Organizing code</span></span>

<span data-ttu-id="7f663-108">F# コードを整理する主な方法は 2 つの機能: モジュールと名前空間。</span><span class="sxs-lookup"><span data-stu-id="7f663-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="7f663-109">次は似ていますが、次の相違点を持つ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7f663-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="7f663-110">名前空間は、.NET 名前空間としてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="7f663-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="7f663-111">モジュールは、静的クラスとしてコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7f663-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="7f663-112">名前空間は、常に最上位レベルです。</span><span class="sxs-lookup"><span data-stu-id="7f663-112">Namespaces are always top level.</span></span> <span data-ttu-id="7f663-113">モジュールは、最上位レベルとその他のモジュール内で入れ子にできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="7f663-114">名前空間は、複数のファイルにまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="7f663-115">モジュールことはできません。</span><span class="sxs-lookup"><span data-stu-id="7f663-115">Modules cannot.</span></span>
* <span data-ttu-id="7f663-116">モジュールは、使用する装飾できます`[<RequireQualifiedAccess>]`と`[<AutoOpen>]`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="7f663-117">次のガイドラインには、これらを使用してコードを整理するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7f663-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="7f663-118">最上位レベルの名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="7f663-119">コードについては、パブリックに使用できるように、名前空間は、最上位レベルのモジュールに優先します。</span><span class="sxs-lookup"><span data-stu-id="7f663-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="7f663-120">.NET 名前空間としてコンパイル、ため問題に c# から使用できるようにされません。</span><span class="sxs-lookup"><span data-stu-id="7f663-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="7f663-121">最上位レベルのモジュールを使用することがありますは表示されません、f# からのみ呼び出されるとは異なるが C# の場合、コンシューマーの呼び出し元を修飾することによって驚き可能性があります`MyClass`で、`MyCode`モジュール。</span><span class="sxs-lookup"><span data-stu-id="7f663-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="7f663-122">慎重に適用します。 `[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="7f663-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="7f663-123">`[<AutoOpen>]`コンストラクトを汚染は、呼び出し元に対して使用できるもののスコープと由来問題に対する回答が「マジック」です。</span><span class="sxs-lookup"><span data-stu-id="7f663-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="7f663-124">これは一般的に便利です。</span><span class="sxs-lookup"><span data-stu-id="7f663-124">This is generally not a good thing.</span></span> <span data-ttu-id="7f663-125">この規則の例外は、f# コア ライブラリ自体 (ただし、この事実も少し意見の分かれる)</span><span class="sxs-lookup"><span data-stu-id="7f663-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="7f663-126">ただし、パブリック API を整理するとは別にそのパブリック API からヘルパー機能を持っている場合、利便性を勧めします。</span><span class="sxs-lookup"><span data-stu-id="7f663-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...


    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="7f663-127">これにより、関数のパブリック API からクリーンに別の実装の詳細を完全修飾するヘルパー メソッドを呼び出すたびにしなくてもできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="7f663-128">さらに、拡張メソッドと名前空間レベルでの式ビルダーを公開する簡潔で表現`[<AutoOpen>]`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="7f663-129">使用して`[<RequireQualifiedAccess>]`するたびに名前が競合または読みやすさが容易になると思われる</span><span class="sxs-lookup"><span data-stu-id="7f663-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="7f663-130">追加する、`[<RequireQualifiedAccess>]`属性をモジュールにことを示し、モジュールが開かれていませんアクセスを修飾するモジュールの要素への参照が明示的に必要なことです。</span><span class="sxs-lookup"><span data-stu-id="7f663-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="7f663-131">たとえば、`Microsoft.FSharp.Collections.List`モジュールは、この属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="7f663-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="7f663-132">これは、機能は、関数と、モジュール内の値は、他のモジュールの名前と競合する可能性のある名前を持つ場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7f663-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="7f663-133">修飾のアクセスを必要とすると、長期的な保守容易性とライブラリの発展性が大幅に増やすできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="7f663-134">並べ替え`open`ステートメント位相的</span><span class="sxs-lookup"><span data-stu-id="7f663-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="7f663-135">F# で宣言の順序が重要な使用含む`open`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7f663-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="7f663-136">これとは異なり、C# の場合は、ここでの効果`using`と`using static`はファイルでこれらのステートメントの順序に依存しません。</span><span class="sxs-lookup"><span data-stu-id="7f663-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="7f663-137">F# では、スコープに開かれた要素は既に組み込まれている他のユーザーでシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="7f663-138">つまり、その並べ替え`open`コードの意味をステートメントが変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="7f663-139">その結果、すべての並べ替えは、任意`open`ステートメント (たとえば、英数字順) 通常は推奨されません、意図した動作の違いを生成するようにします。</span><span class="sxs-lookup"><span data-stu-id="7f663-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is generally not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="7f663-140">代わりに、ことをお勧めして並べ替えること[位相的](https://en.wikipedia.org/wiki/Topological_sorting); は、注文、`open`順序内のステートメント_レイヤー_定義は、システムのです。</span><span class="sxs-lookup"><span data-stu-id="7f663-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="7f663-141">英数字のトポロジの異なるレイヤー内での並べ替えを行うことがありますも見なされます。</span><span class="sxs-lookup"><span data-stu-id="7f663-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="7f663-142">たとえば、次に、f# コンパイラ サービス パブリック API ファイルのトポロジの並べ替えを示します。</span><span class="sxs-lookup"><span data-stu-id="7f663-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="7f663-143">改行が各レイヤーが後で並べ替えられる英数字順にトポロジのレイヤーを区切ることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="7f663-144">これは、クリーンに値を誤ってシャドウせずコードを整理します。</span><span class="sxs-lookup"><span data-stu-id="7f663-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="7f663-145">クラスを使用して、副作用がある値が含まれる</span><span class="sxs-lookup"><span data-stu-id="7f663-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="7f663-146">何度も値を初期化して、データベースまたはその他のリモート リソースにコンテキストをインスタンス化するなどの副作用を持つことができる場合。</span><span class="sxs-lookup"><span data-stu-id="7f663-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="7f663-147">などのモジュールを初期化し、後続の関数で使用しようとしがちです。</span><span class="sxs-lookup"><span data-stu-id="7f663-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="7f663-148">これをお勧め頻繁に不適切な理由はいくつかの。</span><span class="sxs-lookup"><span data-stu-id="7f663-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="7f663-149">コードベースでアプリケーションの構成をプッシュする最初に、`dep1`と`dep2`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="7f663-150">これは、大規模なコードベースで維持するが困難です。</span><span class="sxs-lookup"><span data-stu-id="7f663-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="7f663-151">第二に、静的に初期化されたデータは、自体のコンポーネントが複数のスレッドを使用する場合、スレッド セーフではない値を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="7f663-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="7f663-152">この違反が明確に`dep3`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="7f663-153">最後に、モジュールの初期化は、静的コンス トラクターに、全体のコンパイル単位をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7f663-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="7f663-154">場合は、そのモジュール内の let バインドされた値の初期化でエラーの発生が明らかに、`TypeInitializationException`アプリケーション全体の有効期間にわたってしキャッシュされました。</span><span class="sxs-lookup"><span data-stu-id="7f663-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="7f663-155">これは、診断が難しいことができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="7f663-156">通常は、内部例外については、理由を試みることができますが場合がない、根本原因を示しませんします。</span><span class="sxs-lookup"><span data-stu-id="7f663-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="7f663-157">代わりに、依存関係を保持するためにだけ、単純なクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="7f663-158">これにより、以下。</span><span class="sxs-lookup"><span data-stu-id="7f663-158">This enables the following:</span></span>

1. <span data-ttu-id="7f663-159">API 自体の外部依存の状態をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="7f663-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="7f663-160">API 外部で、構成を行うようになりましたことができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="7f663-161">従属変数の値の初期化でエラーとしてマニフェストを`TypeInitializationException`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="7f663-162">API では、簡単にテストできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7f663-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="7f663-163">エラー管理</span><span class="sxs-lookup"><span data-stu-id="7f663-163">Error management</span></span>

<span data-ttu-id="7f663-164">大規模なシステムでエラーの管理が複雑になり、微妙試み、シルバー、システムを確認するために行頭文字がフォールト トレラントし、適切に動作はありません。</span><span class="sxs-lookup"><span data-stu-id="7f663-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="7f663-165">次のガイドラインには、この困難な領域を移動するためのガイダンスを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="7f663-166">エラーの場合と、ドメインに組み込みの種類で無効な状態を表す</span><span class="sxs-lookup"><span data-stu-id="7f663-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="7f663-167">[判別共用体](../language-reference/discriminated-unions.md)、f# を使用する、できますを型システムの障害のあるプログラムの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="7f663-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="7f663-168">例えば:</span><span class="sxs-lookup"><span data-stu-id="7f663-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="7f663-169">この場合、これには銀行口座から資金を引き出しが失敗する可能性を 3 つの既知方法があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="7f663-170">各エラーの場合は、型で表され、対処できるようにため安全に、プログラム全体でします。</span><span class="sxs-lookup"><span data-stu-id="7f663-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="7f663-171">一般に、さまざまな方法をモデル化することができる場合に当たることができます**失敗**ドメイン内のエラー処理コードが不要になったとして扱われますものだけでなく正規プログラム フローを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="7f663-172">単に通常のプログラム フローの一部であるとは見なされません**例外的な**します。</span><span class="sxs-lookup"><span data-stu-id="7f663-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="7f663-173">この 2 つの主な利点があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="7f663-174">時間の経過と共に変更では、ドメインを管理しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="7f663-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="7f663-175">エラーの場合は、単体テストを容易にします。</span><span class="sxs-lookup"><span data-stu-id="7f663-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="7f663-176">エラーは、型で表すことができないときに例外を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="7f663-177">問題ドメインでは、すべてのエラーを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="7f663-178">これらのエラーは*例外的な*のため、本質的に発生させるし、f# の例外をキャッチする機能。</span><span class="sxs-lookup"><span data-stu-id="7f663-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="7f663-179">最初に、お勧めお読みになる、[例外のデザイン ガイドライン](../../standard/design-guidelines/exceptions.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f663-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="7f663-180">これらにも適用 f# です。</span><span class="sxs-lookup"><span data-stu-id="7f663-180">These are also applicable to F#.</span></span>

<span data-ttu-id="7f663-181">例外の発生の目的で f# で使用できる主な構成要素は、次の優先順位で検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="7f663-182">関数</span><span class="sxs-lookup"><span data-stu-id="7f663-182">Function</span></span> | <span data-ttu-id="7f663-183">構文</span><span class="sxs-lookup"><span data-stu-id="7f663-183">Syntax</span></span> | <span data-ttu-id="7f663-184">目的</span><span class="sxs-lookup"><span data-stu-id="7f663-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="7f663-185">発生させる、`System.ArgumentNullException`指定された引数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="7f663-186">発生させる、`System.ArgumentException`指定された引数名とメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="7f663-187">発生させます、`System.InvalidOperationException`指定したメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="7f663-188">例外をスローする汎用の機構です。</span><span class="sxs-lookup"><span data-stu-id="7f663-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="7f663-189">発生させます、`System.Exception`指定したメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="7f663-190">発生させる、`System.Exception`書式指定文字列とその入力によって決まりますメッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="7f663-191">使用して`nullArg`、`invalidArg`と`invalidOp`をスローするためのメカニズムとして`ArgumentNullException`、`ArgumentException`と`InvalidOperationException`適切な場合です。</span><span class="sxs-lookup"><span data-stu-id="7f663-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="7f663-192">`failwith`と`failwithf`関数一般的に使用しないで、ベースを起動するため`Exception`入力と、特定の例外ではありません。</span><span class="sxs-lookup"><span data-stu-id="7f663-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="7f663-193">1、[例外のデザイン ガイドライン](../../standard/design-guidelines/exceptions.md)、可能な場合より詳細な例外を発生させる場合します。</span><span class="sxs-lookup"><span data-stu-id="7f663-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="7f663-194">例外処理構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-194">Using exception-handling syntax</span></span>

<span data-ttu-id="7f663-195">F# を使用して例外パターンをサポートしています、`try...with`構文。</span><span class="sxs-lookup"><span data-stu-id="7f663-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="7f663-196">パターン マッチを使用して例外の発生時に実行する機能の調整はクリーンなコードを保持する場合は、少し難しいことができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="7f663-197">これに対処するこのような方法の 1 つを使用して[アクティブ パターン](../language-reference/active-patterns.md)例外自体でのエラー ケースを囲むグループ機能するための手段として。</span><span class="sxs-lookup"><span data-stu-id="7f663-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="7f663-198">たとえばは、例外をスローする場合は、例外のメタデータで有益な情報を囲むできる API が消費している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="7f663-199">アクティブ パターン内のキャプチャされた例外の本体で便利値へのアンラッピングをいくつかの状況で便利な値であることができますを返します。</span><span class="sxs-lookup"><span data-stu-id="7f663-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="7f663-200">Monadic のエラーに例外を置き換える処理を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7f663-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="7f663-201">例外は、関数型プログラミングで taboo 多少と見なされます。</span><span class="sxs-lookup"><span data-stu-id="7f663-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="7f663-202">実際には、ません機能を考慮しても安全であるために、例外は、純粋性に違反します。</span><span class="sxs-lookup"><span data-stu-id="7f663-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="7f663-203">ただし、コードが実行しなければならないとその実行時エラーが発生する可能性が実際には、これは無視されます。</span><span class="sxs-lookup"><span data-stu-id="7f663-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="7f663-204">一般に、ほとんどの目的が純粋なも望ましくないを最小限に抑えるには、合計でもないことを前提としてコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="7f663-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="7f663-205">ことが重要コア長所/の次の側面の例外に関して、関連性と、全体として、.NET ランタイムとクロス言語エコシステムで適切かどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="7f663-206">詳細な診断情報については、これは、問題をデバッグするときに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="7f663-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="7f663-207">ランタイムおよび他の .NET 言語で周知です。</span><span class="sxs-lookup"><span data-stu-id="7f663-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="7f663-208">重要な定型句の外に出るコードと比較して大幅に削減できます*回避*アドホックごとに、セマンティクスの一部のサブセットを実装することによって例外。</span><span class="sxs-lookup"><span data-stu-id="7f663-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="7f663-209">この 3 番目の点が重要です。</span><span class="sxs-lookup"><span data-stu-id="7f663-209">This third point is critical.</span></span> <span data-ttu-id="7f663-210">重要な複雑な操作、できなかった例外を使用すると、次のような構造を処理することがあります。</span><span class="sxs-lookup"><span data-stu-id="7f663-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="7f663-211">「Stringly に型指定された」エラー時に一致するパターンのような脆弱なコードが生じる可能性が簡単にします。</span><span class="sxs-lookup"><span data-stu-id="7f663-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="7f663-212">さらに、「より良い」の型を返す関数の「単純」desire で任意の例外を飲み込む動かさを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7f663-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="7f663-213">残念ながら、`tryReadAllText`無数のファイル システムで発生する可能性がある点に基づくさまざまな例外をスローすることができ、このコードを破棄されなくが実際にする起きて環境内で間違った情報。</span><span class="sxs-lookup"><span data-stu-id="7f663-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="7f663-214">結果型は、このコードに置き換えた場合して「stringly に型指定された」エラー メッセージの解析に。</span><span class="sxs-lookup"><span data-stu-id="7f663-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="7f663-215">例外オブジェクト自体を配置することで、`Error`コンス トラクターだけ強制的に、関数ではなく、呼び出しサイトでの例外の種類を正しく処理します。</span><span class="sxs-lookup"><span data-stu-id="7f663-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="7f663-216">これを効果的に行うには、API の呼び出し元として扱うに非常に楽しいものではない、チェックされた例外を作成します。</span><span class="sxs-lookup"><span data-stu-id="7f663-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="7f663-217">キャッチするには、上記の例の適切な代替手段は、*特定*例外およびその例外のコンテキストで意味のある値を返します。</span><span class="sxs-lookup"><span data-stu-id="7f663-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="7f663-218">変更する場合、`tryReadAllText`関数の次のように、`None`複数の意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="7f663-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="7f663-219">キャッチ オールとしてではなく、この関数は今すぐを正しく処理場合ファイルが見つからなかったし、その意味を戻り値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7f663-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="7f663-220">この戻り値は、任意のコンテキスト情報を破棄またはコードの時点で関連することができない可能性があるケースに対処する呼び出し元に強制しない中にそのエラーの場合にマップできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="7f663-221">などの型`Result<'Success, 'Error>`ここで、入れ子にしない、f# の省略可能な型はどちらの戻り値のものだった時を表す完全な基本的な操作に適した*もの*または*nothing*.</span><span class="sxs-lookup"><span data-stu-id="7f663-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="7f663-222">いない例外の代わりに、され必要がありますいないで使用しようとして例外を置換します。</span><span class="sxs-lookup"><span data-stu-id="7f663-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="7f663-223">代わりに、それらに適用してください慎重に行う例外とエラーの管理ポリシーの特定の側面をアドレス対象となるようにします。</span><span class="sxs-lookup"><span data-stu-id="7f663-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="7f663-224">一部のアプリケーションとプログラミングのポイントを必要としません。</span><span class="sxs-lookup"><span data-stu-id="7f663-224">Partial application and point-free programming</span></span>

<span data-ttu-id="7f663-225">F# ポイントを必要としないスタイルで一部のアプリケーションであるため、プログラムにさまざまな方法をサポートします。</span><span class="sxs-lookup"><span data-stu-id="7f663-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="7f663-226">モジュールまたは何かの実装内でコードを再利用と役に立つこのことができますが、一般的にはないものをパブリックに公開します。</span><span class="sxs-lookup"><span data-stu-id="7f663-226">This can be beneficial for code reuse within a module or the implementation of something, but it is generally not something to expose publicly.</span></span> <span data-ttu-id="7f663-227">一般に、ポイントを必要としないプログラミングは、それ自体の長所があり、いないスタイルに従事している人の重要な知的バリアを追加できます。</span><span class="sxs-lookup"><span data-stu-id="7f663-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="7f663-228">部分的に適用し、パブリック Api で、カリー化を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7f663-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="7f663-229">ほとんどの例外を除き、パブリック Api で一部のアプリケーションの使用はコンシューマーが混乱することはできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="7f663-230">通常、 `let`-f# コードでバインドされた値は**値**ではなく、**関数値**です。</span><span class="sxs-lookup"><span data-stu-id="7f663-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="7f663-231">値と関数の値を一緒に混在させることができますと引き換えに相当量の認知オーバーヘッドは、コードの行の数が少ないの保存などの演算子と組み合わされている場合に特に`>>`関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="7f663-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="7f663-232">ポイントを必要としないプログラミング ツールへの影響を検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="7f663-233">カリー化関数には、その引数はラベル付けしません。</span><span class="sxs-lookup"><span data-stu-id="7f663-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="7f663-234">ツールへの影響があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-234">This has tooling implications.</span></span> <span data-ttu-id="7f663-235">次の 2 つの関数を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="7f663-236">有効な関数は、これらはいずれもが`funcWithApplication`カリー化関数です。</span><span class="sxs-lookup"><span data-stu-id="7f663-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="7f663-237">エディターで、型、ポインターを合わせるときにこの参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="7f663-238">呼び出しサイトで Visual Studio などのツールでのヒントは与えないに関してどのような意味のある情報、`string`と`int`実際には入力の種類を表します。</span><span class="sxs-lookup"><span data-stu-id="7f663-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="7f663-239">ようなポイントを必要としないコードが発生した場合`funcWithApplication`パブリックに使用できるをお勧め完全 η 拡張させるために行うツールできますで引数にわかりやすい名前。</span><span class="sxs-lookup"><span data-stu-id="7f663-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="7f663-240">さらに、ポイントのないコードをデバッグできますが困難になる不可能です。</span><span class="sxs-lookup"><span data-stu-id="7f663-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="7f663-241">名前にバインドされている値に依存するデバッグ ツール (たとえば、`let`バインディング) を実行して中間値の中間にあるを検査することです。</span><span class="sxs-lookup"><span data-stu-id="7f663-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="7f663-242">コードには、検査する値がない、するものはありませんをデバッグします。</span><span class="sxs-lookup"><span data-stu-id="7f663-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="7f663-243">将来的には、デバッグ ツールを以前に実行されたパスに基づくこれらの値を合成する進化可能性がありますが、できません、上、おすすめコンテンツを hedge することをお勧め*潜在的な*機能をデバッグします。</span><span class="sxs-lookup"><span data-stu-id="7f663-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="7f663-244">内部の定型句を削減する手法として部分適用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="7f663-245">前のポイントとは対照的は、部分適用は、アプリケーションまたは API の詳細な内部構造の中で定型句を削減するためのすばらしいツールです。</span><span class="sxs-lookup"><span data-stu-id="7f663-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="7f663-246">これは、単体テストの定型句に対処する問題では多くの場合より複雑な Api の実装に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7f663-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="7f663-247">たとえばを実現する方法、次のコードに示すどのような最もモック フレームワークを提供このようなフレームワークの外部の依存関係を取得することがなくし API を bespoke 関連を学習します。</span><span class="sxs-lookup"><span data-stu-id="7f663-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="7f663-248">たとえば、次のソリューションのトポロジを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="7f663-249">`ImplementationLogic.fsproj` などのコードに公開する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="7f663-250">単体テスト`Transactions.doTransaction`で`ImplementationLogic.Tests.fspoj`は簡単。</span><span class="sxs-lookup"><span data-stu-id="7f663-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fspoj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="7f663-251">部分的に適用する`doTransaction`モック コンテキストにオブジェクトできますたびにモック コンテキストを構築する必要はありませんすべての単体テスト内の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7f663-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member __.TheFirstMember() = ...
        member __.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="7f663-252">この手法をユニバーサルに適用されません、全体のコードベースが、複雑な内部構造と単体テストのそれらの内部構造の定型句を削減することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7f663-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="7f663-253">アクセス制御</span><span class="sxs-lookup"><span data-stu-id="7f663-253">Access control</span></span>

<span data-ttu-id="7f663-254">F# は、複数のオプションの[アクセス制御](../language-reference/access-control.md).NET ランタイムで使用可能なから継承します。</span><span class="sxs-lookup"><span data-stu-id="7f663-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="7f663-255">これらは型に対してだけ使用可能ではありません - するその関数の場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="7f663-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="7f663-256">必要に応じて非`public`型とパブリックに使用できるようにすることが必要になるまでのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="7f663-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="7f663-257">これにどのようなコンシューマーのいくつか最小限に抑えられます</span><span class="sxs-lookup"><span data-stu-id="7f663-257">This also minimizes what consumers couple to</span></span>
* <span data-ttu-id="7f663-258">すべての機能をヘルパーのままにしておくこと`private`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="7f663-259">使用を検討`[<AutoOpen>]`多数になる場合、ヘルパー関数のプライベート モジュールにします。</span><span class="sxs-lookup"><span data-stu-id="7f663-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="7f663-260">型の推定とジェネリック</span><span class="sxs-lookup"><span data-stu-id="7f663-260">Type inference and generics</span></span>

<span data-ttu-id="7f663-261">型の推論では、多数の定型句を入力することから保存できます。</span><span class="sxs-lookup"><span data-stu-id="7f663-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="7f663-262">F# コンパイラで自動ジェネリック化を使用して、ユーザー側でほとんどない余分な労力より汎用的なコードを記述できるとします。</span><span class="sxs-lookup"><span data-stu-id="7f663-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="7f663-263">ただし、これらの機能は、汎用的なではありません。</span><span class="sxs-lookup"><span data-stu-id="7f663-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="7f663-264">明示的な型のパブリック Api で引数名のラベルを付けるし、この型の推定に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="7f663-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="7f663-265">この理由は**する**API では、コンパイラではないの形状のコントロールでする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="7f663-266">コンパイラは、の型の推論でジョブを正常に実行できることに依存している内部構造には、種類が変更された場合に、API の変更の形状を設定することです。</span><span class="sxs-lookup"><span data-stu-id="7f663-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="7f663-267">目的の動作がありますが、下流のコンシューマーが対処する重大な API の変更がほぼ確実に発生します。</span><span class="sxs-lookup"><span data-stu-id="7f663-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="7f663-268">代わりに、パブリック API の形状を明示的に制御する場合は、これらの重大な変更を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7f663-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="7f663-269">DDD 用語では、このことができますと見なす対策破損レイヤー。</span><span class="sxs-lookup"><span data-stu-id="7f663-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="7f663-270">ジェネリック引数をわかりやすい名前を付けることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="7f663-271">特定のドメインに固有ではない本当に汎用的なコードを記述していない場合にわかりやすい名前に作業中のドメインを理解する他のプログラマは役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7f663-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="7f663-272">という名前の型パラメーターなど、`'Document`ドキュメントとの対話のコンテキストでデータベースによりわかりやすく、関数またはメンバーを使用しているジェネリック ドキュメントの種類を受け入れることができません。</span><span class="sxs-lookup"><span data-stu-id="7f663-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="7f663-273">PascalCase でジェネリック型パラメーターの名前付けを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="7f663-274">これは、作業を行う .NET では、ため PascalCase ではなく snake_case またはキャメル ケースを使用することをお勧めの一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="7f663-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="7f663-275">最後に、自動ジェネリック化とは限りません f# または大規模なコードベースに追加された新しい方のため boon です。</span><span class="sxs-lookup"><span data-stu-id="7f663-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="7f663-276">一般的なコンポーネントを使用するのには、認知オーバーヘッドがあります。</span><span class="sxs-lookup"><span data-stu-id="7f663-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="7f663-277">さらに、自動的にでさまざまな入力の種類 (let だけの場合は、そのために使用する)、一般化された関数を使用しない場合がその時点でジェネリックする実際の利点はありません。</span><span class="sxs-lookup"><span data-stu-id="7f663-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="7f663-278">常にかどうかを記述するコードは実際には役に立つジェネリックを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="7f663-279">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="7f663-279">Performance</span></span>

<span data-ttu-id="7f663-280">F# の値では、既定では、特定のクラス (特に、関係する同時実行性と並列処理) のバグを回避することができますを変更できません。</span><span class="sxs-lookup"><span data-stu-id="7f663-280">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="7f663-281">ただし、場合によっては、実行時間やメモリの割り当ての最適な (またはでも適切な) の効率を実現するために作業の範囲可能性があります最適使用して実装の状態の変更は、インプレースです。</span><span class="sxs-lookup"><span data-stu-id="7f663-281">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="7f663-282">F# のオプトインごとに可能な限り、`mutable`キーワード。</span><span class="sxs-lookup"><span data-stu-id="7f663-282">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="7f663-283">ただし、使用の`mutable`f# で純粋性の機能に対応していない感じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-283">However, use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="7f663-284">純度からの期待を調整する場合は問題ありません。 これは[参照の透過性](https://en.wikipedia.org/wiki/Referential_transparency)です。</span><span class="sxs-lookup"><span data-stu-id="7f663-284">This is fine, if you adjust expectations from purity to [referential transparency](https://en.wikipedia.org/wiki/Referential_transparency).</span></span> <span data-ttu-id="7f663-285">参照の透過性のない純度 - が f# の関数を作成するときのエンド目標です。</span><span class="sxs-lookup"><span data-stu-id="7f663-285">Referential transparency - not purity - is the end goal when writing F# functions.</span></span> <span data-ttu-id="7f663-286">これにより、パフォーマンス クリティカル コードの変更ベースの実装に対して機能インターフェイスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-286">This allows you to write a functional interface over a mutation-based implementation for performance critical code.</span></span>

### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="7f663-287">変更可能なコードを変更できないインターフェイスでラップします。</span><span class="sxs-lookup"><span data-stu-id="7f663-287">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="7f663-288">目標として参照透過性は、パフォーマンスが重要な機能の変更可能な大打撃を公開しないコードを記述するが重要です。</span><span class="sxs-lookup"><span data-stu-id="7f663-288">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="7f663-289">たとえば、次のコードを実装して、 `Array.contains` f# コア ライブラリ内の関数。</span><span class="sxs-lookup"><span data-stu-id="7f663-289">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="7f663-290">この関数を複数回呼び出すことも、基になる配列が変更されません。 また、不要にそれを利用することで、変更可能な状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="7f663-290">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="7f663-291">コード内にほとんどすべての行が変異を使用している場合でもがしいものに透過的なです。</span><span class="sxs-lookup"><span data-stu-id="7f663-291">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="7f663-292">クラスの変更可能なデータをカプセル化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-292">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="7f663-293">前の例では、変更可能なデータを使用して操作をカプセル化するのに 1 つの関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-293">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="7f663-294">これは常により複雑なデータ セットのための十分なです。</span><span class="sxs-lookup"><span data-stu-id="7f663-294">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="7f663-295">次の関数のセットを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-295">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="7f663-296">このコードは、パフォーマンスおよびですが、呼び出し元の保守を担当している変異ベースのデータ構造を公開します。</span><span class="sxs-lookup"><span data-stu-id="7f663-296">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="7f663-297">これは、メンバーを持たない基になる変更可能なクラスの内部でラップすることができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-297">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member __.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member __.Count = t.Count

    member __.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="7f663-298">`Closure1Table` 基になるデータ構造を維持するために呼び出し元を強制しないため、基になる変異ベースのデータ構造をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="7f663-298">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="7f663-299">クラスは、データとは、呼び出し元に詳細情報を公開することがなく変異ベースのルーチンをカプセル化する強力な手段です。</span><span class="sxs-lookup"><span data-stu-id="7f663-299">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="7f663-300">必要に応じて`let mutable`セルを参照する</span><span class="sxs-lookup"><span data-stu-id="7f663-300">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="7f663-301">参照セルは、値そのものではなく、値への参照を表す方法です。</span><span class="sxs-lookup"><span data-stu-id="7f663-301">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="7f663-302">パフォーマンス クリティカルなコードを使用できますが、通常は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="7f663-302">Although they can be used for performance-critical code, they are generally not recommended.</span></span> <span data-ttu-id="7f663-303">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7f663-303">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="7f663-304">参照セルの使用は、逆参照し、基になるデータの再参照することですべての後続のコードを「汚染」です。</span><span class="sxs-lookup"><span data-stu-id="7f663-304">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="7f663-305">代わりに、 `let mutable`:</span><span class="sxs-lookup"><span data-stu-id="7f663-305">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="7f663-306">ラムダ式の中間で変異の 1 つのポイントとは別に他のすべてのコードを接して`acc`、通常の使用方法に違いはありません、同様の方法で行うことができます`let`-変更不可の値をバインドします。</span><span class="sxs-lookup"><span data-stu-id="7f663-306">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="7f663-307">これは、ため、時間の経過と共に変化しやすく、されます。</span><span class="sxs-lookup"><span data-stu-id="7f663-307">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="7f663-308">オブジェクトのプログラミング</span><span class="sxs-lookup"><span data-stu-id="7f663-308">Object programming</span></span>

<span data-ttu-id="7f663-309">F# は、オブジェクトおよびオブジェクト指向 (オブジェクト指向) の概念を完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="7f663-309">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="7f663-310">多くのオブジェクト指向の概念には、強力で便利ですが、それらのすべてを使用する場合に適してします。</span><span class="sxs-lookup"><span data-stu-id="7f663-310">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="7f663-311">次の一覧は、高レベルのオブジェクト指向機能のカテゴリに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="7f663-311">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="7f663-312">**多くの状況でこれらの機能の使用を検討してください。**</span><span class="sxs-lookup"><span data-stu-id="7f663-312">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="7f663-313">ドット付き表記 (`x.Length`)</span><span class="sxs-lookup"><span data-stu-id="7f663-313">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="7f663-314">インスタンス メンバー</span><span class="sxs-lookup"><span data-stu-id="7f663-314">Instance members</span></span>
* <span data-ttu-id="7f663-315">暗黙的なコンス トラクター</span><span class="sxs-lookup"><span data-stu-id="7f663-315">Implicit constructors</span></span>
* <span data-ttu-id="7f663-316">静的メンバー</span><span class="sxs-lookup"><span data-stu-id="7f663-316">Static members</span></span>
* <span data-ttu-id="7f663-317">インデクサー表記 (`arr.[x]`)</span><span class="sxs-lookup"><span data-stu-id="7f663-317">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="7f663-318">名前付きおよびオプションの引数</span><span class="sxs-lookup"><span data-stu-id="7f663-318">Named and Optional arguments</span></span>
* <span data-ttu-id="7f663-319">インターフェイスとインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="7f663-319">Interfaces and interface implementations</span></span>

<span data-ttu-id="7f663-320">**最初に、これらの機能に到達しないは慎重に適用して、問題を解決するは便利であるときに。**</span><span class="sxs-lookup"><span data-stu-id="7f663-320">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="7f663-321">メソッドのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="7f663-321">Method overloading</span></span>
* <span data-ttu-id="7f663-322">変更可能なデータをカプセル化</span><span class="sxs-lookup"><span data-stu-id="7f663-322">Encapsulated mutable data</span></span>
* <span data-ttu-id="7f663-323">型の演算子</span><span class="sxs-lookup"><span data-stu-id="7f663-323">Operators on types</span></span>
* <span data-ttu-id="7f663-324">自動プロパティ</span><span class="sxs-lookup"><span data-stu-id="7f663-324">Auto properties</span></span>
* <span data-ttu-id="7f663-325">実装する`IDisposable`と `IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="7f663-325">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="7f663-326">型の拡張機能</span><span class="sxs-lookup"><span data-stu-id="7f663-326">Type extensions</span></span>
* <span data-ttu-id="7f663-327">イベント</span><span class="sxs-lookup"><span data-stu-id="7f663-327">Events</span></span>
* <span data-ttu-id="7f663-328">構造体</span><span class="sxs-lookup"><span data-stu-id="7f663-328">Structs</span></span>
* <span data-ttu-id="7f663-329">デリゲート</span><span class="sxs-lookup"><span data-stu-id="7f663-329">Delegates</span></span>
* <span data-ttu-id="7f663-330">列挙体</span><span class="sxs-lookup"><span data-stu-id="7f663-330">Enums</span></span>

<span data-ttu-id="7f663-331">**一般的に使用する必要がありますしない限り、これらの機能を回避します。**</span><span class="sxs-lookup"><span data-stu-id="7f663-331">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="7f663-332">型の継承に基づいた階層と実装の継承</span><span class="sxs-lookup"><span data-stu-id="7f663-332">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="7f663-333">Null 値と `Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="7f663-333">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="7f663-334">コンポジションを継承よりも優先します。</span><span class="sxs-lookup"><span data-stu-id="7f663-334">Prefer composition over inheritance</span></span>

<span data-ttu-id="7f663-335">[継承の経過と共に変化](https://en.wikipedia.org/wiki/Composition_over_inheritance)は長年にわたる表現な f# コードが遵守することができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-335">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="7f663-336">基本的な原則ことする必要がありますいない基本クラスを公開し、強制的に呼び出し元が機能を実装する基本クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="7f663-336">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="7f663-337">クラスを必要としない場合は、インターフェイスを実装するオブジェクトの式を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f663-337">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="7f663-338">[オブジェクト式](../language-reference/object-expressions.md)クラスの内部でようにする必要はありません値に実装されたインターフェイスをバインドをその場でインターフェイスを実装することを許可します。</span><span class="sxs-lookup"><span data-stu-id="7f663-338">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="7f663-339">これは、便利な場合に特にする_のみ_インターフェイスを実装する完全クラスのない必要とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f663-339">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="7f663-340">たとえば、次のコードは内で実行される[Ionide](http://ionide.io/)にないシンボルを追加した場合は、コードの修正操作を提供する、`open`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="7f663-340">For example, here is the code that is run in [Ionide](http://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="7f663-341">Visual Studio コード API を扱うときに、クラスの必要はありません、ためオブジェクトの式は、この最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="7f663-341">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="7f663-342">単体テスト、暫定的な方法でテスト ルーチンを持つインターフェイスをスタブするときの重要なにもです。</span><span class="sxs-lookup"><span data-stu-id="7f663-342">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="type-abbreviations"></a><span data-ttu-id="7f663-343">型略称</span><span class="sxs-lookup"><span data-stu-id="7f663-343">Type Abbreviations</span></span>

<span data-ttu-id="7f663-344">[型略称](../language-reference/type-abbreviations.md)関数のシグネチャまたはより複雑な型などの別の型にラベルを割り当てるに便利です。</span><span class="sxs-lookup"><span data-stu-id="7f663-344">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="7f663-345">次のエイリアスがで計算を定義する必要な条件にラベルを割り当てますなど[CNTK](https://www.microsoft.com/cognitive-toolkit/)ライブラリを習得詳細。</span><span class="sxs-lookup"><span data-stu-id="7f663-345">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://www.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="7f663-346">`Computation`名がエイリアスがシグネチャと一致するすべての関数を表すために便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="7f663-346">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="7f663-347">型の省略形を使用して、次のようにして、便利より簡潔なコードできます。</span><span class="sxs-lookup"><span data-stu-id="7f663-347">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="7f663-348">ドメインを表す型の省略形は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7f663-348">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="7f663-349">型の省略形は便利な関数のシグネチャに、名前を付けることが、可能性がある混乱を招く場合、その他の種類の省略形です。</span><span class="sxs-lookup"><span data-stu-id="7f663-349">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="7f663-350">この省略形を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="7f663-350">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="7f663-351">複数の方法で混乱を招くことができます。</span><span class="sxs-lookup"><span data-stu-id="7f663-351">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="7f663-352">`BufferSize` 抽象化です。整数の単なる別の名前です。</span><span class="sxs-lookup"><span data-stu-id="7f663-352">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="7f663-353">場合`BufferSize`公開されるパブリック API で、簡単に解釈される可能性を単に意味`int`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-353">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="7f663-354">一般に、ドメインの種類に複数の属性を持ちなどのプリミティブ型ではない`int`です。</span><span class="sxs-lookup"><span data-stu-id="7f663-354">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="7f663-355">この省略形では、その仮定に違反します。</span><span class="sxs-lookup"><span data-stu-id="7f663-355">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="7f663-356">大文字と小文字`BufferSize`(PascalCase) は、この型がより多くのデータを保持していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="7f663-356">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="7f663-357">このエイリアスは、見やすく関数の名前付き引数を提供するのと比較を提供していません。</span><span class="sxs-lookup"><span data-stu-id="7f663-357">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="7f663-358">コンパイルされた IL; で、省略形が明らかにはこの別名は、コンパイル時の構造と同様の整数です。</span><span class="sxs-lookup"><span data-stu-id="7f663-358">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

<span data-ttu-id="7f663-359">要約すると、型の省略形の落とし穴ができる**いない**これらの省略形は、型を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="7f663-359">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="7f663-360">前の例では、`BufferSize`のみです、`int`は背後でない追加のデータや新機能だけでなく、型システムから利点`int`は既にです。</span><span class="sxs-lookup"><span data-stu-id="7f663-360">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>
