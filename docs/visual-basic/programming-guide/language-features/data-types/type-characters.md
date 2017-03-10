---
title: "Type Characters (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "&H prefix for hexadecimal values"
  - "hexadecimal literals"
  - "F literal type character"
  - "& identifier type character"
  - "type characters"
  - "octal literals"
  - "literals, hexadecimal"
  - "&O prefix for octal values"
  - "literals, default types"
  - "defaults, literal types"
  - "C literal type character"
  - "type characters, literal"
  - "$ identifier type character"
  - "L literal type character"
  - "UI literal type characters"
  - "default literal types"
  - "D literal type character"
  - "literals, octal"
  - "S literal type character"
  - "! identifier type character"
  - "US literal type characters"
  - "% identifier type character"
  - "data types [Visual Basic], type characters"
  - "characters, identifier type"
  - "type characters, identifier"
  - "# identifier type character"
  - "identifier type characters"
  - "literal type characters"
  - "I literal type character"
  - "R literal type character"
  - "@ identifier type character"
  - "UL literal type characters"
  - "literal types, default"
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Type Characters (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言ステートメントでデータ型を指定するだけでなく、*型文字*を使用してプログラミング要素のデータ型を強制的に指定することもできます。  型文字は要素の直後に指定する必要があります。間にはどのような文字も指定しないでください。  
  
 型文字は要素名には含まれません。  型文字を使用して定義した要素を参照するときには、型文字を省略できます。  
  
## 識別子の型文字  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には*識別子の型文字*が用意されています。それらの型文字は、宣言で変数または定数のデータ型を指定するために使用できます。  次の表は、使用できる識別子の型文字とその使用例を示しています。  
  
|識別子の型文字|データ型|例|  
|-------------|----------|-------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 `Boolean`、`Byte`、`Char`、`Date`、`Object`、`SByte`、`Short`、`UInteger`、`ULong`、および `UShort` の各データ型や、配列、構造体などの複合データ型に対応する識別子の型文字はありません。  
  
 場合によっては、`$` 文字を [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の関数に追加することもできます。たとえば、`Left` ではなく `Left$` を使用すると、`String` 型の戻り値を取得できます。  
  
 いずれの場合でも、識別子の型文字は識別子名の直後に指定する必要があります。  
  
## リテラルの型文字  
 *リテラル*は、何らかのデータ型の特定の値のテキスト表現です。  
  
### 既定のリテラル型  
 通常、コード内のリテラルの形式によってその値のデータ型が決まります。  それらの既定の型を次に示します。  
  
|リテラルのテキスト形式|既定のデータ型|例|  
|-----------------|-------------|-------|  
|小数部のない数値|`Integer`|`2147483647`|  
|小数部がなく、`Integer` 型で表すには大きすぎる数値|`Long`|`2147483648`|  
|小数部のある数値|`Double`|`1.2`|  
|二重引用符で囲む|`String`|`"A"`|  
|シャープ記号で囲まれたリテラル|`Date`|`#5/17/1993 9:32 AM#`|  
  
### 強制的なリテラル型  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、*リテラルの型文字*が用意されています。それらの型文字は、リテラルに対して、そのリテラル形式が示す以外のデータ型を指定するために使用できます。  このためには、リテラルの型文字をリテラルの最後に付けます。  次の表は、使用できるリテラルの型文字とその使用例を示しています。  
  
|リテラルの型文字|データ型|例|  
|--------------|----------|-------|  
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
  
 `Boolean`、`Byte`、`Date`、`Object`、`SByte`、および `String` の各データ型や、配列、構造体などの複合データ型に対応するリテラルの型文字はありません。  
  
 また、変数、定数、および式に使用する場合と同様に、リテラルにも識別子の型文字 \(`%`、`&`、`@`、`!`、`#`、`$`\) を使用できます。  ただし、リテラルの型文字 \(`S`、`I`、`L`、`D`、`F`、`R`、`C`\) はリテラルにしか使用できません。  
  
 いずれの場合でも、リテラルの型文字はリテラル値の直後に指定する必要があります。  
  
## 16 進数および 8 進数リテラル  
 通常、コンパイラは、整数リテラルを 10 進数 \(基数 10\) として解釈します。  整数リテラルにプレフィックス `&H` を付けると、強制的に 16 進数 \(基数 16\) として解釈します。また、プレフィックス `&O` を付けると、8 進数 \(基数 8\) として解釈します。  プレフィックスの後には、該当する記数法に従った文字で値を記述する必要があります。  たとえば、次のように表されます。  
  
|基数|プレフィックス|有効な文字|例|  
|--------|-------------|-----------|-------|  
|16 進数 \(基数 16\)。|`&H`|0\-9 および A\-F|`&HFFFF`|  
|8 進数 \(基数 8\)。|`&O`|0\-7|`&O77`|  
  
 プレフィックスを付けたリテラルの後には、リテラルの型文字を続けることができます。  次に例を示します。  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 上の例では、`counter` には 10 進数の \-32768 が設定され、`flags` には 10 進数の \+32768 が設定されます。  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)