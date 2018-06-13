---
title: コンピュテーション式 (F#)
description: F# でシーケンス処理することができ、制御フローの構成要素とバインディングを使用して結合する計算を作成するための便利な構文を作成する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: a4ddb3fde284452bc901c5270551611e43742c1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566614"
---
# <a name="computation-expressions"></a><span data-ttu-id="99fae-103">コンピュテーション式</span><span class="sxs-lookup"><span data-stu-id="99fae-103">Computation Expressions</span></span>

<span data-ttu-id="99fae-104">F# コンピュテーション式は、シーケンス処理することができ、制御フローの構成要素とバインディングを使用して結合する計算を作成するための便利な構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="99fae-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="99fae-105">便利な構文を提供する使えます*モナド*、高度なプログラミング機能データ、制御、および機能のプログラムでの副作用を管理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="99fae-105">They can be used to provide a convenient syntax for *monads*, a functional programming feature that can be used to manage data, control, and side effects in functional programs.</span></span>


## <a name="built-in-workflows"></a><span data-ttu-id="99fae-106">組み込みのワークフロー</span><span class="sxs-lookup"><span data-stu-id="99fae-106">Built-in Workflows</span></span>
<span data-ttu-id="99fae-107">シーケンス式では、非同期ワークフローおよびクエリ式とコンピュテーション式の例があります。</span><span class="sxs-lookup"><span data-stu-id="99fae-107">Sequence expressions are an example of a computation expression, as are asynchronous workflows and query expressions.</span></span> <span data-ttu-id="99fae-108">詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[クエリ式](query-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="99fae-108">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

<span data-ttu-id="99fae-109">特定の機能は、シーケンス式と非同期のワークフローの両方に共通して、コンピュテーション式の基本構文を示しています。</span><span class="sxs-lookup"><span data-stu-id="99fae-109">Certain features are common to both sequence expressions and asynchronous workflows and illustrate the basic syntax for a computation expression:</span></span>

```fsharp
builder-name { expression }
```

<span data-ttu-id="99fae-110">前の構文では、指定された式がで指定された型の計算式であるを指定します*ビルダー名前*です。</span><span class="sxs-lookup"><span data-stu-id="99fae-110">The previous syntax specifies that the given expression is a computation expression of a type specified by *builder-name*.</span></span> <span data-ttu-id="99fae-111">コンピュテーション式では、組み込みのワークフローをなどで`seq`または`async`、かを定義するものであることができます。</span><span class="sxs-lookup"><span data-stu-id="99fae-111">The computation expression can be a built-in workflow, such as `seq` or `async`, or it can be something you define.</span></span> <span data-ttu-id="99fae-112">*ビルダー名前*と呼ばれる特殊な種類のインスタンスの識別子を指定、*ビルダー型*です。</span><span class="sxs-lookup"><span data-stu-id="99fae-112">The *builder-name* is the identifier for an instance of a special type known as the *builder type*.</span></span> <span data-ttu-id="99fae-113">ビルダーの型は、式の実行方法を制御するコンピュテーション式のフラグメントを結合する方法、つまり、コードを制御する特殊なメソッドを定義するクラス型です。</span><span class="sxs-lookup"><span data-stu-id="99fae-113">The builder type is a class type that defines special methods that govern the way the fragments of the computation expression are combined, that is, code that controls how the expression executes.</span></span> <span data-ttu-id="99fae-114">ビルダー クラスを説明する別の方法では、多く f# の構成要素、ループのバインドなどの操作をカスタマイズできる言うです。</span><span class="sxs-lookup"><span data-stu-id="99fae-114">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

<span data-ttu-id="99fae-115">コンピュテーション式、2 つの形式がいくつかの一般的な言語構成要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="99fae-115">In computation expressions, two forms are available for some common language constructs.</span></span> <span data-ttu-id="99fae-116">使用して、バリアント型のコンス トラクターを呼び出すことができます、!</span><span class="sxs-lookup"><span data-stu-id="99fae-116">You can invoke the variant constructs by using a !</span></span> <span data-ttu-id="99fae-117">(感嘆符) など、特定のキーワードでサフィックス`let!`、`do!`のようにします。</span><span class="sxs-lookup"><span data-stu-id="99fae-117">(bang) suffix on certain keywords, such as `let!`, `do!`, and so on.</span></span> <span data-ttu-id="99fae-118">これらの特殊な形式は、これらの操作の通常の組み込みのビヘイビアーを置換するビルダー クラスで定義されている特定の機能をによりします。</span><span class="sxs-lookup"><span data-stu-id="99fae-118">These special forms cause certain functions defined in the builder class to replace the ordinary built-in behavior of these operations.</span></span> <span data-ttu-id="99fae-119">これらのフォームのように、`yield!`形式の`yield`シーケンス式で使用されるキーワード。</span><span class="sxs-lookup"><span data-stu-id="99fae-119">These forms resemble the `yield!` form of the `yield` keyword that is used in sequence expressions.</span></span> <span data-ttu-id="99fae-120">詳細については、次を参照してください。[シーケンス](sequences.md)です。</span><span class="sxs-lookup"><span data-stu-id="99fae-120">For more information, see [Sequences](sequences.md).</span></span>


## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="99fae-121">コンピュテーション式の新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="99fae-121">Creating a New Type of Computation Expression</span></span>
<span data-ttu-id="99fae-122">ビルダー クラスを作成し、クラスの特定の特殊なメソッドを定義することは、独自の計算式の特性を定義できます。</span><span class="sxs-lookup"><span data-stu-id="99fae-122">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="99fae-123">ビルダー クラスは、次の表に記載されているメソッドをオプションで定義できます。</span><span class="sxs-lookup"><span data-stu-id="99fae-123">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="99fae-124">次の表では、ワークフロー ビルダー クラスで使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="99fae-124">The following table describes methods that can be used in a workflow builder class.</span></span>


|<span data-ttu-id="99fae-125">**メソッド**</span><span class="sxs-lookup"><span data-stu-id="99fae-125">**Method**</span></span>|<span data-ttu-id="99fae-126">**通常のシグネチャ**</span><span class="sxs-lookup"><span data-stu-id="99fae-126">**Typical signature(s)**</span></span>|<span data-ttu-id="99fae-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="99fae-127">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="99fae-128">に対して呼び出さ`let!`と`do!`コンピュテーション式でします。</span><span class="sxs-lookup"><span data-stu-id="99fae-128">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="99fae-129">関数として計算式をラップします。</span><span class="sxs-lookup"><span data-stu-id="99fae-129">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="99fae-130">に対して呼び出さ`return`コンピュテーション式でします。</span><span class="sxs-lookup"><span data-stu-id="99fae-130">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="99fae-131">に対して呼び出さ`return!`コンピュテーション式でします。</span><span class="sxs-lookup"><span data-stu-id="99fae-131">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="99fae-132">`M<'T> -> M<'T>` または</span><span class="sxs-lookup"><span data-stu-id="99fae-132">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="99fae-133">コンピュテーション式を実行します。</span><span class="sxs-lookup"><span data-stu-id="99fae-133">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="99fae-134">`M<'T> * M<'T> -> M<'T>` または</span><span class="sxs-lookup"><span data-stu-id="99fae-134">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="99fae-135">コンピュテーション式のシーケンスに対して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="99fae-135">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="99fae-136">`seq<'T> * ('T -> M<'U>) -> M<'U>` または</span><span class="sxs-lookup"><span data-stu-id="99fae-136">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="99fae-137">に対して呼び出さ`for...do`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-137">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="99fae-138">に対して呼び出さ`try...finally`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-138">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="99fae-139">に対して呼び出さ`try...with`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-139">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="99fae-140">に対して呼び出さ`use`コンピュテーション式内のバインディングです。</span><span class="sxs-lookup"><span data-stu-id="99fae-140">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="99fae-141">に対して呼び出さ`while...do`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-141">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="99fae-142">に対して呼び出さ`yield`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-142">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="99fae-143">に対して呼び出さ`yield!`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-143">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="99fae-144">空のと呼ばれる`else`の分岐`if...then`コンピュテーション式内の式。</span><span class="sxs-lookup"><span data-stu-id="99fae-144">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
<span data-ttu-id="99fae-145">使用し、返しますビルダー クラスでメソッドの多くは、`M<'T>`コンス トラクターは、結合された計算の種類を表すとは別に定義された型は、通常、`Async<'T>`ための非同期ワークフローおよび`Seq<'T>`ワークフローのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="99fae-145">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="99fae-146">これらのメソッドのシグネチャは、1 つの構築から返されるワークフロー オブジェクトは、次に渡すことができるようにそれらを結合し、互いに入れ子になった有効にします。</span><span class="sxs-lookup"><span data-stu-id="99fae-146">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="99fae-147">コンピュテーション式を解析する場合、コンパイラは、前の表に、メソッドとそのコンピュテーション式内のコードを使用して、一連の入れ子になった関数呼び出しに式を変換します。</span><span class="sxs-lookup"><span data-stu-id="99fae-147">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="99fae-148">入れ子になった式は、次の形式です。</span><span class="sxs-lookup"><span data-stu-id="99fae-148">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="99fae-149">上記のコードへの呼び出しで`Run`と`Delay`コンピュテーション式ビルダー クラスで定義されていない場合は省略します。</span><span class="sxs-lookup"><span data-stu-id="99fae-149">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="99fae-150">としてここに示される、コンピュテーション式の本体`{| cexpr |}`は、次の表で説明の翻訳でビルダー クラスのメソッドに関連する呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="99fae-150">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="99fae-151">コンピュテーション式`{| cexpr |}`に従ってこれらの変換を再帰的に定義されているは、 `expr` f# の式と`cexpr`コンピュテーション式です。</span><span class="sxs-lookup"><span data-stu-id="99fae-151">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>



|<span data-ttu-id="99fae-152">正規表現</span><span class="sxs-lookup"><span data-stu-id="99fae-152">Expression</span></span>|<span data-ttu-id="99fae-153">変換</span><span class="sxs-lookup"><span data-stu-id="99fae-153">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="99fae-154">前の表に`other-expr`それ以外の場合、表に一覧表示されていない式を記述します。</span><span class="sxs-lookup"><span data-stu-id="99fae-154">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="99fae-155">ビルダー クラスは、前の表に、翻訳をすべてサポートしているすべてのメソッドを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="99fae-155">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="99fae-156">実装されていないこれらのコンストラクトでは、その型の計算式で使用できません。</span><span class="sxs-lookup"><span data-stu-id="99fae-156">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="99fae-157">たとえば、サポートしない場合、 `use` 、コンピュテーション式のキーワードの定義を省略することができます`Use`ビルダー クラスにします。</span><span class="sxs-lookup"><span data-stu-id="99fae-157">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="99fae-158">次のコード例では、一連の手順を実行することができる、一度に 1 つのステップを評価する計算をカプセル化する計算式を示します。</span><span class="sxs-lookup"><span data-stu-id="99fae-158">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="99fae-159">A 判別共用体型、 `OkOrException`、これまでに評価された式のエラー状態をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="99fae-159">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="99fae-160">このコードでは、ビルダー メソッドのいくつかの定型実装など、コンピュテーション式で使用できるいくつかの一般的なパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="99fae-160">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this 
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="99fae-161">コンピュテーション式が、式から返される、基になる型です。</span><span class="sxs-lookup"><span data-stu-id="99fae-161">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="99fae-162">計算の結果または遅延の計算を実行できる、基になる型を表すことがありますか、それに何らかの種類のコレクションを反復処理手段を提供することがあります。</span><span class="sxs-lookup"><span data-stu-id="99fae-162">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="99fae-163">前の例では、基になる型は**最終的に**です。</span><span class="sxs-lookup"><span data-stu-id="99fae-163">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="99fae-164">シーケンス式では、基になる型は<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>します。</span><span class="sxs-lookup"><span data-stu-id="99fae-164">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99fae-165">クエリ式では、基になる型は<xref:System.Linq.IQueryable?displayProperty=nameWithType>します。</span><span class="sxs-lookup"><span data-stu-id="99fae-165">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="99fae-166">非同期ワークフローでは、基になる型は[ `Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)です。</span><span class="sxs-lookup"><span data-stu-id="99fae-166">For an asychronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="99fae-167">`Async`オブジェクトは結果を計算するために実行する作業を表します。</span><span class="sxs-lookup"><span data-stu-id="99fae-167">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="99fae-168">たとえば、呼び出す[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)計算を実行し、結果を返すにします。</span><span class="sxs-lookup"><span data-stu-id="99fae-168">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="99fae-169">カスタム操作</span><span class="sxs-lookup"><span data-stu-id="99fae-169">Custom Operations</span></span>
<span data-ttu-id="99fae-170">コンピュテーション式のカスタム処理を定義し、コンピュテーション式では演算子として、カスタム操作を使用できます。</span><span class="sxs-lookup"><span data-stu-id="99fae-170">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="99fae-171">たとえば、クエリ式ではクエリ演算子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="99fae-171">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="99fae-172">カスタムの操作を定義するときは、結果を定義する必要がありますとコンピュテーション式内のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="99fae-172">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="99fae-173">カスタム操作を定義するのには、コンピュテーション式のビルダー クラスに配置し、適用、 [ `CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)です。</span><span class="sxs-lookup"><span data-stu-id="99fae-173">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="99fae-174">この属性は、これは、カスタム操作で使用する名前、引数として文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="99fae-174">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="99fae-175">この名前は、スコープ コンピュテーション式の始め中かっこの開始時に渡されます。</span><span class="sxs-lookup"><span data-stu-id="99fae-175">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="99fae-176">そのため、このブロックで、カスタム操作と同じ名前のある識別子を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="99fae-176">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="99fae-177">たとえばなどの識別子の使用を回避`all`または`last`クエリ式でします。</span><span class="sxs-lookup"><span data-stu-id="99fae-177">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

## <a name="see-also"></a><span data-ttu-id="99fae-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="99fae-178">See Also</span></span>
[<span data-ttu-id="99fae-179">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="99fae-179">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="99fae-180">非同期ワークフロー</span><span class="sxs-lookup"><span data-stu-id="99fae-180">Asynchronous Workflows</span></span>](asynchronous-workflows.md)

[<span data-ttu-id="99fae-181">シーケンス</span><span class="sxs-lookup"><span data-stu-id="99fae-181">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[<span data-ttu-id="99fae-182">クエリ式</span><span class="sxs-lookup"><span data-stu-id="99fae-182">Query Expressions</span></span>](query-expressions.md)
