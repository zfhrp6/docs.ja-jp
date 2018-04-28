---
title: '例外: invalidArg 関数 (F#)'
description: F# 'invalidArg' 関数は引数の例外を生成する方法について説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.assetid: d375b704-6b27-493e-bd1d-ee217a53c4b5
ms.openlocfilehash: fc7b1d25adf71bc1704a3f2db4359006f0ba1670
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-invalidarg-function"></a>例外: invalidArg 関数

`invalidArg`関数に引数例外が生成されます。


## <a name="syntax"></a>構文

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>コメント
前の構文でパラメーター名は、引数が正しくないパラメーターの名前を持つ文字列です。 *エラー メッセージ文字列*リテラル文字列または型の値は、`string`です。 なったら、`Message`例外オブジェクトのプロパティです。

によって生成された例外`invalidArg`は、`System.ArgumentException`例外。 次のコードの使用例`invalidArg`は例外をスローします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

出力は次のように (非表示)、スタック トレースでの後にします。

```
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外の種類](exception-types.md)

[例外: `try...with` 式](the-try-with-expression.md)

[例外: `try...finally` 式](the-try-finally-expression.md)

[例外: `raise` 関数](the-raise-function.md)

[例外: `failwith` 関数](the-failwith-function.md)
