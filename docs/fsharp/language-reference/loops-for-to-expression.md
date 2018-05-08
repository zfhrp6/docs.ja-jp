---
title: 'ループ: for...to 式 (F#)'
description: 参照してくださいか f# データ型.. ループでループ変数の値の範囲を反復処理に式を使用します。
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
