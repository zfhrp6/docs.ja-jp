---
title: F# でのコーディング規則
description: F# コードを記述する場合は、一般的なガイドラインと表現方法を説明します。
ms.date: 05/14/2018
ms.openlocfilehash: f3d16f735ddc1901aeaa5ebb39e2fa2b70a3d836
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="f-coding-conventions"></a>F# でのコーディング規則

大規模な f# 使用経験から、次の規則が策定コードベースです。 [優れた f# コードの 5 つの原則](index.md#five-principles-of-good-f-code)各推奨事項の基盤となっています。 関連している、 [f# コンポーネントのデザイン ガイドライン](component-design-guidelines.md)、f#、コードだけでなくコンポーネント ライブラリなどの該当するが、します。

## <a name="organizing-code"></a>コードの整理

F# コードを整理する主な方法は 2 つの機能: モジュールと名前空間。 次は似ていますが、次の相違点を持つ操作を行います。

* 名前空間は、.NET 名前空間としてコンパイルされます。 モジュールは、静的クラスとしてコンパイルします。
* 名前空間は、常に最上位レベルです。 モジュールは、最上位レベルとその他のモジュール内で入れ子にできます。
* 名前空間は、複数のファイルにまたがることができます。 モジュールことはできません。
* モジュールは、使用する装飾できます`[<RequireQualifiedAccess>]`と`[<AutoOpen>]`です。

次のガイドラインには、これらを使用してコードを整理するのに役立ちます。

### <a name="prefer-namespaces-at-the-top-level"></a>最上位レベルの名前空間を使用します。

コードについては、パブリックに使用できるように、名前空間は、最上位レベルのモジュールに優先します。 .NET 名前空間としてコンパイル、ため問題に c# から使用できるようにされません。

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

最上位レベルのモジュールを使用することがありますは表示されません、f# からのみ呼び出されるとは異なるが C# の場合、コンシューマーの呼び出し元を修飾することによって驚き可能性があります`MyClass`で、`MyCode`モジュール。

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a>慎重に適用します。 `[<AutoOpen>]`

`[<AutoOpen>]`コンストラクトを汚染は、呼び出し元に対して使用できるもののスコープと由来問題に対する回答が「マジック」です。 これは一般的に便利です。 この規則の例外は、f# コア ライブラリ自体 (ただし、この事実も少し意見の分かれる)

ただし、パブリック API を整理するとは別にそのパブリック API からヘルパー機能を持っている場合、利便性を勧めします。

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

これにより、関数のパブリック API からクリーンに別の実装の詳細を完全修飾するヘルパー メソッドを呼び出すたびにしなくてもできます。

さらに、拡張メソッドと名前空間レベルでの式ビルダーを公開する簡潔で表現`[<AutoOpen>]`です。

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a>使用して`[<RequireQualifiedAccess>]`するたびに名前が競合または読みやすさが容易になると思われる

追加する、`[<RequireQualifiedAccess>]`属性をモジュールにことを示し、モジュールが開かれていませんアクセスを修飾するモジュールの要素への参照が明示的に必要なことです。 たとえば、`Microsoft.FSharp.Collections.List`モジュールは、この属性を持ちます。

これは、機能は、関数と、モジュール内の値は、他のモジュールの名前と競合する可能性のある名前を持つ場合に便利です。 修飾のアクセスを必要とすると、長期的な保守容易性とライブラリの発展性が大幅に増やすできます。

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a>並べ替え`open`ステートメント位相的

F# で宣言の順序が重要な使用含む`open`ステートメントです。 これとは異なり、C# の場合は、ここでの効果`using`と`using static`はファイルでこれらのステートメントの順序に依存しません。

F# では、スコープに開かれた要素は既に組み込まれている他のユーザーでシャドウできます。 つまり、その並べ替え`open`コードの意味をステートメントが変わる可能性があります。 その結果、すべての並べ替えは、任意`open`ステートメント (たとえば、英数字順) 通常は推奨されません、意図した動作の違いを生成するようにします。

