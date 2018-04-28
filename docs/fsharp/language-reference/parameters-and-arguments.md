---
title: パラメーターと引数 (F#)
description: パラメーターを定義して、関数、メソッド、およびプロパティに引数を渡すのための f# 言語サポートについて説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e146ec4e877bb89f10e2f3daad2d8356c29fa81f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="parameters-and-arguments"></a>パラメーターと引数

このトピックでは、パラメーターを定義して、関数、メソッド、およびプロパティに引数を渡すのための言語サポートについて説明します。 定義して、可変個の引数を受け取るメソッドを使用する方法と、参照渡しする方法に関する情報が含まれています。


## <a name="parameters-and-arguments"></a>パラメーターと引数
用語*パラメーター*を指定する必要な値の名前を表すために使用します。 用語*引数*は各パラメーターに指定された値を使用します。

パラメーターは、組、カリー化形式、または 2 つの組み合わせで指定できます。 明示的なパラメーター名を使用して引数を渡すことができます。 メソッドのパラメーターを省略可能として指定し、既定値を指定できます。


## <a name="parameter-patterns"></a>パラメーターのパターン
関数やメソッドに渡されるパラメーターは一般に、スペースで区切られたパターンです。 つまり、基本的に、パターンのいずれかの記載[Match 式](match-expressions.md)関数またはメンバーのパラメーター リストで使用できます。

メソッドは、通常渡す引数のタプルの形式を使用します。 これの処理タプルの形式に一致する .NET メソッドに引数が渡される方法は他の .NET 言語の観点から明確結果。

カリー化されたフォームを使用して作成した関数で最もよく使用される`let`バインドします。

次の疑似コードは、組、カリー化された引数の例を示します。

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

組にいくつかの引数があり、いくつかの場合は、形式を組み合わせています。

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

他のパターンは、パラメーター リストにも使用できますが、パラメーターのパターンが可能なすべての入力が一致しない場合があります不完全な一致実行時にします。 例外`MatchFailureException`引数の値がパラメーター リストで指定されたパターンと一致しない場合に生成します。 不完全な一致では、パラメーターのパターンと、コンパイラは警告を発行します。 他には、少なくとも 1 つのパターンが一般的に、パラメーター リストに便利ですし、ワイルドカード パターンがします。 提供されている引数を無視したいときに、パラメーター リストでワイルドカード パターンを使用するとします。 次のコードでは、引数リスト内のワイルドカード パターンの使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

ワイルドカード パターンでは、不要なコマンドラインの引数は通常、次のコードと同様に、文字列の配列として提供されているときに、使用するプログラムへのメイン エントリ ポイントなど、渡された引数を必要としないときに便利です。 を指定できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

引数でときどき使われるその他のパターンは、`as`パターン、および判別共用体、およびアクティブ パターンに関連付けられている識別子パターン。 単一ケースの判別共用体パターンは次のように使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

出力は次のとおりです。

```
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

アクティブ パターンは、引数を次の例のように、目的の形式に変換するときに、たとえば、パラメーターとして役立ちます。

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

使用することができます、`as`次のコード行に示すように、ローカルの値として照合する値を格納するパターン。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

使用されることがある別のパターンは、関数の本文として提供して、名前のない最後の引数のままにする関数、暗黙の型引数をすぐにパターン マッチを実行する、ラムダ式です。 この例では、次のコード行がします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

このコードをジェネリック リストを受け取りを返す関数定義`true`リストが空の場合と`false`それ以外の場合。 このような手法を使用すると、コードが読みにくくなります。

場合によっては、不完全な一致を伴うパターンは、役立ちます。 など、プログラムの一覧が 3 つだけの要素を持つことがわかっている場合がありますパターンを使用する、次のようにパラメーター リスト内です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

不完全な一致パターンの使用は、クイック プロトタイプの作成とその他の一時的な使用に最適な予約されています。 コンパイラでは、このようなコードの警告を発行します。 このようなパターンでは、すべての可能な入力の一般的なケースを対応することはできませんし、したがってはコンポーネント Api には向いていません。

## <a name="named-arguments"></a>名前付き引数
メソッドの引数は、引数のコンマ区切りリストを内の位置で指定できます。 または渡すことができるメソッドを明示的に等号 (=) とで渡される値の後に、名前を指定します。 名前を提供することで指定した場合は、宣言で使用されているとは異なる順序で表示ことができます。

名前付き引数、コード読みやすくし、適応性がより API では、メソッドのパラメーターの順序変更などの変更の特定の種類になります。

名前付き引数がなく、メソッドに対してのみ許可されます`let`-関数、関数の値、またはラムダ式を連結します。

次のコード例では、名前付き引数の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

クラスのコンス トラクターの呼び出しでは、名前付き引数に似た構文を使用して、クラスのプロパティの値を設定できます。 次の例は、この構文を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

詳細については、次を参照してください。[コンス トラクター (f#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05)です。

## <a name="optional-parameters"></a>省略可能なパラメーター
パラメーター名の前に疑問符 () を使用して、メソッドのオプション パラメーターを指定できます。 省略可能なパラメーターが、f# オプションの種類として解釈されるを使用して、オプションの種類がクエリを通常の方法で照会できますので、`match`を持つ式`Some`と`None`です。 省略可能なパラメーターを使用して作成した関数ではなく、メンバーでのみ許可`let`バインドします。

関数を使用することもできます。 `defaultArg`、省略可能な引数の既定値を設定します。 `defaultArg`関数は、最初の引数と省略可能なパラメーターと、既定値、2 つ目として受け取ります。

次の例では、省略可能なパラメーターの使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

出力は次のとおりです。

```
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
```

## <a name="passing-by-reference"></a>参照を渡し
F# でサポートする、`byref`キーワードで、参照渡しでパラメーターを渡すことを指定します。 つまり、関数の実行後の値に変更が保持されます。 に対して指定した値、`byref`パラメーターを変更可能にする必要があります。 また、適切な種類の参照セルを渡すことができます。

関数から 1 つ以上の値を返す方法として発展 .NET 言語での参照渡しです。 F# では、この目的で組を返すまたは、変更可能な参照セルをパラメーターとして使用できます。 `byref` .NET ライブラリとの相互運用のパラメーターが提供される主にします。

次の例では、使用、`byref`キーワード。 参照セルをパラメーターとして使用するときにする必要があります名前付きの値として参照セルを作成して、パラメーターとして使用するは、追加だけでなく、`ref`演算子の最初の呼び出しに示すよう`Increment`次のコードにします。 参照セルを作成する基になる値のコピーを作成するための最初の呼び出しは一時的な値だけインクリメントします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3809.fs)]

戻り値として組を使用して格納できる`out`.NET ライブラリのメソッドのパラメーターです。 または、扱うことのできる、`out`パラメーターとして、`byref`パラメーター。 次のコード例では、両方の方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a>パラメーター配列
場合によっては異機種混在型のパラメーターの任意の数を取得する関数を定義する必要があります。 これは実用的ではないために使用できるすべての型のために可能なすべてのオーバー ロードされたメソッドを作成します。 .NET の実装では、パラメーター配列の機能によってこのようなメソッドのサポートを提供します。 任意の数のパラメーターでは、そのシグニチャに、パラメーター配列を受け取るメソッドを指定できます。 パラメーターは、配列に配置されています。 配列の要素の型では、関数に渡すことができるパラメーターの型を決定します。 場合は、パラメーター配列を定義する`System.Object`要素型として、クライアント コード値渡すことが任意の型。

F# で、パラメーター配列は、メソッドでのみ定義します。 スタンドアロン関数またはモジュールで定義されている関数では、それらを使用できません。

使用して、パラメーター配列を定義する、`ParamArray`属性。 `ParamArray`属性は、最後のパラメーターにのみ適用できます。

次のコードは、両方とを受け取り、パラメーター配列の種類の定義をパラメーター配列を受け取るメソッドが f# の .NET メソッドの呼び出しを示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

プロジェクト内で実行するときに、前のコードの出力のとおりです。

```
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a>関連項目
[メンバー](members/index.md)
