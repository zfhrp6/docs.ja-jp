---
title: インデックス付きプロパティ (F#)
description: F# でインデックス付きのプロパティは順序付けされたデータを配列に似たアクセスを提供するプロパティについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 503cef9693cfe5e13d4e2d19a721d65bff1ce749
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235942"
---
# <a name="indexed-properties"></a>インデックス付きプロパティ

*インデックス付きプロパティ*を配列に似たアクセスを提供するプロパティ値に基づいて並べ替えられるデータ。 これらは 3 つの形式があります。

* `Item`
* `Ordinal`
* `Cardinal`

F# のメンバーは、これら 3 つの配列に似たアクセスを提供する名前のいずれかの名前をする必要があります。 `IndexerName` 次の 3 つのオプションのいずれかを表すために使用します。


## <a name="syntax"></a>構文

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a>コメント
前の構文のフォームは、両方があるインデックス付きプロパティを定義する方法を示して、`get`と`set`メソッドが、`get`メソッドのみかが、`set`メソッドのみです。 両方のみ get および set のみに示される構文に示される構文を結合し、get および set の両方を持つプロパティを生成できます。 この後者の形式を使用すると、get で異なるアクセシビリティ修飾子と属性を配置して、メソッドを設定できます。

ときに、 *IndexerName*は`Item`コンパイラは、既定のインデックス付きプロパティとしてプロパティを扱います。 A*インデックス付きプロパティの既定*オブジェクト インスタンスの配列に似た構文を使用してアクセスできるプロパティです。 たとえば場合、`obj`構文は、このプロパティを定義する型のオブジェクトである`obj.[index]`プロパティにアクセスするために使用します。

既定以外のインデックス付きプロパティへのアクセスの構文では、プロパティ、かっこ内のインデックスの名前を指定します。 たとえば、次のプロパティが`Ordinal`、記述する`obj.Ordinal(index)`へのアクセスします。

使用する形式に関係なくのカリー化された形式を使用する必要があります常に、`set`インデックス付きプロパティのメソッドです。 カリー化関数については、次を参照してください。[関数](../functions/index.md)です。

## <a name="example"></a>例

次のコード例は、定義と使用の既定値と既定以外のインデックス付きプロパティ get し、set メソッドを示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a>出力

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a>複数のインデックス変数でインデックス付きプロパティ
インデックス付きプロパティには、1 つ以上のインデックス変数を持つことができます。 その場合は、プロパティを使用する場合に、変数はコンマで区切られます。 このようなプロパティの set メソッド、最初は、キーを含むタプル、2 番目の値が設定されている 2 つのカリー化された引数が必要です。

次のコードでは、複数のインデックス変数でインデックス付きプロパティの使用を示します。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a>関連項目
[メンバー](index.md)
