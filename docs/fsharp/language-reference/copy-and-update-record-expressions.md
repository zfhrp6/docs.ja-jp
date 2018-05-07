---
title: コピーして更新するレコード式 (f#)
description: "'コピーと更新レコード式' 既存のレコードを更新プログラムをコピーするフィールドを指定および更新されたレコードを返しますを記述する方法を説明します。"
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 000746b6e76349ae6d8f338519a58034f4e29020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
