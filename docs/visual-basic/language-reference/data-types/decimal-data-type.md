---
title: "Decimal Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Decimal"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "literal type characters, D"
  - "trailing zeros"
  - "real numbers"
  - "trailing 0 characters"
  - "Decimal data type"
  - "D literal type character"
  - "decimals, Decimal data type"
  - "0 characters, trailing"
  - "data types [Visual Basic], assigning"
  - "decimal keyword"
  - "numbers, real"
  - "variable-precision numbers"
  - "zeros, trailing"
  - "@ identifier type character"
  - "identifier type characters, @"
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Decimal Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

96 ビット \(12 バイト\) の整数を 10 の累乗 \(可変\) でスケーリングした値を表す 128 ビット \(16 バイト\) の符号付きの値を保持します。  スケール ファクターには、小数点の右側の桁数を 0 ～ 28 の範囲で指定します。  スケール ファクターが 0 \(小数点なし\) であれば、最大値は \+\/\-79,228,162,514,264,337,593,543,950,335 \(\+\/\-7.9228162514264337593543950335E\+28\) になります。  小数点以下 28 桁の数値の場合、最大値は \+\/\-7.9228162514264337593543950335 で、ゼロを除く最小値は \+\/\-0.0000000000000000000000000001 \(\+\/\-1E\-28\) です。  
  
## 解説  
 `Decimal` 型では、桁数が非常に大きい数値を扱うことができます。  有効桁数は最大 29 で、7.9228 x 10^28 を超える値を表現できます。  特に、多くの桁数を必要とし、丸め誤差が許容されない財務計算などに適しています。  
  
 `Decimal` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **精度。** `Decimal` は浮動小数点型のデータ型ではありません。  `Decimal` 構造体には、バイナリ整数値と共に符号ビット、および値のどの部分が小数かを指定するスケール ファクターが整数で格納されます。  このため、`Decimal` では、メモリ内で浮動小数点型 \(`Single` および `Double`\) よりも正確に数値を表現できます。  
  
-   **パフォーマンス** `Decimal` は、すべての数値型の中で最もパフォーマンスの低いデータ型です。  データ型を選択する前に、精度の重要性とパフォーマンスとを比較検討する必要があります。  
  
-   **拡大変換。** `Decimal` データ型は `Single` または `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `Decimal` を変換できることを意味します。  
  
-   **後続のゼロ。**Visual Basic では、`Decimal` のリテラルに後続ゼロが格納されません。  ただし、`Decimal` 型の変数は、計算に必要なすべての後続ゼロを保持します。  次に例を示します。  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     この例で、`MsgBox` の出力は次のようになります。  
  
     d1 \= 2.375, d2 \= 1.625, d3 \= 4.000, d4 \= 4  
  
-   **型宣言文字。**あるリテラルに型文字 `D` を付けると、そのリテラルは整数型 \(`Decimal`\) に変換されます。  ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 \(`Decimal`\) に変換されます。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Decimal?displayProperty=fullName> 構造体です。  
  
## 範囲  
 `D` の型文字を使用して、`Decimal` 型の変数または定数に大きな値を代入することが必要になる場合があります。  この要件は次のようにリテラルの型文字がリテラルに従うコンパイラが `Long` としてリテラルを解釈するためです。  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 `bigDec1` の宣言には、割り当てられた値が `Long`の範囲内にあるため、オーバーフローが発生しません。  `Long` の値は `Decimal` の変数に代入できます。  
  
 `bigDec2` の宣言には、割り当てられた値が `Long`に対して大きすぎるため、オーバーフロー エラーが生成されます。  数値リテラルは `Long`として解釈できないため `Decimal` の変数に代入することはできません。  
  
 `bigDec3`では、リテラルの型文字 `D` はコンパイラに `Long`ではなく `Decimal` としてリテラルを解釈するように、問題を解決します。  
  
## 参照  
 <xref:System.Decimal?displayProperty=fullName>   
 <xref:System.Decimal.%23ctor%2A?displayProperty=fullName>   
 <xref:System.Math.Round%2A?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)