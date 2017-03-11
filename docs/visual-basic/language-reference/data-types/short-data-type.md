---
title: "Short Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Short"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "S literal type character"
  - "Short data type"
  - "literal type characters, S"
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Short Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

\-32,768 から 32,767 までの符号付き 16 ビット \(2 バイト\) の整数を保持します。  
  
## 解説  
 `Short` データ型は、整数型 \(`Integer`\) ほどのデータ 幅を必要としない整数値を格納するために使用します。  場合によっては、共通言語ランタイムが `Short` 変数をメモリ内で間を空けないようにパックし、メモリの消費量を減らすことも可能です。  
  
 `Short` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **拡大変換。** `Short` データ型は、`Integer`、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `Short` を変換できることを意味します。  
  
-   **型宣言文字。**あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。  `Short` には識別子の型文字はありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Int16?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.Int16?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)