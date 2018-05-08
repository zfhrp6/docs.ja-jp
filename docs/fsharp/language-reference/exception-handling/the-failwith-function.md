---
title: '例外: failwith 関数 (F#)'
description: "'Failwith' 関数が f# の例外を生成する方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: 59f7129faf38668dd7390790e22d25f37c129750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="exceptions-the-failwith-function"></a>例外: failwith 関数

`failwith`関数には、f# の例外が生成されます。


## <a name="syntax"></a>構文

```fsharp
failwith error-message-string
```

## <a name="remarks"></a>コメント
*エラー メッセージ文字列*リテラル文字列または型の値は、前の構文で`string`です。 なったら、`Message`例外のプロパティです。

によって生成される例外`failwith`は、`System.Exception`名前を持つ参照である例外`Failure`f# コードでします。 次のコードの使用例`failwith`は例外をスローします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6001.fs)]
    
## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外の種類](exception-types.md)

[例外: `try...with` 式](the-try-with-expression.md)

[例外: `try...finally` 式](the-try-finally-expression.md)

[例外: `raise` 関数](the-raise-function.md)
