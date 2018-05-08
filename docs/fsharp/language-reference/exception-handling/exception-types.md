---
title: 例外の種類 (F#)
description: 定義して、f# の例外の種類を使用する方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 4462dd00ddf9524d1fd376ee1e73e81fcfd5d945
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="exception-types"></a>例外の種類

F# の例外の 2 つのカテゴリがあります。 .NET の例外の種類と f# の例外の種類。 このトピックでは、定義して、f# の例外の種類を使用する方法について説明します。


## <a name="syntax"></a>構文

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a>コメント
前の構文で*例外型*新しい f# の例外の種類の名前を指定および*引数の型*この型の例外が発生するときに指定できる引数の型を表します。 タプル型を使用して複数の引数を指定することができます*引数の型*です。

F# の例外の一般的な定義には、次のようになります。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

使用してこの型の例外を生成することができます、`raise`関数は、次のようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

F# の例外の種類を使用するには、フィルター内で直接、`try...with`式では、次の例で示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

例外の種類で定義された、 `exception` f# のキーワードはから継承する新しい型`System.Exception`です。


## <a name="see-also"></a>関連項目
[例外処理](index.md)

[例外: `raise` 関数](the-raise-function.md)

[例外階層](https://msdn.microsoft.com/library/z4c5tckx.aspx)
