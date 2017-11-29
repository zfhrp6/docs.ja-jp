---
title: "match 式 (F#)"
description: "F# 一致式が式のパターンのセットとの比較に基づいている分岐のコントロールがどのように提供する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8854b713-255a-408d-942a-e80ab52fd2a4
ms.openlocfilehash: c8b9be744cfa7bc76f0d663b12abd66f8757fc56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="match-expressions"></a>match 式

`match`式が式のパターンのセットとの比較に基づいている分岐のコントロールを提供します。

## <a name="syntax"></a>構文

```fsharp
// Match expression.
match test-expression with
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...

// Pattern matching function.
function
| pattern1 [ when condition ] -> result-expression1
| pattern2 [ when condition ] -> result-expression2
| ...
```

## <a name="remarks"></a>コメント

パターン一致式では、複雑なパターンのセットとテスト式の比較に基づく、分岐できます。 `match` 、式、*テスト式*、逆を使用して、対応する一致が見つかったが、各パターンと比較*結果式*が評価されると、結果として得られる値は一致する式の値として返されます。

パターン一致の前の構文に示す関数は、ラムダ式、パターン マッチが行わ直ちに引数です。 パターン一致の前の構文に示す関数は、次のと同じです。

```fsharp
fun arg ->
    match arg with
    | pattern1 [ when condition ] -> result-expression1
    | pattern2 [ when condition ] -> result-expression2
    | ...
```    

ラムダ式の詳細については、次を参照してください。[ラムダ式:、`fun`キーワード](functions/lambda-expressions-the-fun-keyword.md)です。

パターンのセット全体では、入力変数のすべての一致候補を取り扱う必要があります。 ワイルドカード パターンを使用する多くの場合、(`_`)、以前に一致しない入力の値に一致する最後のパターンとして。

次のコードを示すための方法の一部、`match`式を使用します。 参照と使用できるすべての可能なパターンの例では、次を参照してください。[パターン マッチ](pattern-matching.md)です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4601.fs)]

## <a name="guards-on-patterns"></a>パターンのガード

使用することができます、`when`句をパターンに一致する変数が満たす必要がある追加の条件を指定します。 このような句と呼ばれます、*ガード*です。 式以下、`when`そのガードに関連付けられているパターンに一致するものが加えられる場合を除き、キーワードは評価されません。

次の例では、変数パターンの数値の範囲を指定する保護の使用を示します。 ブール演算子を使用して複数の条件を組み合わせることに注意してください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4602.fs)]

リテラル以外の値は、パターンでは使用できません、ためにを付けることに注意してください、`when`句の値に対する入力の一部を比較する必要がある場合に指定します。 これを次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4603.fs)]

## <a name="see-also"></a>関連項目

[F# 言語リファレンス](index.md)

[アクティブ パターン](active-patterns.md)

[パターン一致](pattern-matching.md)
