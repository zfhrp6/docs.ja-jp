---
title: "Data Types of Operator Results (Visual Basic) | Microsoft Docs"
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
  - "data types [Visual Basic], operator result data types"
  - "result data types"
  - "operator result data types"
  - "operators [Visual Basic], data types"
  - "data types [Visual Basic], ranges"
  - "operators [Visual Basic], result data types"
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Data Types of Operator Results (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、オペランドのデータ型を基に、演算結果のデータ型を確認します。  これは、いずれかのオペランドよりも広い範囲を持つデータ型である可能性もあります。  
  
## データ型の範囲  
 次に、対象となるデータ型の範囲を小さいものから順に示します。  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md): 2 種類の値  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md): 256 種類の整数値  
  
-   [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md): 65,536 \(6.5...E\+4\) 種類の整数値  
  
-   [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md): 4,294,967,296 \(4.2...E\+9\) 種類の整数値  
  
-   [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md): 18,446,744,073,709,551,615 \(1.8...E\+19\) 種類の整数値  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md): 1.5...E\+29 種類の整数値、最大範囲 7.9...E\+28 \(絶対値\)  
  
-   [Single](../../../visual-basic/language-reference/data-types/single-data-type.md): 最大範囲 3.4...E\+38 \(絶対値\)  
  
-   [Double](../../../visual-basic/language-reference/data-types/double-data-type.md): 最大範囲 1.7...E\+308 \(絶対値\)  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のデータ型の詳細については、「[Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)」を参照してください。  
  
 オペランドが [Nothing](../../../visual-basic/language-reference/nothing.md) と評価される場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の算術演算子はこれを 0 と見なします。  
  
## 10 進数演算  
 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) データ型は、浮動小数点でも整数でもないという点に注意してください。  
  
 `+`、`–`、`*`、`/`、または `Mod` 演算の一方のオペランドが `Decimal` であり、もう一方が `Single` または `Double` でない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は後者のオペランドを `Decimal` に拡大変換します。  演算は `Decimal` で実行され、結果のデータ型は `Decimal` です。  
  
## 浮動小数点数演算  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、ほとんどの浮動小数点演算が、最も効率的なデータ型である [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) で実行されます。  しかし、一方のオペランドが [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) で、他方が `Double` でない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は演算を `Single` で実行します。  演算に先立って、各オペランドは必要に応じて適切なデータ型に拡大変換され、演算結果はそのデータ型になります。  
  
