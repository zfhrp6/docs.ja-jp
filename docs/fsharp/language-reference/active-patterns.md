---
title: アクティブ パターン (F#)
description: アクティブ パターンを使用して、f# のプログラミング言語で入力データを分割する名前付きのパーティションを定義する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: b8c3270b1efbeb3495ac69bf1217fddf8a5a73e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="active-patterns"></a>アクティブ パターン

*アクティブ パターン*パターン一致式の判別共用体の場合と同様に、これらの名前を使用できるように、入力のデータを分割する名前付きパーティションを定義できるようにします。 アクティブ パターンを使用すると、パーティションごとにカスタマイズした方法でデータを分解できます。


## <a name="syntax"></a>構文

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a>コメント
前の構文では、識別子で表される入力データのパーティションの名*引数*、または、つまり、他の名前、引数のすべての値のセットのサブセットです。 アクティブ パターン定義では最大 7 つのパーティションを指定できます。 *式*データを分解するには、フォームをについて説明します。 アクティブ パターン定義を使用すると、判断するための名前付きのパーティションに属している引数として提供された値の規則を定義します。 (| と |) のシンボルをいいます*バナナ クリップ*この型の使用すると、バインディングによって作成された関数が呼び出されると、*アクティブ レコグナイザー*です。

たとえば、引数を指定して、次のアクティブなパターンを検討してください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

次の例のように、式と一致するパターンでは、アクティブ パターンを使用できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

このプログラムの出力は次のとおりです。

```
7 is odd
11 is odd
32 is even
```

アクティブ パターンの別の使用は、同じ基になるデータがさまざまな可能な表現が場合など、いくつかの方法でデータ型を分解するためです。 たとえば、 `Color` RGB 表現または HSB 表現にオブジェクトを分解する可能性があります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

上のプログラムの出力は次のとおりです。

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

組み合わせで、アクティブなパターンを使用してこれら 2 つの方法を有効にするパーティションにデータを適切なフォームだけに分解し、計算のため最も便利な形式で、適切なデータに対して適切な計算を実行します。

結果として得られるパターン一致式では、非常に判読できる、大幅に簡素化する可能性のある複雑な分岐構造やデータ分析のコードは、便利な方法で書き込むデータを有効にします。


## <a name="partial-active-patterns"></a>パーシャル アクティブ パターン
場合によっては、入力領域の一部だけを分割する必要があります。 その場合は、いくつかの入力に一致は他の入力が一致しなくなるの部分のパターンのセットを作成します。 常に、値を生成しないアクティブ パターンと呼びます*パーシャル アクティブ パターン*; オプションの種類である戻り値があります。 部分的なアクティブ パターンを定義するのには、バナナ クリップ内のパターンの一覧の最後にワイルドカード文字 (_) を使用します。 次のコードでは、部分的なアクティブ パターンの使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

前の例の出力は次のとおりです。

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

パーシャル アクティブ パターンを使用して、個々 の選択肢もあります不整合または相互に排他的なが必要はありません。 次の例では、パターン四角形パターン キューブのでとは、不整合のあるいくつかの番号は、四角形、64 などのキューブの両方です。 次のプログラムは、すべての整数が 1000000 までは、四角形およびキューブの両方を印刷します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

出力は次のとおりです。

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a>パラメーター化されたアクティブ パターン
アクティブ パターンが常に一致する項目の少なくとも 1 つの引数を受け取りますが、名前で同様に、追加の引数がかかる*パラメーター化されたアクティブ パターン*適用されます。 追加の引数には、一般的なパターンを特化することができるようにします。 たとえば、文字列を解析する多くの場合、正規表現を使用してアクティブ パターンが部分的なアクティブ パターンを使用する次のコードのように、余分なパラメーターとして、正規表現を含める`Integer`上記のコード例で定義されています。 この例では、[全般] である ParseRegex アクティブ パターンをカスタマイズするさまざまな日付形式の正規表現を使用する文字列が与えられます。 整数アクティブ パターンが一致した文字列を DateTime コンス トラクターに渡すことができる整数に変換するために使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

前のコードの出力は次のとおりです。

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

アクティブなパターンは、パターン一致式のみに限定することはありません、let バインディングで使用することもできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

前のコードの出力は次のとおりです。

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[match 式](match-expressions.md)

