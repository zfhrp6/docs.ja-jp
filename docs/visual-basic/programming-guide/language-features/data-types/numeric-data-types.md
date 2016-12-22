---
title: "Numeric Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "integral types, Visual Basic"
  - "Short data type, numeric data types"
  - "Double data type, numeric data types"
  - "Long data type, Visual Basic numeric data types"
  - "numbers, whole"
  - "fractions"
  - "numbers"
  - "whole numbers"
  - "integer numbers"
  - "numbers, integer"
  - "fractional data types"
  - "mantissas, of fractional numbers"
  - "mantissas"
  - "data types [Visual Basic], numeric"
  - "Integer data type, numeric data types"
  - "exponent, of fractional numbers"
  - "integers"
  - "numeric data types, Visual Basic"
  - "Single data type, numeric types"
  - "Decimal data type, numeric data types"
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Numeric Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] には、さまざまな表現で数値を処理するための*数値データ型*が用意されています。  *整数*型は整数 \(正、負、および 0\) だけを表し、*非整数*型は整数部分と小数部分がある数値を表します。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] データ型の side\-by\-side の比較を示す表については、「[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)」を参照してください。  
  
## 整数型  
 *整数型*は、小数部分のない数だけを表すデータ型です。  
  
 *符号付き*整数型は、[SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) \(8 ビット\)、[Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) \(16 ビット\)、[Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) \(32 ビット\)、および [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) \(64 ビット\) です。  小数値ではなく、整数が常に変数に格納されている場合、次の型のいずれかとして宣言します。  
  
 *符号なし*整数型は、[Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) \(8 ビット\)、[UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) \(16 ビット\)、[UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) \(32 ビット\)、および [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) \(64 ビット\) です。  変数にバイナリ データまたは状態が不明のデータが含まれる場合は、これらの型のいずれかとして変数を宣言します。  
  
### パフォーマンス  
 算術演算の処理は、他のデータ型よりも整数型の方が高速です。  算術演算の処理は、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、`Integer` 型および `UInteger` 型で最速です。  
  
### 大きい整数  
 `Integer` データ型が保持できる整数よりも、より大きい整数を保持する必要がある場合、代わりに、`Long` データ型を使用できます。  `Long` 変数は、\-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 までの数を保持できます。  `Long` を使用した演算は、`Integer` を使用した場合よりも少し遅くなります。  
  
 さらに大きい値が必要な場合は、[Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) を使用できます。  小数部分を使用しない場合、`Decimal` 変数には、\-79,228,162,514,264,337,593,543,950,335 から 79,228,162,514,264,337,593,543,950,335 までの数を保持できます。  しかし、`Decimal` の数値を使用した演算は、他の数値データ型を使用した場合よりも大幅に遅くなります。  
  
### 小さい整数  
 `Integer` データ型のすべての範囲が必要ない場合、\-32,768 から 32,767 までの整数を保持できる、`Short` データ型を使用できます。  最も小さい整数の範囲に対しては、`SByte` データ型に、\-128 から 127 までの整数が保持されます。  小さい整数が保持される変数が非常に多くある場合、`Short` 変数および `SByte` 変数を、共通言語ランタイムに格納することもできます。この方法はより効率的であり、メモリの使用量を節約できます。  しかし、`Short` および `SByte` を使用した演算は、`Integer` を使用した演算よりも多少遅くなります。  
  
### 符号なし整数  
 変数が負の数値を保持する必要がないことが分かっている場合、*符号なしの型* `Byte`、`UShort`、`UInteger`、および `ULong` を使用できます。  これらのデータ型のそれぞれで、対応する符号付き型の 2 倍の正の整数を保持できます \(`SByte`、`Short`、`Integer`、および `Long`\)。  パフォーマンスの面では、それぞれの符号なしの型は、対応する符号付き型と同じくらい効率的です。  特に、`UInteger` と `Integer` は、共に非常に効率的にすべての基本数値データ型を処理します。  
  
## 非整数型の数値型  
 *非整数型のデータ型*は、整数部分と小数部分の両方を含む数値を表す型です。  
  
 非整数型の数値データ型は、`Decimal` \(128 ビットの固定小数点\)、[Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) \(32 ビットの浮動小数点\)、および [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) \(64 ビットの浮動小数点\) です。  これらの型はすべて符号付きです。  変数に小数が含まれる可能性がある場合には、この 3 つのいずれかの型で宣言します。  
  
 `Decimal` は浮動小数点型のデータ型ではありません。  `Decimal` の数値には、バイナリ整数値、および値のどの部分が小数部分であるのかを指定する、整数スケーリング要因があります。  
  
 通貨値に `Decimal` の変数を使用できます。  Sun は値の精度です。  `Double` データ型は高速で少ないメモリしか使用しませんが、四捨五入による誤差が生じる可能性があります。  `Decimal` の型は、 28 の小数点以下に完全さを保持します。  
  
 浮動小数点数 \(`Single` および `Double`\) の数値は `Decimal` の数値よりも大きい範囲ですが、丸め誤差が発生する可能性があります。  浮動小数点型がサポートする有効桁数は `Decimal` よりも少ないですが、より大きい値を表すことができます。  
  
 非整数型の数値は、mmmEeee として表すことができます。ここでは、mmm は *仮数* \(有効桁数\) であり、eee は*指数* \(10 の累乗\) です。  非整数型の最も大きい正の値は、`Decimal` では 7.9228162514264337593543950335E\+28、`Single` では 3.4028235E\+38、および `Double` では 1.79769313486231570E\+308 です。  
  
### パフォーマンス  
 現在のプラットフォーム上のプロセッサでは、浮動小数点の演算が倍精度で実行されるため、`Double` は、最も効率的な小数データ型です。  しかし、`Double` を使用した演算は、`Integer` などの整数型を使用した演算ほどは速くありません。  
  
### 小さい絶対値  
 考えられる最も小さい絶対値 \(0 に最も近い\) を持つ数に対しては、負の値には \-4.94065645841246544E\-324 を、および正の値には 4.94065645841246544E\-324 の数を、`Double` 変数に保持できます。  
  
### 小さい小数値  
 `Double` データ型のすべての範囲が必要ない場合、\-3.4028235E\+38 から 3.4028235E\+38 までの浮動小数点数を保持できる、`Single` データ型を使用できます。  `Single` 変数の最も小さいマグニチュードは、負の値に対しては \-1.401298E\-45、正の値に対しては 1.401298E\-45 です。  小さい浮動小数点数が保持される変数が非常に多くある場合、`Single` 変数を、共通言語ランタイムに格納することもできます。この方法はより効率的であり、メモリの使用量を節約できます。  
  
## 参照  
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Miscellaneous Data Types](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)