代わりに、ことをお勧めして並べ替えること[位相的](https://en.wikipedia.org/wiki/Topological_sorting); は、注文、`open`順序内のステートメント_レイヤー_定義は、システムのです。 英数字のトポロジの異なるレイヤー内での並べ替えを行うことがありますも見なされます。

たとえば、次に、f# コンパイラ サービス パブリック API ファイルのトポロジの並べ替えを示します。

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

改行が各レイヤーが後で並べ替えられる英数字順にトポロジのレイヤーを区切ることに注意してください。 これは、クリーンに値を誤ってシャドウせずコードを整理します。

## <a name="use-classes-to-contain-values-that-have-side-effects"></a>クラスを使用して、副作用がある値が含まれる

何度も値を初期化して、データベースまたはその他のリモート リソースにコンテキストをインスタンス化するなどの副作用を持つことができる場合。 などのモジュールを初期化し、後続の関数で使用しようとしがちです。

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

これをお勧め頻繁に不適切な理由はいくつかの。

コードベースでアプリケーションの構成をプッシュする最初に、`dep1`と`dep2`です。 これは、大規模なコードベースで維持するが困難です。

第二に、静的に初期化されたデータは、自体のコンポーネントが複数のスレッドを使用する場合、スレッド セーフではない値を含めないでください。 この違反が明確に`dep3`です。

最後に、モジュールの初期化は、静的コンス トラクターに、全体のコンパイル単位をコンパイルします。 場合は、そのモジュール内の let バインドされた値の初期化でエラーの発生が明らかに、`TypeInitializationException`アプリケーション全体の有効期間にわたってしキャッシュされました。 これは、診断が難しいことができます。 通常は、内部例外については、理由を試みることができますが場合がない、根本原因を示しませんします。

代わりに、依存関係を保持するためにだけ、単純なクラスを使用します。

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member __.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member __.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

これにより、以下。

1. API 自体の外部依存の状態をプッシュします。
2. API 外部で、構成を行うようになりましたことができます。
3. 従属変数の値の初期化でエラーとしてマニフェストを`TypeInitializationException`です。
4. API では、簡単にテストできるようになりました。

## <a name="error-management"></a>エラー管理

大規模なシステムでエラーの管理が複雑になり、微妙試み、シルバー、システムを確認するために行頭文字がフォールト トレラントし、適切に動作はありません。 次のガイドラインには、この困難な領域を移動するためのガイダンスを提供する必要があります。

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a>エラーの場合と、ドメインに組み込みの種類で無効な状態を表す

[判別共用体](../language-reference/discriminated-unions.md)、f# を使用する、できますを型システムの障害のあるプログラムの状態を表します。 例えば:

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

この場合、これには銀行口座から資金を引き出しが失敗する可能性を 3 つの既知方法があります。 各エラーの場合は、型で表され、対処できるようにため安全に、プログラム全体でします。

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

一般に、さまざまな方法をモデル化することができる場合に当たることができます**失敗**ドメイン内のエラー処理コードが不要になったとして扱われますものだけでなく正規プログラム フローを処理する必要があります。 単に通常のプログラム フローの一部であるとは見なされません**例外的な**します。 この 2 つの主な利点があります。

1. 時間の経過と共に変更では、ドメインを管理しやすくなります。
2. エラーの場合は、単体テストを容易にします。

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a>エラーは、型で表すことができないときに例外を使用します。

問題ドメインでは、すべてのエラーを表示することができます。 これらのエラーは*例外的な*のため、本質的に発生させるし、f# の例外をキャッチする機能。

最初に、お勧めお読みになる、[例外のデザイン ガイドライン](../../standard/design-guidelines/exceptions.md)です。 これらにも適用 f# です。

例外の発生の目的で f# で使用できる主な構成要素は、次の優先順位で検討してください。

| 関数 | 構文 | 目的 |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | 発生させる、`System.ArgumentNullException`指定された引数名を使用します。 |
| `invalidArg` | `invalidArg "argumentName" "message"` | 発生させる、`System.ArgumentException`指定された引数名とメッセージを使用します。 |
| `invalidOp` | `invalidOp "message"` | 発生させます、`System.InvalidOperationException`指定したメッセージを使用します。 |
|`raise`| `raise (ExceptionType("message"))` | 例外をスローする汎用の機構です。 |
| `failwith` | `failwith "message"` | 発生させます、`System.Exception`指定したメッセージを使用します。 |
| `failwithf` | `failwithf "format string" argForFormatString` | 発生させる、`System.Exception`書式指定文字列とその入力によって決まりますメッセージを使用します。 |

使用して`nullArg`、`invalidArg`と`invalidOp`をスローするためのメカニズムとして`ArgumentNullException`、`ArgumentException`と`InvalidOperationException`適切な場合です。

`failwith`と`failwithf`関数一般的に使用しないで、ベースを起動するため`Exception`入力と、特定の例外ではありません。 1、[例外のデザイン ガイドライン](../../standard/design-guidelines/exceptions.md)、可能な場合より詳細な例外を発生させる場合します。

### <a name="using-exception-handling-syntax"></a>例外処理構文を使用します。

F# を使用して例外パターンをサポートしています、`try...with`構文。

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

パターン マッチを使用して例外の発生時に実行する機能の調整はクリーンなコードを保持する場合は、少し難しいことができます。 これに対処するこのような方法の 1 つを使用して[アクティブ パターン](../language-reference/active-patterns.md)例外自体でのエラー ケースを囲むグループ機能するための手段として。 たとえばは、例外をスローする場合は、例外のメタデータで有益な情報を囲むできる API が消費している可能性があります。 アクティブ パターン内のキャプチャされた例外の本体で便利値へのアンラッピングをいくつかの状況で便利な値であることができますを返します。

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a>Monadic のエラーに例外を置き換える処理を使用しないでください。

例外は、関数型プログラミングで taboo 多少と見なされます。 実際には、ません機能を考慮しても安全であるために、例外は、純粋性に違反します。 ただし、コードが実行しなければならないとその実行時エラーが発生する可能性が実際には、これは無視されます。 一般に、ほとんどの目的が純粋なも望ましくないを最小限に抑えるには、合計でもないことを前提としてコードを記述します。

ことが重要コア長所/の次の側面の例外に関して、関連性と、全体として、.NET ランタイムとクロス言語エコシステムで適切かどうかを検討してください。

1. 詳細な診断情報については、これは、問題をデバッグするときに特に便利です。
2. ランタイムおよび他の .NET 言語で周知です。
3. 重要な定型句の外に出るコードと比較して大幅に削減できます*回避*アドホックごとに、セマンティクスの一部のサブセットを実装することによって例外。

この 3 番目の点が重要です。 重要な複雑な操作、できなかった例外を使用すると、次のような構造を処理することがあります。

```fsharp
Result<Result<MyType, string>, string list>
```

「Stringly に型指定された」エラー時に一致するパターンのような脆弱なコードが生じる可能性が簡単にします。

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

さらに、「より良い」の型を返す関数の「単純」desire で任意の例外を飲み込む動かさを指定できます。

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

残念ながら、`tryReadAllText`無数のファイル システムで発生する可能性がある点に基づくさまざまな例外をスローすることができ、このコードを破棄されなくが実際にする起きて環境内で間違った情報。 結果型は、このコードに置き換えた場合して「stringly に型指定された」エラー メッセージの解析に。

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

例外オブジェクト自体を配置することで、`Error`コンス トラクターだけ強制的に、関数ではなく、呼び出しサイトでの例外の種類を正しく処理します。 これを効果的に行うには、API の呼び出し元として扱うに非常に楽しいものではない、チェックされた例外を作成します。

キャッチするには、上記の例の適切な代替手段は、*特定*例外およびその例外のコンテキストで意味のある値を返します。 変更する場合、`tryReadAllText`関数の次のように、`None`複数の意味を持ちます。

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

キャッチ オールとしてではなく、この関数は今すぐを正しく処理場合ファイルが見つからなかったし、その意味を戻り値を割り当てます。 この戻り値は、任意のコンテキスト情報を破棄またはコードの時点で関連することができない可能性があるケースに対処する呼び出し元に強制しない中にそのエラーの場合にマップできます。

などの型`Result<'Success, 'Error>`ここで、入れ子にしない、f# の省略可能な型はどちらの戻り値のものだった時を表す完全な基本的な操作に適した*もの*または*nothing*. いない例外の代わりに、され必要がありますいないで使用しようとして例外を置換します。 代わりに、それらに適用してください慎重に行う例外とエラーの管理ポリシーの特定の側面をアドレス対象となるようにします。

## <a name="partial-application-and-point-free-programming"></a>一部のアプリケーションとプログラミングのポイントを必要としません。

F# ポイントを必要としないスタイルで一部のアプリケーションであるため、プログラムにさまざまな方法をサポートします。 モジュールまたは何かの実装内でコードを再利用と役に立つこのことができますが、一般的にはないものをパブリックに公開します。 一般に、ポイントを必要としないプログラミングは、それ自体の長所があり、いないスタイルに従事している人の重要な知的バリアを追加できます。

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a>部分的に適用し、パブリック Api で、カリー化を使用しないでください。

ほとんどの例外を除き、パブリック Api で一部のアプリケーションの使用はコンシューマーが混乱することはできます。 通常、 `let`-f# コードでバインドされた値は**値**ではなく、**関数値**です。 値と関数の値を一緒に混在させることができますと引き換えに相当量の認知オーバーヘッドは、コードの行の数が少ないの保存などの演算子と組み合わされている場合に特に`>>`関数を作成します。

### <a name="consider-the-tooling-implications-for-point-free-programming"></a>ポイントを必要としないプログラミング ツールへの影響を検討してください。

カリー化関数には、その引数はラベル付けしません。 ツールへの影響があります。 次の 2 つの関数を考慮してください。

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

有効な関数は、これらはいずれもが`funcWithApplication`カリー化関数です。 エディターで、型、ポインターを合わせるときにこの参照してください。

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

呼び出しサイトで Visual Studio などのツールでのヒントは与えないに関してどのような意味のある情報、`string`と`int`実際には入力の種類を表します。

ようなポイントを必要としないコードが発生した場合`funcWithApplication`パブリックに使用できるをお勧め完全 η 拡張させるために行うツールできますで引数にわかりやすい名前。

さらに、ポイントのないコードをデバッグできますが困難になる不可能です。 名前にバインドされている値に依存するデバッグ ツール (たとえば、`let`バインディング) を実行して中間値の中間にあるを検査することです。 コードには、検査する値がない、するものはありませんをデバッグします。 将来的には、デバッグ ツールを以前に実行されたパスに基づくこれらの値を合成する進化可能性がありますが、できません、上、おすすめコンテンツを hedge することをお勧め*潜在的な*機能をデバッグします。

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a>内部の定型句を削減する手法として部分適用を検討してください。

前のポイントとは対照的は、部分適用は、アプリケーションまたは API の詳細な内部構造の中で定型句を削減するためのすばらしいツールです。 これは、単体テストの定型句に対処する問題では多くの場合より複雑な Api の実装に役立ちます。 たとえばを実現する方法、次のコードに示すどのような最もモック フレームワークを提供このようなフレームワークの外部の依存関係を取得することがなくし API を bespoke 関連を学習します。

たとえば、次のソリューションのトポロジを考慮してください。

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

`ImplementationLogic.fsproj` などのコードに公開する可能性があります。

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member __.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

単体テスト`Transactions.doTransaction`で`ImplementationLogic.Tests.fspoj`は簡単。

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

部分的に適用する`doTransaction`モック コンテキストにオブジェクトできますたびにモック コンテキストを構築する必要はありませんすべての単体テスト内の関数を呼び出します。

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

この手法をユニバーサルに適用されません、全体のコードベースが、複雑な内部構造と単体テストのそれらの内部構造の定型句を削減することをお勧めします。

## <a name="access-control"></a>アクセス制御

F# は、複数のオプションの[アクセス制御](../language-reference/access-control.md).NET ランタイムで使用可能なから継承します。 これらは型に対してだけ使用可能ではありません - するその関数の場合にも使用できます。

* 必要に応じて非`public`型とパブリックに使用できるようにすることが必要になるまでのメンバーです。 これにどのようなコンシューマーのいくつか最小限に抑えられます
* すべての機能をヘルパーのままにしておくこと`private`です。
* 使用を検討`[<AutoOpen>]`多数になる場合、ヘルパー関数のプライベート モジュールにします。

## <a name="type-inference-and-generics"></a>型の推定とジェネリック

型の推論では、多数の定型句を入力することから保存できます。 F# コンパイラで自動ジェネリック化を使用して、ユーザー側でほとんどない余分な労力より汎用的なコードを記述できるとします。 ただし、これらの機能は、汎用的なではありません。

* 明示的な型のパブリック Api で引数名のラベルを付けるし、この型の推定に依存しないでください。

    この理由は**する**API では、コンパイラではないの形状のコントロールでする必要があります。 コンパイラは、の型の推論でジョブを正常に実行できることに依存している内部構造には、種類が変更された場合に、API の変更の形状を設定することです。 目的の動作がありますが、下流のコンシューマーが対処する重大な API の変更がほぼ確実に発生します。 代わりに、パブリック API の形状を明示的に制御する場合は、これらの重大な変更を制御できます。 DDD 用語では、このことができますと見なす対策破損レイヤー。

* ジェネリック引数をわかりやすい名前を付けることを検討してください。

    特定のドメインに固有ではない本当に汎用的なコードを記述していない場合にわかりやすい名前に作業中のドメインを理解する他のプログラマは役立ちます。 という名前の型パラメーターなど、`'Document`ドキュメントとの対話のコンテキストでデータベースによりわかりやすく、関数またはメンバーを使用しているジェネリック ドキュメントの種類を受け入れることができません。

* PascalCase でジェネリック型パラメーターの名前付けを検討してください。

    これは、作業を行う .NET では、ため PascalCase ではなく snake_case またはキャメル ケースを使用することをお勧めの一般的な方法です。

最後に、自動ジェネリック化とは限りません f# または大規模なコードベースに追加された新しい方のため boon です。 一般的なコンポーネントを使用するのには、認知オーバーヘッドがあります。 さらに、自動的にでさまざまな入力の種類 (let だけの場合は、そのために使用する)、一般化された関数を使用しない場合がその時点でジェネリックする実際の利点はありません。 常にかどうかを記述するコードは実際には役に立つジェネリックを検討してください。

## <a name="performance"></a>パフォーマンス

F# の値では、既定では、特定のクラス (特に、関係する同時実行性と並列処理) のバグを回避することができますを変更できません。 ただし、場合によっては、実行時間やメモリの割り当ての最適な (またはでも適切な) の効率を実現するために作業の範囲可能性があります最適使用して実装の状態の変更は、インプレースです。 F# のオプトインごとに可能な限り、`mutable`キーワード。

ただし、使用の`mutable`f# で純粋性の機能に対応していない感じる可能性があります。 純度からの期待を調整する場合は問題ありません。 これは[参照の透過性](https://en.wikipedia.org/wiki/Referential_transparency)です。 参照の透過性のない純度 - が f# の関数を作成するときのエンド目標です。 これにより、パフォーマンス クリティカル コードの変更ベースの実装に対して機能インターフェイスを作成することができます。

### <a name="wrap-mutable-code-in-immutable-interfaces"></a>変更可能なコードを変更できないインターフェイスでラップします。

目標として参照透過性は、パフォーマンスが重要な機能の変更可能な大打撃を公開しないコードを記述するが重要です。 たとえば、次のコードを実装して、 `Array.contains` f# コア ライブラリ内の関数。

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

この関数を複数回呼び出すことも、基になる配列が変更されません。 また、不要にそれを利用することで、変更可能な状態を維持します。 コード内にほとんどすべての行が変異を使用している場合でもがしいものに透過的なです。

### <a name="consider-encapsulating-mutable-data-in-classes"></a>クラスの変更可能なデータをカプセル化することを検討してください。

前の例では、変更可能なデータを使用して操作をカプセル化するのに 1 つの関数を使用します。 これは常により複雑なデータ セットのための十分なです。 次の関数のセットを考慮してください。

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

このコードは、パフォーマンスおよびですが、呼び出し元の保守を担当している変異ベースのデータ構造を公開します。 これは、メンバーを持たない基になる変更可能なクラスの内部でラップすることができます。

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

`Closure1Table` 基になるデータ構造を維持するために呼び出し元を強制しないため、基になる変異ベースのデータ構造をカプセル化します。 クラスは、データとは、呼び出し元に詳細情報を公開することがなく変異ベースのルーチンをカプセル化する強力な手段です。

### <a name="prefer-let-mutable-to-reference-cells"></a>必要に応じて`let mutable`セルを参照する

参照セルは、値そのものではなく、値への参照を表す方法です。 パフォーマンス クリティカルなコードを使用できますが、通常は推奨されません。 次に例を示します。

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

参照セルの使用は、逆参照し、基になるデータの再参照することですべての後続のコードを「汚染」です。 代わりに、 `let mutable`:

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

ラムダ式の中間で変異の 1 つのポイントとは別に他のすべてのコードを接して`acc`、通常の使用方法に違いはありません、同様の方法で行うことができます`let`-変更不可の値をバインドします。 これは、ため、時間の経過と共に変化しやすく、されます。

## <a name="object-programming"></a>オブジェクトのプログラミング

F# は、オブジェクトおよびオブジェクト指向 (オブジェクト指向) の概念を完全にサポートします。 多くのオブジェクト指向の概念には、強力で便利ですが、それらのすべてを使用する場合に適してします。 次の一覧は、高レベルのオブジェクト指向機能のカテゴリに関するガイダンスを提供します。

**多くの状況でこれらの機能の使用を検討してください。**

* ドット付き表記 (`x.Length`)
* インスタンス メンバー
* 暗黙的なコンス トラクター
* 静的メンバー
* インデクサー表記 (`arr.[x]`)
* 名前付きおよびオプションの引数
* インターフェイスとインターフェイスの実装

**最初に、これらの機能に到達しないは慎重に適用して、問題を解決するは便利であるときに。**

* メソッドのオーバーロード
* 変更可能なデータをカプセル化
* 型の演算子
* 自動プロパティ
* 実装する`IDisposable`と `IEnumerable`
* 型の拡張機能
* イベント
* 構造体
* デリゲート
* 列挙体

**一般的に使用する必要がありますしない限り、これらの機能を回避します。**

* 型の継承に基づいた階層と実装の継承
* Null 値と `Unchecked.defaultof<_>`

### <a name="prefer-composition-over-inheritance"></a>コンポジションを継承よりも優先します。

[継承の経過と共に変化](https://en.wikipedia.org/wiki/Composition_over_inheritance)は長年にわたる表現な f# コードが遵守することができます。 基本的な原則ことする必要がありますいない基本クラスを公開し、強制的に呼び出し元が機能を実装する基本クラスを継承します。

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a>クラスを必要としない場合は、インターフェイスを実装するオブジェクトの式を使用します。

[オブジェクト式](../language-reference/object-expressions.md)クラスの内部でようにする必要はありません値に実装されたインターフェイスをバインドをその場でインターフェイスを実装することを許可します。 これは、便利な場合に特にする_のみ_インターフェイスを実装する完全クラスのない必要とする必要があります。

たとえば、次のコードは内で実行される[Ionide](http://ionide.io/)にないシンボルを追加した場合は、コードの修正操作を提供する、`open`ステートメント。

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

Visual Studio コード API を扱うときに、クラスの必要はありません、ためオブジェクトの式は、この最適なツールです。 単体テスト、暫定的な方法でテスト ルーチンを持つインターフェイスをスタブするときの重要なにもです。

## <a name="type-abbreviations"></a>型略称

[型略称](../language-reference/type-abbreviations.md)関数のシグネチャまたはより複雑な型などの別の型にラベルを割り当てるに便利です。 次のエイリアスがで計算を定義する必要な条件にラベルを割り当てますなど[CNTK](https://www.microsoft.com/cognitive-toolkit/)ライブラリを習得詳細。

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

`Computation`名がエイリアスがシグネチャと一致するすべての関数を表すために便利な方法です。 型の省略形を使用して、次のようにして、便利より簡潔なコードできます。

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a>ドメインを表す型の省略形は使用しないでください。

型の省略形は便利な関数のシグネチャに、名前を付けることが、可能性がある混乱を招く場合、その他の種類の省略形です。 この省略形を考慮してください。

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

複数の方法で混乱を招くことができます。

* `BufferSize` 抽象化です。整数の単なる別の名前です。
* 場合`BufferSize`公開されるパブリック API で、簡単に解釈される可能性を単に意味`int`です。 一般に、ドメインの種類に複数の属性を持ちなどのプリミティブ型ではない`int`です。 この省略形では、その仮定に違反します。
* 大文字と小文字`BufferSize`(PascalCase) は、この型がより多くのデータを保持していることを意味します。
* このエイリアスは、見やすく関数の名前付き引数を提供するのと比較を提供していません。
* コンパイルされた IL; で、省略形が明らかにはこの別名は、コンパイル時の構造と同様の整数です。

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) =
        ...
```

要約すると、型の省略形の落とし穴ができる**いない**これらの省略形は、型を抽象化します。 前の例では、`BufferSize`のみです、`int`は背後でない追加のデータや新機能だけでなく、型システムから利点`int`は既にです。
