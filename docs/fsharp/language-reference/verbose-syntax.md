---
title: 冗語構文 (F#)
description: F# のプログラミング言語の詳細および軽量構文の違いについて説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: fd040a66a789bc6717fd14e6a9f28274c9e3542b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="verbose-syntax"></a>冗語構文

2 つの形式の構文がある多くの構成要素、f# 言語で使用可能な:*冗語構文*と*軽量構文*です。 冗語構文では、一般的に使用されていなくても、インデントを受けにくくするという利点があります。 その他のキーワードと同様に、軽量構文が短いとインデントの先頭と末尾、コンス トラクターを使用ではなく`begin`、 `end`、`in`のようにします。 既定の構文は、軽量構文です。 このトピックは、軽量構文が有効でない場合に、f# の構成要素の構文を説明します。 冗語構文は、常に有効に、軽量構文を有効にした場合でも使用できるようにも冗語構文の一部の構造体。 使用して軽量構文を無効にすることができます、`#light "off"`ディレクティブです。


## <a name="table-of-constructs"></a>構成要素の表
次の表のコンテキストで、軽量と詳細な f# 言語構成要素の構文を示していますが、2 つの形式間の差がある場合。 この表で、山かっこ (&lt;&gt;) 構文のユーザーが指定した要素を囲みます。 さらに詳細な構文については、これらの構成要素内で使用される各言語構成要素のドキュメントを参照してください。



<table>
<tr>
<th>言語構成要素</th>
<th>軽量構文</th>
<th>冗語構文</th>
</tr>
<tr>
<td>
複合式
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


入れ子になった`let`バインド

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
コード ブロック
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
begin
    <expression1>;
    <expression2>;
end
```
</td>
</tr>
<tr><td>
`for...do`
</td><td>

```
for counter = start to finish do
    ...
```

</td><td>

```
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td>レコード
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>class
</td><td>
```
type <class-name>(<params>) = ... ```

</td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td>構造体</td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td>判別共用体</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end    
```

</td>
</tr>
<tr><td>interface</td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td>オブジェクト式</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td>インターフェイスの実装</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>型拡張機能</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td>name</td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>



## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)

[コンパイラ ディレクティブ](compiler-directives.md)

[コードのフォーマットに関するガイドライン](code-formatting-guidelines.md)
