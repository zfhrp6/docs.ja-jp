---
title: "SByte Data Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.sbyte"
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
  - "SByte data type"
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# SByte Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\-128 から 127 までの符号付き 8 ビット \(1 バイト\) の整数を保持します。  
  
## 解説  
 `SByte` 型は、`Integer` のデータ幅全体、または `Short` のデータ幅の半分も必要としない整数値を格納する場合に使用します。  場合によっては、共通言語ランタイムが `SByte` 変数をメモリ内で間を空けないようにパックし、メモリの消費量を減らすことも可能です。  
  
 `SByte` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **CLS への準拠。** `SByte` データ型は、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS: Common Language Specification\) の一部ではありません。したがって、CLS 準拠のコードでは、このデータ型を使用しているコンポーネントを使用できません。  
  
-   **拡大変換。** `SByte` データ型は、`Short`、`Integer`、`Long`、`Decimal`、`Single`、および `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `SByte` を変換できることを意味します。  
  
-   **型宣言文字。** `SByte` 型には、リテラルの型文字も識別子の型文字もありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.SByte?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.SByte?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)