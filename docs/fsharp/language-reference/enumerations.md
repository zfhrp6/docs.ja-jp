---
title: 列挙型 (F#)
description: F# でリテラルの代わりに列挙体を使用して読みやすく、保守が容易なコードを作成する方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4b1a61fb69403f826733893667e55991d39867c6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="enumerations"></a>列挙

*列挙体*とも呼ばれる、*列挙型*、およびとも整数型の値のサブセットにラベルが割り当てられている場所です。 リテラルの代わりに使用すると、コードの読み取りおよび保守が容易になります。


## <a name="syntax"></a>構文

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>コメント
列挙体ように見えるを単純な値を持つ判別共用体が、値を指定することができます。 通常、値は、0 または 1 から始まる整数またはビット位置を表す整数です。 列挙する場合はビットの位置を表す、使用する必要も、[フラグ](xref:System.FlagsAttribute)属性。

列挙体の基になる型は、たとえばを使用できるようにリテラル、サフィックスを持つなど、使用されるリテラルから決定されます`1u`、`2u`などの符号なし整数の (`uint32`) 型です。

名前付きの値を参照するときにする必要がありますとして使用する列挙型自体の名前、修飾子は、`enum-name.value1`だけでなく、`value1`です。 この動作は、判別共用体の動作とは異なります。 これは、常に列挙型であるため、 [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15)属性。

次のコードは、宣言と列挙型の使用方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

適切な演算子を使用して基になる型は、次のコードに示すように、列挙型を変換できます簡単にします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

列挙型には、次の基になる型の 1 つ持つことができます: `sbyte`、 `byte`、 `int16`、 `uint16`、 `int32`、 `uint32`、 `int64`、 `uint16`、 `uint64`、および`char`です。 列挙型は、.NET framework から継承されている型として表される`System.Enum`、さらにから継承される`System.ValueType`です。 したがって、インライン親オブジェクトで、スタックに配置されている値型では、基になる型の任意の値が列挙体の有効な値。 これは重要なパターン マッチ列挙体に数値を使用するときに、名前のない値をキャッチするパターンを指定する必要があるためです。

`enum`関数 f# ライブラリで使用できます、定義済みの 1 つ以外の値も、列挙値を生成する名前付きの値。 使用する、`enum`次のように機能します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

既定値`enum`関数は型で機能`int32`します。 そのため、基になるその他の型を持つ列挙型と共に使用できません。 代わりに、次を使用します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[キャストと変換](casting-and-conversions.md)
