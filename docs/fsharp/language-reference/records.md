---
title: "レコード (F#)"
description: "F# のレコードがオプションでメンバーの名前付きの値の単純な集計を表現する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3a3701ea-4308-4fa1-9b5c-b955c470f17a
ms.openlocfilehash: f5ade1db39431d99f10eb6967f02335123b83d34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="records"></a>レコード

レコードは、名前付きの値の単純な集合を表しており、オプションでメンバーを含みます。  4.1 以降では f#、構造体または参照型をか、設定できます。  これらは、既定では参照型です。

## <a name="syntax"></a>構文

```fsharp
[ attributes ]
type [accessibility-modifier] typename = {
    [ mutable ] label1 : type1;
    [ mutable ] label2 : type2;
    ...
}
    [ member-list ]
```

## <a name="remarks"></a>コメント
前の構文で*typename*レコードの種類の名前を指定*label1*と*label2*と呼ばれる値の名前は、*ラベル*、および*type1*と*type2*これらの値の種類を示します。 *メンバー リスト*省略可能な型のメンバーの一覧を示します。  使用することができます、`[<Struct>]`参照型であるレコードではなく、構造体レコードを作成する属性。

いくつかの例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1901.fs)]

各ラベルは、別々 の行には、セミコロンを省略できます。

呼ばれる式の値を設定することができます*式を記録*です。 コンパイラは、(、ラベルが十分に区別されるその他のレコードの種類の場合) を使用するラベルから型を推測します。 中かっこ ({}) は、レコード式を囲みます。 次のコードはラベルが付いた 3 つの浮動要素を持つレコードを初期化するレコード式`x`、`y`と`z`です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1907.fs)]

同じラベルも別の型がある場合は、短縮形を使わないでください。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1903.fs)]

最後に宣言された型のラベルの以前に宣言された型よりも優先前の例では`mypoint3D`と推論されます`Point3D`です。 次のコードのように、レコード型を明示的に指定することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1908.fs)]

メソッドは、クラス型と同様のレコードの種類に対して定義できます。

## <a name="creating-records-by-using-record-expressions"></a>レコード式を使用してレコードを作成します。
レコードで定義されているラベルを使用してレコードを初期化することができます。 これを行う式を呼びます、*式を記録*です。 中かっこを使用して、区切り記号としてセミコロンを使用してレコード式を囲みます。

次の例では、レコードを作成する方法を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1904.fs)]

レコード式では、型定義では、最後のフィールドの後のセミコロンは、1 行のすべてのフィールドがあるかどうかに関係なく、オプションです。

レコードを作成する場合は、各フィールドの値を指定する必要があります。 任意のフィールドの初期化式内の他のフィールドの値を参照することはできません。

次のコードの種類で`myRecord2`フィールドの名前から推測されます。 必要に応じて、型名を明示的に指定することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

レコードの構築の別の形式は、既存のレコードをコピーして、可能性のあるフィールドの値の一部を変更する必要がある場合に役に立ちます。 次のコード行を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

この形式のレコード式と呼ばれる、*コピーして更新するレコード式*です。

レコードは既定では変更できません。ただし、コピーと更新の式を使用して変更されたレコードを簡単に作成することができます。 変更可能なフィールドを明示的に指定できます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1909.fs)]

レコードのフィールドでは、DefaultValue 属性を使用しないでください。 既定値に初期化されるフィールドのレコードの既定のインスタンスを定義およびコピーを使用し、既定値と異なるフィールドを設定する式をレコードを更新することをお勧めします。

```fsharp
// Rather than use [<DefaultValue>], define a default record.
type MyRecord =
{
    field1 : int
    field2 : int
}

let defaultRecord1 = { field1 = 0; field2 = 0 }
let defaultRecord2 = { field1 = 1; field2 = 25 }

// Use the with keyword to populate only a few chosen fields
// and leave the rest with default values.
let rr3 = { defaultRecord1 with field2 = 42 }
```

## <a name="pattern-matching-with-records"></a>レコードを使用したパターン マッチ
レコードは、パターン マッチで使用できます。 いくつかのフィールドを明示的に指定し、一致が発生したときに割り当てられる他のフィールドの変数を設定できます。 これを次のコード例に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1910.fs)]

このコードによる出力は次のとおりです。

```
Point is at the origin.
Point is on the x-axis. Value is 100.000000.
Point is at (10.000000, 0.000000, -1.000000).
```

## <a name="differences-between-records-and-classes"></a>レコードおよびクラス間の相違点
レコードのフィールドとは異なり、クラスからプロパティとして自動的に公開されているし、それらが作成時に使用され、レコードのコピー。 レコードの作成は、クラスの構築からも異なります。 レコードの種類では、コンス トラクターを定義できません。 代わりに、このトピックで説明する構築構文が適用されます。 クラスは、コンス トラクターのパラメーター、フィールド、およびプロパティ間の直接の関係のあるありません。

共用体と構造体の型と同様には、レコードは、構造の等値セマンティクスを持ちます。 クラスは、参照を持つ等値セマンティクスです。 次のコード例を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1911.fs)]

クラスと同じコードを記述する場合、2 つのクラス オブジェクトしない場合は等しくためとアドレスのみを比較するように 2 つの値をヒープ上の 2 つのオブジェクトを表します (クラス型のオーバーライドしない限り、`System.Object.Equals`メソッド)。

レコードに等しいかどうかを参照する必要がある場合、属性を追加`[<ReferenceEquality>]`レコード上。

## <a name="see-also"></a>関連項目
[F# の型](fsharp-types.md)

[クラス](classes.md)

[F# 言語リファレンス](index.md)

[参照の等価性](https://msdn.microsoft.com/en-us/visualfsharpdocs/conceptual/core.referenceequalityattribute-class-%5bfsharp%5d)

[パターン一致](pattern-matching.md)
