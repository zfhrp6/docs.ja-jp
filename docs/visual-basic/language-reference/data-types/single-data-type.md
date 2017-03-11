---
title: "Single Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Single"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Single data type"
  - "F literal type character"
  - "trailing zeros"
  - "real numbers"
  - "literal type characters, F"
  - "trailing 0 characters"
  - "identifier type characters, !"
  - "single-precision numbers"
  - "! identifier type character"
  - "0 characters, trailing"
  - "data types [Visual Basic], assigning"
  - "floating-point numbers, Single data type"
  - "numbers, real"
  - "zeros, trailing"
  - "numbers, floating point"
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Single Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

IEEE 32 ビット \(4 バイト\) の符号付き単精度浮動小数点数を格納します。負の値は \-3.4028235E\+38 ～ \-1.401298E\-45、正の値は 1.401298E\-45 ～ 3.4028235E\+38 の範囲の値をとります。  単精度の数値には、実数の近似値が格納されます。  
  
## 解説  
 `Single` データ型は、倍精度浮動小数点型 \(`Double`\) ほどのデータ 幅を必要としない浮動小数点数を格納するために使用します。  場合によっては、共通言語ランタイムが `Single` 変数をメモリ内で間を空けないようにパックし、メモリの消費量を減らすことも可能です。  
  
 `Single` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **精度。**浮動小数点数を扱う場合、これらの値がメモリ内で常に正確に表現されているわけではないことに注意してください。  このため、値の比較や `Mod` 演算子など、特定の処理で予期しない結果が返される可能性があります。  詳細については、「[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。  
  
-   **拡大変換。** `Single` データ型は `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、`Single` を `Double` に変換できることを意味します。  
  
-   **後続のゼロ。**浮動小数点のデータ型には、後続のゼロの文字に対する内部表現がありません。  たとえば、4.2000 と 4.2 は区別されません。  したがって、浮動小数点数の値を表示または印刷するとき、後続のゼロの文字は出力されません。  
  
-   **型宣言文字。**あるリテラルに型文字 `F` を付けると、そのリテラルは単精度浮動小数点型 \(`Single`\) に変換されます。  ある識別子に識別子の型文字 `!` を付けると、その識別子は整数型 \(`Single`\) に変換されます。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Single?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.Single?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)