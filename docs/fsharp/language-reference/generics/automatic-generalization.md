---
title: 自動ジェネリック化 (F#)
description: どの F# で自動的に一般化引数および関数の型が可能であれば、複数の型を操作できるように説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 858c8bab4a1a37f44a700744e70ebfa8a5abf12c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="automatic-generalization"></a>自動ジェネリック化

F# の関数よぶ式の種類を評価するのに型の推定を使用します。 このトピックでは、どの F# で自動的に一般化引数と型の関数の可能な限り、複数の型を動作させることについて説明します。


## <a name="automatic-generalization"></a>自動ジェネリック化
F# コンパイラ、関数の型の推論を実行するときに、指定されたパラメーターがジェネリックできるかどうかを判断します。 コンパイラは、各パラメーターを調べし、関数は、そのパラメーターの特定の種類に依存しているかどうかを決定します。 そうでない場合は、ジェネリックにする型が推論されます。

次のコード例は、ジェネリックにするに基づいてコンパイラが推定する関数を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

ある型を推論`'a -> 'a -> 'a`です。

種類は、同じの不明な型の 2 つの引数を受け取りを同じ型の値を返します関数であることを示します。 前の関数である理由のいずれかのジェネリックは、大きい-演算子よりも (`>`) 自体はジェネリックではします。 大きい-シグネチャを持つ演算子よりも`'a -> 'a -> bool`します。 ジェネリックではできない演算子もし、そのパラメーターの型を一般化することはできません、関数のコードでは、非ジェネリック関数または演算子と共にパラメーターの型を使用する場合。

`max`はジェネリックを使用できますの種類など`int`、`float`というように、次の例に示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

ただし、2 つの引数は、同じ種類のする必要があります。 署名が`'a -> 'a -> 'a`ではなく、`'a -> 'b -> 'a`です。 したがって、次のコードは、型が一致しないために、エラーを生成します。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max`使用することも、大きい値をサポートする任意の型の演算子よりもします。 そのため、使用することもに、文字列で、次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a>値制限
コンパイラは、明示的な引数を持ち、完全な関数定義でのみ、単純な変更できない値に自動ジェネリック化を実行します。

つまり、コンパイラ エラーが発生すると、特定の型であることを十分に制約を受けないがもない汎化可能なコードをコンパイルしようとする場合。 この問題は、エラー メッセージが値としての自動ジェネリック化では、この制限を指す、*値制限*です。

通常、ジェネリックにする構成要素、その場合、コンパイラが不十分な情報を一般化し、か、または意図せずに、非ジェネリック コンストラクトのための十分な種類の情報を省略した場合に、値制限エラーが発生します。 値制限エラーの解決策は、複数の完全で、次の方法のいずれかの型の推論の問題を制限する詳細な情報についてを提供することです。


- 値またはパラメーターに、明示的な型の注釈を追加することで非ジェネリックである型を制限します。

- 問題が使用されている場合、関数の合成など、または不完全なジェネリック関数を定義する、汎化できない構成コンストラクトに適用されるカリー化関数の引数を通常の関数定義として関数を書き直してください。

- 問題が複雑すぎるため、汎用化では式の場合は、なります関数に、未使用のパラメーターを追加することによってです。

- 明示的なジェネリック型パラメーターを追加します。 このオプションはほとんど使用されません。

- 次のコード例では、これらの各シナリオを示しています。

ケース 1: 式が複雑すぎます。 この例では、一覧で`counter`するものでは`int option ref`、単純な変更できない値が定義されていませんが、します。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

ケース 2: では、汎化できない構成要素を使用して、ジェネリック関数を定義します。 この例では、構造は、関数の引数の部分的な適用が伴うので汎化できない構成がします。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

ケース 3: は、未使用のパラメーターを追加します。 この式が汎化のほど単純でないため、コンパイラは、値の制限のエラーを発行します。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

ケース 4: 型パラメーターを追加します。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

最後の場合、値には型関数の場合、次のようになど多くのさまざまな種類の値を作成するために使用できるようになります。

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>関連項目
[型推論](../type-inference.md)

[ジェネリック](index.md)

[静的に解決される型パラメーター](statically-resolved-type-parameters.md)

[制約](constraints.md)

