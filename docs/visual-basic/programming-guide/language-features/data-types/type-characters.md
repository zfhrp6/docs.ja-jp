---
title: "型文字 (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: 20a9a30689fb62a6956987b06470e76eeb42ebab
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="type-characters-visual-basic"></a>文字 (Visual Basic)

を、宣言ステートメントでのデータ型を指定するだけでなくでプログラミング要素のデータ型を強制することができます、*文字入力*です。 型文字間にある任意の種類の文字を含まない、要素の直後にする必要があります。

型文字は、要素の名前の一部ではありません。 型文字を使用せず、型文字で定義された要素を参照できます。

## <a name="identifier-type-characters"></a>識別子の型文字

Visual Basic のセットを提供する*識別子の型文字*変数または定数のデータ型を指定する宣言で使用できます。 次の表は、使用状況の例で使用できる識別子の型文字を示します。
  
|識別子の型文字|データの種類|例|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 識別子の型文字が存在しない、 `Boolean`、 `Byte`、 `Char`、 `Date`、 `Object`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`データ型、またはのいずれか配列や構造体などの複合データ型。

場合によっては、追加することができます、 `$` Visual Basic の関数では、たとえば文字`Left$`の代わりに`Left`、返される型の値を取得する`String`です。

すべての場合、識別子の型文字は、識別子名の直後にする必要があります。

## <a name="literal-type-characters"></a>リテラルの型文字

A*リテラル*データ型の特定の値のテキスト表現です。  

### <a name="default-literal-types"></a>既定のリテラル型

リテラルの形式、コードに通常表示されるデータ型を決定します。 次の表は、これらの既定値の型を示します。  
  
|リテラルのテキストの形式|既定のデータ型|例|  
|-----------------------------|-----------------------|-------------|  
|数値いいえ小数部のあります。|`Integer`|`2147483647`|  
|数値いいえ小数部のある、に対して大きすぎます `Integer`|`Long`|`2147483648`|  
|数値、小数部の一部|`Double`|`1.2`|  
|二重引用符で囲まれました。|`String`|`"A"`|  
|番号記号で囲まれました。|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>リテラル型の強制

Visual Basic のセットを提供する*リテラルの型文字*、もの以外のデータ型にそのフォームを想定するリテラルを強制的に使用できることを示します。 リテラルの末尾に文字を追加して行います。 次の表は、使用状況の例で使用可能なリテラルの型文字を示します。
  
|リテラルの型文字|データの種類|例|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

リテラルの型文字が存在しない、 `Boolean`、 `Byte`、 `Date`、 `Object`、 `SByte`、または`String`データ型、または配列や構造体などの任意の複合データ型。

リテラルには、識別子の型文字が使用してもできます (`%`、 `&`、 `@`、 `!`、 `#`、 `$`)、変数、定数、および式のことができます。 ただし、リテラルの型文字 (`S`、 `I`、 `L`、 `D`、 `F`、 `R`、 `C`) リテラルでのみ使用できます。

すべての場合、リテラルの型文字は、リテラル値の直後にする必要があります。

## <a name="hexadecimal-binary-and-octal-literals"></a>16 進数、バイナリ、および 8 進数リテラル

コンパイラは、通常、10 進数 (基数 10) 番号システム内にある整数リテラルを解釈します。 16 進数 (基数 16) を付けて、整数リテラルを定義することも、 `&H` (基本 2 進数値で、プレフィックス、`&B`プレフィックス、および 8 進数 (基本 8) として番号、`&O`プレフィックス。 プレフィックスに続く数字を数値システムに適したにする必要があります。 次の表を示します。  
  
|基本の数|プレフィックス|有効桁の値|例|
|-----------------|------------|------------------------|-------------|
|16 進数 (基数 16)。|`&H`|0 ~ 9 および A ~ F|`&HFFFF`|
|バイナリ (基本 2)|`&B`|0-1|`&B01111100`|
|8 進数 (基数 8)。|`&O`|0-7|`&O77`|

Visual Basic 2017 以降、アンダー スコア文字を使用することができます (`_`) 整数リテラルの読みやすさを強化するために桁区切り記号として。 次の例では、`_`バイナリ リテラルを 8 ビットのグループにグループ化する文字。

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

リテラルの型文字を持つプレフィックスが指定されたリテラルに従うことができます。 この例を次に示します。

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

前の例では、 `counter` -32768 の 10 進値を持つと`flags`+32768 の 10 進値を持つファイルです。

Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。 例:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>参照

 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
