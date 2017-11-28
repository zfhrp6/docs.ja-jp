---
title: "型略称 (F#)"
description: "F# 型の省略形型に名前を付けるより意味のあるコードを読みやすくためにについて説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 560af74f-935f-415c-af56-604cddb9da6b
ms.openlocfilehash: 235c0240fe89d203b9474dec2b3f91947f453cd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="type-abbreviations"></a>型略称

A*型略称*エイリアスまたは型の代替名です。

## <a name="syntax"></a>構文

```fsharp
type type-abbreviation = type-name
```

## <a name="remarks"></a>コメント
型の省略形を使用すると、コードを読みやすくために、型、わかりやすい名前を付けます。 種類が書き込みに面倒なを使いやすい名を作成するのにも使用できます。さらに、型を使用するすべてのコードを変更しなくても、基になる型を変更しやすく型の省略形を使用することができます。 単純型の省略形を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

型の省略形は、次のコードのように、ジェネリック パラメーターを含めることができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

前のコードで`Transform`を任意の型の 1 つの引数を受け取る関数を表す型の省略形は、同じ型の 1 つの値を返します。

型の省略形は、.NET Framework の MSIL コードでは保持されません。 したがって、f# アセンブリ別の .NET Framework 言語からを使用する場合は、型の省略形の基になる種類の名前を使用する必要があります。

型の省略形は、測定単位でも使用できます。 詳細については、次を参照してください。[単位](units-of-measure.md)です。


## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

