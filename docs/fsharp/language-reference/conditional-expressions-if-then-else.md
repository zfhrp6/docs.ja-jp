---
title: "条件式: if... then...else (F#)"
description: "コードの別の分岐を実行するのには、f# で条件付きの式を記述する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a>条件式:`if...then...else`

`if...then...else`式は、コードの別の分岐を実行し、別の値によって指定されるブール式を評価することもできます。


## <a name="syntax"></a>構文

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a>コメント
前の構文で*expression1*ブール式を評価するときに実行`true`、それ以外の*expression2*を実行します。

異なり、他の言語で、`if...then...else`構造は式、ステートメントではなくです。 つまりを実行する分岐の最後の式の値には、値が生成されます。 各分岐で生成される値の型が一致する必要があります。 明示的ながある場合`else`分岐では、そのタイプが`unit`です。 したがって場合の種類、`then`分岐以外の任意の型は、 `unit`、必要があります、`else`分岐と同じ戻り値の型。 チェーンと`if...then...else`式のキーワードを使用することができます、併せて`elif`の代わりに`else if`; それらが等しい。

## <a name="example"></a>例
次の例を使用する方法を示しています、`if...then...else`式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

