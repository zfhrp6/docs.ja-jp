---
title: "コンピュテーション式 (F#)"
description: "F# でシーケンス処理することができ、制御フローの構成要素とバインディングを使用して結合する計算を作成するための便利な構文を作成する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: acabbf5d-fbb8-479f-894c-7251bf16c8c3
ms.openlocfilehash: 15ba2e167efc1d295d81439dcf85bc7272e05265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="computation-expressions"></a>コンピュテーション式

F# コンピュテーション式は、シーケンス処理することができ、制御フローの構成要素とバインディングを使用して結合する計算を作成するための便利な構文を提供します。 便利な構文を提供する使えます*モナド*、高度なプログラミング機能データ、制御、および機能のプログラムでの副作用を管理するために使用できます。


## <a name="built-in-workflows"></a>組み込みのワークフロー
シーケンス式では、非同期ワークフローおよびクエリ式とコンピュテーション式の例があります。 詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[クエリ式](query-expressions.md)です。

特定の機能は、シーケンス式と非同期のワークフローの両方に共通して、コンピュテーション式の基本構文を示しています。

```fsharp
builder-name { expression }
```

前の構文では、指定された式がで指定された型の計算式であるを指定します*ビルダー名前*です。 コンピュテーション式では、組み込みのワークフローをなどで`seq`または`async`、かを定義するものであることができます。 *ビルダー名前*と呼ばれる特殊な種類のインスタンスの識別子を指定、*ビルダー型*です。 ビルダーの型は、式の実行方法を制御するコンピュテーション式のフラグメントを結合する方法、つまり、コードを制御する特殊なメソッドを定義するクラス型です。 ビルダー クラスを説明する別の方法では、多く f# の構成要素、ループのバインドなどの操作をカスタマイズできる言うです。

コンピュテーション式、2 つの形式がいくつかの一般的な言語構成要素を使用できます。 使用して、バリアント型のコンス トラクターを呼び出すことができます、! (感嘆符) など、特定のキーワードでサフィックス`let!`、`do!`のようにします。 これらの特殊な形式は、これらの操作の通常の組み込みのビヘイビアーを置換するビルダー クラスで定義されている特定の機能をによりします。 これらのフォームのように、`yield!`形式の`yield`シーケンス式で使用されるキーワード。 詳細については、次を参照してください。[シーケンス](sequences.md)です。


## <a name="creating-a-new-type-of-computation-expression"></a>コンピュテーション式の新しい型を作成します。
ビルダー クラスを作成し、クラスの特定の特殊なメソッドを定義することは、独自の計算式の特性を定義できます。 ビルダー クラスは、次の表に記載されているメソッドをオプションで定義できます。

次の表では、ワークフロー ビルダー クラスで使用できるメソッドについて説明します。


|**メソッド**|**通常のシグネチャ**|**説明**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|に対して呼び出さ`let!`と`do!`コンピュテーション式でします。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|関数として計算式をラップします。|
|`Return`|`'T -> M<'T>`|に対して呼び出さ`return`コンピュテーション式でします。|
|`ReturnFrom`|`M<'T> -> M<'T>`|に対して呼び出さ`return!`コンピュテーション式でします。|
|`Run`|`M<'T> -> M<'T>` または<br /><br />`M<'T> -> 'T`|コンピュテーション式を実行します。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` または<br /><br />`M<unit> * M<'T> -> M<'T>`|コンピュテーション式のシーケンスに対して呼び出されます。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` または<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|に対して呼び出さ`for...do`コンピュテーション式内の式。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|に対して呼び出さ`try...finally`コンピュテーション式内の式。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|に対して呼び出さ`try...with`コンピュテーション式内の式。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|に対して呼び出さ`use`コンピュテーション式内のバインディングです。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|に対して呼び出さ`while...do`コンピュテーション式内の式。|
|`Yield`|`'T -> M<'T>`|に対して呼び出さ`yield`コンピュテーション式内の式。|
|`YieldFrom`|`M<'T> -> M<'T>`|に対して呼び出さ`yield!`コンピュテーション式内の式。|
|`Zero`|`unit -> M<'T>`|空のと呼ばれる`else`の分岐`if...then`コンピュテーション式内の式。|
使用し、返しますビルダー クラスでメソッドの多くは、`M<'T>`コンス トラクターは、結合された計算の種類を表すとは別に定義された型は、通常、`Async<'T>`ための非同期ワークフローおよび`Seq<'T>`ワークフローのシーケンス。 これらのメソッドのシグネチャは、1 つの構築から返されるワークフロー オブジェクトは、次に渡すことができるようにそれらを結合し、互いに入れ子になった有効にします。 コンピュテーション式を解析する場合、コンパイラは、前の表に、メソッドとそのコンピュテーション式内のコードを使用して、一連の入れ子になった関数呼び出しに式を変換します。

