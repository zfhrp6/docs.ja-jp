---
title: 'ループ: for...in 式 (F#)'
description: 参照してくださいか f# データ型.. 式でコンス トラクターをループが使用される列挙可能なコレクション内のパターンの一致を繰り返し処理します。
ms.date: 05/16/2016
ms.openlocfilehash: 926f0a9940021b3dc0deefc12ea158c35975e949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="loops-forin-expression"></a>ループ: for...in 式

このループ構造は、範囲式、シーケンス、リスト、配列、または列挙型をサポートするその他の構造体などの列挙可能なコレクション内のパターンの一致を反復処理に使用されます。


## <a name="syntax"></a>構文

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a>コメント
`for...in`式と比較すること、`for each`の他の .NET 言語のステートメントをループ列挙可能なコレクション内の値に使用されているためです。 ただし、`for...in`も全体のコレクションを反復処理だけではなくコレクションに対する一致するパターンをサポートします。

列挙可能なコレクションとして、またはを使用して、列挙可能な式を指定することができます、`..`演算子、整数型の範囲とします。 列挙可能なコレクションには、リスト、シーケンス、配列、セット、マップ、およびなどが含まれます。 実装する任意の型`System.Collections.IEnumerable`使用できます。

使用して範囲を表現するときに、`..`演算子を次の構文を使用することができます。

*開始*. *[完了] します。*

呼ばれるインクリメントを含むバージョンを使用することができます、*スキップ*次のコードのように、します。

*開始*. *スキップ*. *[完了] します。*

パターンとして整数の範囲と単純なカウンター変数を使用すると通常の動作をイテレーションごとに 1 つのカウンター変数をインクリメントするが、カウンターが代わりにインクリメント skip 値で範囲には、skip 値が含まれている場合。

パターンに一致した値は、式の本体でも使用できます。

コード例を次の例を示します、`for...in`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

出力は次のとおりです。

```
1
5
100
450
788
```

次の例では、単純な変数ではなくタプル パターンを使用する方法とシーケンス、ループする方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

出力は次のとおりです。

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

次の例では、単純な整数の範囲内でループする方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

Function1 の出力は次のとおりです。

```
1 2 3 4 5 6 7 8 9 10
```

次の例では、ループ、範囲を範囲の他のすべての要素が含まれている 2 のスキップを使用する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

出力`function2`のとおりです。

```
1 3 5 7 9
```

次の例では、文字の範囲を使用する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

出力`function3`のとおりです。

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

次の例では、負の値のスキップ値逆順イテレーションを使用する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

出力`function4`のとおりです。

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

先頭と範囲の終了には、次のコードのように、関数など、式ことができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

出力`function5`この入力には、次のようにします。

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

次の例は、ループ内に要素が不要な場合に、ワイルドカード文字 (_) の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

出力は次のとおりです。

```
Number of elements in list1: 5
```

`Note` 使用することができます`for...in`シーケンス式およびその他の計算式で、カスタマイズされたバージョンの場合、`for...in`式を使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)です。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[ループ: `for...to` 式](loops-for-to-expression.md)

[ループ: `while...do` 式](loops-while-do-expression.md)
