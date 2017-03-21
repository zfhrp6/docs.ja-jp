---
title: "文字 (Visual Basic) を入力して |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6e112e7d221ef8e7a660094306bbb242c988e843
ms.lasthandoff: 03/13/2017

---
# <a name="type-characters-visual-basic"></a>型文字 (Visual Basic)
一部のプログラミング要素のデータ型を強制する宣言ステートメントでデータ型を指定することだけでなく、*文字を入力*します。 型の文字の任意の種類の要素の直後にする必要があります。  
  
 型文字は、要素の名前の一部ではありません。 型文字型の文字で定義された要素を参照できます。  
  
## <a name="identifier-type-characters"></a>識別子の型文字  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]セットを提供*識別子の型文字*、変数または定数のデータ型を指定する宣言で使用することができます。 次の表は、使用状況の例を含む使用可能な識別子の型文字を示します。  
  
|識別子の型文字|データ型|例|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 識別子の型文字が存在していない、 `Boolean`、 `Byte`、 `Char`、 `Date`、 `Object`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`データ型、または配列や構造体などの任意の複合データ型。  
  
 場合によっては、追加することができます、`$`に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]機能、たとえば`Left$`の代わりに`Left`、返される型の値を取得する`String`です。  
  
 すべての場合、識別子の型文字は、識別名の直後にする必要があります。  
  
## <a name="literal-type-characters"></a>リテラルの型文字  
 A*リテラル*データ型の特定の値のテキスト表現です。  
  
### <a name="default-literal-types"></a>既定のリテラル型  
 通常、コード内のリテラルの形式によってのデータ型が決まります。 次の表は、これらの既定の種類を示します。  
  
|リテラルのテキストの形式|既定のデータ型|例|  
|-----------------------------|-----------------------|-------------|  
|数値の小数部のない部分|`Integer`|`2147483647`|  
|数値いいえ小数部のある、に対して大きすぎます`Integer`|`Long`|`2147483648`|  
|数値、小数部の一部|`Double`|`1.2`|  
|二重引用符で囲まれました。|`String`|`"A"`|  
|シャープ記号で囲まれました。|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a>リテラル型の強制  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]セットを提供*リテラルの型文字*に、1 つ以外のデータ型の形式を強制的に使用できることを示します。 リテラルの末尾に文字を付加して行います。 次の表は、使用状況の例を含む使用可能なリテラルの型文字を示します。  
  
|リテラルの型文字|データ型|例|  
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
  
 リテラルの型文字が存在していない、 `Boolean`、 `Byte`、 `Date`、 `Object`、 `SByte`、または`String`データ型、または配列や構造体などの任意の複合データ型。  
  
 リテラルは識別子の型文字にも行えます (`%`、 `&`、 `@`、 `!`、 `#`、 `$`)、変数、定数、式を指定できます。 ただし、リテラルの型文字 (`S`、 `I`、 `L`、 `D`、 `F`、 `R`、 `C`) リテラルでのみ使用できます。  
  
 すべての場合、リテラルの型文字はリテラル値の直後にする必要があります。  
  
## <a name="hexadecimal-and-octal-literals"></a>8 進数および&16; 進数リテラル  
 コンパイラでは、整数リテラルを 10 進数 (基数 10) の数のシステムで通常として解釈します。 リテラルに整数を強制できます 16 進数 (基数 16)、`&H`プレフィックス、およびするは、8 進数 (基数 8) を使用する、`&O`プレフィックス。 続くプレフィックスの数字は、数のシステムに適切なである必要があります。 次の表を示します。  
  
|基数|プレフィックス|有効な文字|例|  
|-----------------|------------|------------------------|-------------|  
|16 進数 (基数 16)。|`&H`|0-9、A ~ F|`&HFFFF`|  
|8 進数 (基数 8)。|`&O`|0-7|`&O77`|  
  
 リテラルの型文字とプレフィックスの付いたリテラルを行うことができます。 次の例に示します。  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 前の例で`counter`-32768 の&10; 進数の値を持つと`flags`+32768 の&10; 進数の値を持つファイル。  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
