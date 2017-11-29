---
title: "例外の種類 (F#)"
description: "定義して、f# の例外の種類を使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e850205a-b8da-459e-8f6d-cb3510f8f173
ms.openlocfilehash: a0864218841396c0ebdf26c7585e0e5bb778f83e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