### \/ および ^ 演算子  
 `/` 演算子は、[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[Single](../../../visual-basic/language-reference/data-types/single-data-type.md)、および [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) データ型に対してのみ定義されています。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前に、必要に応じて各オペランドを適切なデータ型に拡大変換します。演算結果はそのデータ型になります。  
  
 次の表に、`/` 演算子の結果のデータ型を示します。  この表が、オペランドのデータ型の組み合わせで左右対称である点に注目してください。結果のデータ型は、オペランドの順序にかかわらず同じです。  
  
||||||  
|-|-|-|-|-|  
||`Decimal`|`Single`|`Double`|任意の整数型|  
|`Decimal`|10 進数|Single|Double|10 進数|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|任意の整数型|10 進数|Single|Double|Double|  
  
 `^` 演算子は、`Double` データ型に対してのみ定義されています。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前に、必要に応じて各オペランドを `Double` に拡大変換します。結果のデータ型は常に `Double` になります。  
  
## 整数演算  
 整数演算の結果のデータ型は、オペランドのデータ型に依存します。  一般的に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は次のポリシーを使用して結果のデータ型を決定します。  
  
-   二項演算子の両方のオペランドが同じデータ型である場合、結果はそのデータ型になります。  `Boolean` は例外で、強制的に `Short` になります。  
  
-   符号なしオペランドと符号付きオペランドの演算を行うと、結果は、最低でもいずれかのオペランドの範囲を持つ符号付きのデータ型になります。  
  
-   それ以外の場合は、結果は 2 つのオペランドのうち大きいほうのデータ型になります。  
  
 結果のデータ型が、いずれのオペランドのデータ型と同じにならない場合もあります。  
  
> [!NOTE]
>  演算結果として返される値が大きすぎる場合、結果のデータ型に格納できないこともあります。  結果のデータ型よりも値が大きい場合、<xref:System.OverflowException> 例外が発生します。  
  
### 単項プラスおよび単項マイナス演算子  
 次の表に、2 つの単項演算子 `+` および `–` の結果のデータ型を示します。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|単項 `+`|Short|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|単項 `–`|Short|SByte|Short|Short|整数型|整数型|Long|Long|10 進数|  
  
### \<\< および \>\> 演算子  
 2 つのビット シフト演算子 `<<` および `>>` の結果のデータ型を次の表に示します。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、各ビット シフト演算子は左側のオペランド \(シフトされるビット パターン\) の単項演算子として扱われます。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
  
 左側のオペランドが `Decimal`、`Single`、`Double`、または `String` の場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前にそれを `Long` に変換しようと試みます。結果のデータ型は `Long` になります。  右側のオペランド \(シフトするビット数\) は `Integer` または `Integer` に拡大変換できるデータ型である必要があります。  
  
### 二項 \+、–、\*、Mod 演算子  
 二項 `+` と `–` 演算子、および `*` と `Mod` 演算子の結果のデータ型を次の表に示します。  この表が、オペランドのデータ型の組み合わせで左右対称である点に注目してください。結果のデータ型は、オペランドの順序にかかわらず同じです。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整数型|整数型|Long|Long|10 進数|  
|`SByte`|SByte|SByte|Short|Short|整数型|整数型|Long|Long|10 進数|  
|`Byte`|Short|Short|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数型|整数型|Long|Long|10 進数|  
|`UShort`|整数型|整数型|UShort|整数型|UShort|整数型|UInteger|Long|ULong|  
|`Integer`|整数型|整数型|整数型|整数型|整数型|整数型|Long|Long|10 進数|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|10 進数|  
|`ULong`|10 進数|10 進数|ULong|10 進数|ULong|10 進数|ULong|10 進数|ULong|  
  
### \\ 演算子  
 次の表に、`\` 演算子の結果のデータ型を示します。  この表が、オペランドのデータ型の組み合わせで左右対称である点に注目してください。結果のデータ型は、オペランドの順序にかかわらず同じです。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数型|整数型|Long|Long|Long|  
|`UShort`|整数型|整数型|UShort|整数型|UShort|整数型|UInteger|Long|ULong|  
|`Integer`|整数型|整数型|整数型|整数型|整数型|整数型|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 `\` 演算子のいずれかのオペランドが [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[Single](../../../visual-basic/language-reference/data-types/single-data-type.md)、または [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) の場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前にそれを [Long](../../../visual-basic/language-reference/data-types/long-data-type.md) に変換しようと試みます。結果のデータ型は `Long` になります。  
  
## リレーショナルおよびビットごとの比較  
 リレーショナル演算 \(`=`、`<>`、`<`、`>`、`<=`、`>=`\) の結果のデータ型は常に `Boolean`[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) です。  これは、`Boolean` オペランドの論理演算 \(`And`、`AndAlso`、`Not`、`Or`、`OrElse`、`Xor`\) でも同様です。  
  
 ビットごとの論理演算の結果のデータ型は、オペランドのデータ型に依存します。  `AndAlso` および `OrElse` は、`Boolean` 用にのみ定義されており、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、演算が実行される前に、必要に応じて各オペランドが `Boolean` に変換されます。  
  
### \=、\<\>、\<、\>、\<\=、\>\= 演算子  
 両方のオペランドが `Boolean` の場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では `True` の値を `False` よりも小さいものとして見なします。  数値型を `String` と比較する場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では演算に先立って `String` が `Double` に変換されます。  `Char` または `Date` のオペランドは、同じデータ型のオペランドとのみ比較可能です。  結果のデータ型は常に `Boolean` です。  
  
### ビットごとの Not 演算子  
 次の表に、ビットごとの `Not` 演算子の結果のデータ型を示します。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
  
 オペランドが `Decimal`、`Single`、`Double`、または `String` の場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前にそれを `Long` に変換しようと試みます。結果のデータ型は `Long` になります。  
  
### ビットごとの And、Or、Xor 演算子  
 次の表に、ビットごとの `And`、`Or`、および `Xor` 演算子の結果のデータ型を示します。  この表が、オペランドのデータ型の組み合わせで左右対称である点に注目してください。結果のデータ型は、オペランドの順序にかかわらず同じです。  
  
|||||||||||  
|-|-|-|-|-|-|-|-|-|-|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数型|整数型|Long|Long|Long|  
|`UShort`|整数型|整数型|UShort|整数型|UShort|整数型|UInteger|Long|ULong|  
|`Integer`|整数型|整数型|整数型|整数型|整数型|整数型|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 オペランドが `Decimal`、`Single`、`Double`、または `String` の場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前にそれを `Long` に変換しようと試みます。結果のデータ型は `Long` になります。  
  
## その他の演算子  
 `&` 演算子は、`String` オペランドの連結のために定義されています。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前に、必要に応じて各オペランドを `String` に変換します。結果のデータ型は常に `String` です。  `Option Strict` が `On` の場合でも、`&` 演算子の目的のために、`String` への変換はすべて拡大変換の対象となります。  
  
 `Is` と `IsNot` 演算子では、両方のオペランドが参照型である必要があります。  `TypeOf`...`Is` 式では、最初のオペランドが参照型、2 番目のオペランドがデータ型の名前である必要があります。  いずれの場合も、結果のデータ型は `Boolean` です。  
  
 `Like` 演算子は、`String` オペランドのパターン一致用にのみ定義されています。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、演算の前に、各オペランドを必要に応じて `String` に変換しようと試みます。  結果のデータ型は常に `Boolean` です。  
  
## 参照  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operators](../../../visual-basic/language-reference/operators/index.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)