---
title: "リテラル (F#)"
description: "F# のプログラミング言語でリテラルの型について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a>リテラル

> [!NOTE]
この記事の API の参照リンクを移動して msdn (現在のところ)。

このトピックでは、F# でリテラルの型を指定する方法を示す表を示します。

## <a name="literal-types"></a>リテラル型
F# のリテラル型を次の表に示します。 16 進表記で桁を表す文字は、大文字と小文字を区別しません。型を識別する文字は、大文字と小文字を区別します。

|型|説明|サフィックスまたはプリフィックス|例|
|----|-----------|----------------|--------|
|sbyte|符号付き 8 ビット整数|Y|`86y`<br /><br />`0b00000101y`|
|byte|符号なし 8 ビット自然数|uy|`86uy`<br /><br />`0b00000101uy`|
|int16|16 ビット符号付き整数|s|`86s`|
|uint16|符号なし 16 ビット自然数|us|`86us`|
|int<br /><br />int32|32 ビット符号付き整数|l または none|`86`<br /><br />`86l`|
|uint<br /><br />uint32|符号なし 32 ビット自然数|u または ul|`86u`<br /><br />`86ul`|
|unativeint|符号なし自然数としてのネイティブ ポインター|un|`0x00002D3Fun`|
|int64|64 ビット符号付き整数|L|`86L`|
|uint64|符号なし 64 ビット自然数|UL|`86UL`|
|single、float32|32 ビット浮動小数点数|F または f|`4.14F` または `4.14f`|
|||lf|`0x00000000lf`|
|float、double|64 ビット浮動小数点数|none|`4.14` または `2.3E+32` または `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|64 ビット表現に制限されない整数|I|`9999999999999999999999999999I`|
|decimal|固定小数点数または有理数として表現される小数|M または m|`0.7833M` または `0.7833m`|
|Char|Unicode 文字|none|`'a'`|
|文字列型|Unicode 文字列|none|`"text\n"`<br /><br />または<br /><br />`@"c:\filename"`<br /><br />または<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />または<br /><br />`"string1" + "string2"`<br /><br />関連項目[文字列](Strings.md)です。|
|byte|ASCII 文字|B|`'a'B`|
|byte[]|ASCII 文字列|B|`"text"B`|
|String または byte[]|逐語的文字列|@ プリフィックス|`@"\\server\share"`(Unicode)<br /><br />`@"\\server\share"B`(ASCII)|

## <a name="remarks"></a>コメント
Unicode 文字列を使用して指定できる明示的なエンコーディングを含めることができる`\u`後に 16 ビットの 16 進数コードまたは utf-32 エンコーディングを使用して指定できる`\U`Unicode を表す 32 ビットの 16 進数コードを続けてサロゲート ペア。

F# 3.1 で使用することができます、`+`文字列リテラルを結合にサインインします。 使用することも、ビットごとまたは (`|||`) 列挙型フラグを結合する演算子です。 たとえば、F# 3.1 では次のようなコードが有効です。

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

その他のビットごとの演算子は使用できません。


## <a name="named-literals"></a>名前付きリテラル
マークできるの定数にするのには、値、[リテラル](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285)属性。 この属性には、値が定数としてコンパイルされる効果があります。

パターン マッチ式では、小文字で始まる識別子は、リテラルとしてではなく常にバインドされる変数として扱われます。そのため、一般的に、リテラルを定義する場合は先頭大文字を使用する必要があります。

## <a name="integers-in-other-bases"></a>その他の基底の整数

16 進数、8 進数、またはバイナリを使用して 32 ビット符号付き整数を指定することも、 `0x`、`0o`または`0b`それぞれプレフィックスします。

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>数値リテラルにアンダー スコア

4.1 以降では F# を区切ることができます桁の数字、アンダー スコア文字 (`_`)。

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a>関連項目

[Core.LiteralAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
