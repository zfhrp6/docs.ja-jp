---
title: "コピーして更新するレコード式 (f#)"
description: "'コピーと更新レコード式' 既存のレコードを更新プログラムをコピーするフィールドを指定および更新されたレコードを返しますを記述する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a>レコード式のコピーと更新

A*コピーして更新するレコード式*を既存のレコードをコピーし、指定したフィールドを更新、更新されたレコードを返します。 式を指定します。


## <a name="syntax"></a>構文

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>コメント
レコードは可能な既存のレコードに更新プログラムがないように、既定では、変更できません。 更新されたレコードのレコードのすべてのフィールドを作成するのには、もう一度指定する必要があります。 このタスクを簡略化する、*コピーして更新するレコード式*使用できます。 この式は、既存のレコードを受け取り、式から指定されたフィールドと、式で指定された存在しないフィールドを使用して、同じ種類の新しい 1 つを作成します。
これは、既存のレコードをコピーし、可能性のあるフィールドの値の一部を変更する必要がある場合に役立ちます。

新しく作成されたレコードのインスタンス。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

使用することがそのレコードのフィールドでのみ更新する場合は、*コピーして更新するレコード式*次と同様に。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>関連項目
[レコード](records.md)

[F# 言語リファレンス](index.md)
