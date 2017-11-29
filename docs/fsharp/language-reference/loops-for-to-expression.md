---
title: "ループ: for...to 式 (F#)"
description: "参照してくださいか f# データ型.. ループでループ変数の値の範囲を反復処理に式を使用します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a>ループ: for...to 式

`for...to`ループでループ変数の値の範囲を反復処理する式を使用します。


## <a name="syntax"></a>構文

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a>コメント
識別子の型がの型から推論されます、*開始*と*完了*式。 これらの式の型は、32 ビット整数値である必要があります。

式では技術的には、`for...to`命令型プログラミング言語では、従来のステートメントのようにします。 戻り値の型、*式本体*する必要があります`unit`です。 次の例では、さまざまな使用、`for...to`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

このコードの出力は、次のようになります。

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[ループ: `for...in` 式](loops-for-in-expression.md)

[ループ: `while...do` 式](loops-while-do-expression.md)
