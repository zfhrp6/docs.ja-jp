---
title: "ループ: while...do 式 (F#)"
description: "参照してください方法、while... は式が指定されたテスト条件が true の間に反復的な実行 (ループ) を実行するために使用します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loops-whiledo-expression"></a>ループ: while...do 式

`while...do`式を使用して、指定されたテスト条件が true の間に反復的な実行 (ループ) を実行します。


## <a name="syntax"></a>構文

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>コメント
*テスト式*が評価されます。 ある場合`true`、*式本体*を実行し、もう一度テスト式が評価されます。 *式本体*型である必要があります`unit`です。 場合テスト式`false`イテレーションが終了します。

次の例では、使用、`while...do`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

上記のコードの出力は、1 ~ 20、ランダムな数値のうち、最後は 10 ストリームです。

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
使用することができます`while...do`シーケンス式およびその他の計算式で、カスタマイズされたバージョンの場合、`while...do`式を使用します。 詳細については、次を参照してください。[シーケンス](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、および[コンピュテーション式](computation-expressions.md)です。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[ループ: `for...in` 式](loops-for-in-expression.md)

[ループ: `for...to` 式](loops-for-to-expression.md)