入れ子になった式は、次の形式です。

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

上記のコードへの呼び出しで`Run`と`Delay`コンピュテーション式ビルダー クラスで定義されていない場合は省略します。 としてここに示される、コンピュテーション式の本体`{| cexpr |}`は、次の表で説明の翻訳でビルダー クラスのメソッドに関連する呼び出しに変換します。 コンピュテーション式`{| cexpr |}`に従ってこれらの変換を再帰的に定義されているは、 `expr` f# の式と`cexpr`コンピュテーション式です。



|式|変換|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}<code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}<code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
前の表に`other-expr`それ以外の場合、表に一覧表示されていない式を記述します。 ビルダー クラスは、前の表に、翻訳をすべてサポートしているすべてのメソッドを実装する必要はありません。 実装されていないこれらのコンストラクトでは、その型の計算式で使用できません。 たとえば、サポートしない場合、 `use` 、コンピュテーション式のキーワードの定義を省略することができます`Use`ビルダー クラスにします。

次のコード例では、一連の手順を実行することができる、一度に 1 つのステップを評価する計算をカプセル化する計算式を示します。 A 判別共用体型、 `OkOrException`、これまでに評価された式のエラー状態をエンコードします。 このコードでは、ビルダー メソッドのいくつかの定型実装など、コンピュテーション式で使用できるいくつかの一般的なパターンを示します。

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

コンピュテーション式が、式から返される、基になる型です。 計算の結果または遅延の計算を実行できる、基になる型を表すことがありますか、それに何らかの種類のコレクションを反復処理手段を提供することがあります。 前の例では、基になる型は**最終的に**です。 シーケンス式では、基になる型は<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>します。 クエリ式では、基になる型は<xref:System.Linq.IQueryable?displayProperty=nameWithType>します。 非同期ワークフローでは、基になる型は[ `Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)です。 `Async`オブジェクトは結果を計算するために実行する作業を表します。 たとえば、呼び出す[ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)計算を実行し、結果を返すにします。

## <a name="custom-operations"></a>カスタム操作
コンピュテーション式のカスタム処理を定義し、コンピュテーション式では演算子として、カスタム操作を使用できます。 たとえば、クエリ式ではクエリ演算子を含めることができます。 カスタムの操作を定義するときは、結果を定義する必要がありますとコンピュテーション式内のメソッドです。 カスタム操作を定義するのには、コンピュテーション式のビルダー クラスに配置し、適用、 [ `CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)です。 この属性は、これは、カスタム操作で使用する名前、引数として文字列を使用します。 この名前は、スコープ コンピュテーション式の始め中かっこの開始時に渡されます。 そのため、このブロックで、カスタム操作と同じ名前のある識別子を使用しないでください。 たとえばなどの識別子の使用を回避`all`または`last`クエリ式でします。

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[非同期ワークフロー](asynchronous-workflows.md)

[シーケンス](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[クエリ式](query-expressions.md)
