---
title: F# コード formattin のガイドライン
description: F# コードを書式設定するためのガイドラインを説明します。
ms.date: 05/14/2018
ms.openlocfilehash: e5c700ca9ae3968243f11c1237b9e4b26e580dcf
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="f-code-formatting-guidelines"></a>F# コードのガイドラインを書式設定

この記事は、f# コードが実行されるように、コードを書式設定する方法のガイドラインを提供しています。

* 通常、読みやすくとして表示
* Visual Studio のツールおよび他のエディターの書式設定によって適用される規則に従って、
* その他のコードをオンラインに似ています

これらのガイドラインに基づいています[f# の書式設定規則に包括的なガイド](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)によって[Anh 場を南 Phan](https://github.com/dungpa)です。

## <a name="general-rules-for-indentation"></a>インデントの一般的な規則

F# で既定では、重要なホワイト スペースを使用します。 次のガイドラインについては、これをかけることがいくつかの課題を使い分ける方法に関してガイダンスを提供するものです。

### <a name="using-spaces"></a>スペースを使用します。

インデントが必要な場合は、スペース、タブではなくを使用する必要があります。 少なくとも 1 つの領域が必要です。 組織がインデントに使用する空白文字の数を指定するコーディング規則を作成できます。インデントを設定する各レベルのインデントの 2 つ、3 つまたは 4 つのスペースが一般的です。

**インデントあたり 4 つのスペースはお勧めします。**

ただし、プログラムのインデントは主観的な問題。 バリエーションは、[ok] が最初の規則に従う必要がありますは*インデントの整合性*です。 一般的に受け入れられるインデントのスタイルを選択し、コードベース全体にわたって体系的に使用します。

## <a name="formatting-discriminated-union-declarations"></a>共用体の宣言を判別する書式設定

インデント`|`で 4 つのスペースの種類の定義。

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

インスタンス化された判別共用体に複数の行に分割するは、インデントの新しいスコープ含まれているデータを与える必要があります。

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

閉じかっこは、新しい行にすることもできます。

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-tuples"></a>組の書式設定

組のインスタンス化はかっこで囲まれた、する必要があり、区切るコンマ内で従う必要がありますを 1 つのスペースで例: `(1, 2)`、`(x, y, z)`です。

組のパターンに一致するでは、かっこを省略する場合は、一般に受け入れられた例外です。

```fsharp
let (x, y) = z // Destructuring

match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-records"></a>レコードを書式設定

短いレコードは、1 つの行に記述できます。

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

長いレコードは、ラベルの新しい行を使用してください。

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

開始トークンを配置する、同じ行で、新しい行の終わりトークンも問題ありません。

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

リストと配列の要素の場合と同じ規則が適用されます。

## <a name="formatting-lists-and-arrays"></a>書式設定のリストと配列

書き込む`x :: l`前後に空白、`::`演算子 (`::`スペースで囲まれたため、挿入演算子は、) と`[1; 2; 3]`(`;`のため後にスペースを区切り記号である)。

常に 2 つの個別の中かっこのような演算子の間に少なくとも 1 つの領域を使用します。 たとえば、間に空白のままにして、`[`と`{`です。

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

リストと複数行にわたって配列は、レコードと同様のルールを従います。

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

## <a name="formatting-if-expressions"></a>書式設定の if 式

条件のインデントは、それらを構成する式のサイズによって異なります。 場合`cond`、`e1`と`e2`は小さく、単にそれを 1 つの行に書き込みます。

```fsharp
if cond then e1 else e2
```

場合`e1`と`cond`は、小さなが`e2`大き。

```fsharp
if cond then e1
else
    e2
```

場合`e1`と`cond`が大きいと`e2`小さ。

```fsharp
if cond then
    e1
else e2
```

すべての式が大きい場合は。

```fsharp
if cond then
    e1
else
    e2
```

複数の条件で`elif`と`else`と同じスコープでインデント、 `if`:

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a>パターン マッチング

使用して、`|`インデントなしで、一致した文字列の各句。 式が短い場合は、1 行を使用することができます。

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

// OK
match l with [] -> false | _ :: _ -> true
```

パターン マッチングの矢印の右の式が大きすぎる場合、次の行のインデントを設定した 1 つのステップに移動、 `match` /`|`です。

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

パターン マッチにより、開始、匿名の関数の`function`は、通常はインデントされません離れすぎています。 たとえば、次のように 1 つのスコープをインデントも可能です。

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

パターン マッチで定義されている関数で`let`または`let rec`の開始後にインデントされた 4 つのスペースをする必要があります`let`場合でも、`function`キーワードを使用します。

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

矢印の配置はお勧めしません。

## <a name="formatting-trywith-expressions"></a>書式設定やり直して/式

例外の種類で一致するパターンと同じレベルにインデントする`with`です。

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

## <a name="formatting-function-parameter-application"></a>関数パラメーターのアプリケーションを書式設定

一般に、関数パラメーターのほとんどのアプリケーションは、同じ行に行われます。

新しい行に関数にパラメーターを適用する場合は、1 つのスコープでインデントします。

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

次の行、または、ぶら下がりと匿名関数の引数を指定できます`fun`引数行にします。

```fsharp
// OK
let printListWithOffset a list1 =
    List.iter (fun elem ->
        printfn "%d" (a + elem)) list1

// OK, but prefer previous
let printListWithOffset a list1 =
    List.iter (
        fun elem ->
            printfn "%d" (a + elem)) list1
```

### <a name="formatting-infix-operators"></a>挿入演算子を書式設定

スペースで別の演算子。 このルールの明確な例外は、`!`と`.`演算子。

挿入辞式では、[ok] を同じ列に編成します。

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a>パイプライン演算子を書式設定

パイプライン`|>`操作対象の式のすぐ下にある行の先頭に移動する必要があります。

```fsharp
// OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat

// OK, but prefer previous
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

### <a name="formatting-modules"></a>モジュールの書式設定

モジュールを基準としたローカル モジュール内のコードのインデントを設定する必要がありますが、最上位レベルのモジュール内のコードにインデントする必要がありますされません。 Namespace 要素は、インデントする必要はありません。

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

### <a name="formatting-object-expressions-and-interfaces"></a>オブジェクトの式とインターフェイスの書式設定

同じ方法では、オブジェクトの式とインターフェイスを揃える必要があります`member`4 つのスペースの後にインデントします。

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-whitespace-in-expressions"></a>式内の空白文字の書式設定

F# の式内の余分な空白文字を避けてください。

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

名前付き引数もない領域を囲む、 `=`:

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

## <a name="formatting-blank-lines"></a>空白行を書式設定

* 独立した最上位関数やクラスの定義を 2 つの空白行でします。
* クラスの内部でメソッドの定義は、単一の空白行で区切られます。
* 余分な空白行は、関連する関数のグループを区切るための (慎重) に使用できます。 空白行は、一連の関連する困らせる (たとえば、一連のダミー実装) の間で省略可能です。
* 論理的なセクションを示すために、適度関数では、空白行を使用します。

## <a name="formatting-comments"></a>コメントの書式設定

通常、ML スタイル ブロックのコメントを複数のダブル スラッシュ コメントを選びます。

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    Generally avoid these kinds of comments.
*)
```

インライン コメントは、最初の文字を大文字にする必要があります。

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a>名前付け規則

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a>クラス バインド、式バインドおよびバインド パターンの値と関数のキャメル ケースを使用します。

すべての名前をキャメル ケースを使用する許容される f# スタイルには、ローカル変数として、またはにパターン マッチと関数定義がバインドされているし、共通です。

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

クラスのローカルにバインドされた関数は、キャメル ケースを使用してもする必要があります。

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a>内部およびプライベートのモジュール バインド値や関数のキャメル ケースを使用します。

キャメル ケースを使用して、プライベート モジュール バインド値を次のようにします。

* スクリプトでアドホック関数

* モジュールまたは型の内部実装を構成する値

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="avoid-underscores-in-names"></a>名前にアンダー スコアを回避します。

従来、一部の f# ライブラリは、名前にアンダー スコアを使用するがします。 ただし、これが不要になった広く受け入れられて、.NET の名前付け規則と衝突するために一部です。 つまり、f# プログラマによってアンダー スコアを使用頻度の高い、および使用して部分的履歴上の理由から、許容範囲は、点が重要です。 ただし、スタイルが多くの場合、それを使用するかどうかを選択する他のユーザーによって我慢しなければならないことに注意してください。

いくつかの例外には、アンダー スコアが非常に一般的であるネイティブなコンポーネントとの相互運用が含まれます。

### <a name="use-standard-f-operators"></a>標準の f# 演算子を使用します。

次の演算子は、f# の標準ライブラリで定義され、対応を定義する代わりに使用する必要があります。 読みやすく理解し慣用コードを作成する傾向がありますが、これらの演算子を使用するをお勧めします。 開発者向けの背景 OCaml またはその他の関数型プログラミング言語では、さまざまな表現方法に慣れて可能性があります。 次の一覧は、推奨の f# 演算子をまとめたものです。

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Throwing away a value
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

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a>ジェネリックのプレフィックスの構文を使用します (`Foo<T>`) 後置構文方が優先的 (`T Foo`)

F# でジェネリック型の名前付けの両方、後置 ML スタイルを継承 (など、 `int list`) プレフィックス .NET スタイルだけでなく (たとえば、 `list<int>`)。 4 つの特定の型を除く、.NET のスタイルを使用するには。

1. F# では、一覧の後置形式を使用して:`int list`なく`list<int>`です。
2. F# オプションは、後置形式を使用して:`int option`なく`option<int>`です。
3. F# の配列、構文の名前を使用`int[]`なく`int array`または`array<int>`です。
4. 参照セルを使用して`int ref`なく`ref<int>`または`Ref<int>`です。

他のすべての種類では、前置形式を使用します。