---
title: 型略称 (F#)
description: F# 型の省略形型に名前を付けるより意味のあるコードを読みやすくためにについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="type-abbreviations"></a>型略称

A*型略称*エイリアスまたは型の代替名です。

## <a name="syntax"></a>構文

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>コメント
型の省略形を使用すると、コードを読みやすくために、型、わかりやすい名前を付けます。 種類が書き込みに面倒なを使いやすい名を作成するのにも使用できます。さらに、型を使用するすべてのコードを変更しなくても、基になる型を変更しやすく型の省略形を使用することができます。 単純型の省略形を次に示します。

型の省略形のユーザー補助機能が既定で`public`です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

型の省略形は、次のコードのように、ジェネリック パラメーターを含めることができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

前のコードで`Transform`を任意の型の 1 つの引数を受け取る関数を表す型の省略形は、同じ型の 1 つの値を返します。

型の省略形は、.NET Framework の MSIL コードでは保持されません。 したがって、f# アセンブリ別の .NET Framework 言語からを使用する場合は、型の省略形の基になる種類の名前を使用する必要があります。

型の省略形は、測定単位でも使用できます。 詳細については、次を参照してください。[単位](units-of-measure.md)です。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

