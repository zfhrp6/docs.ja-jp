---
title: "UShort Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.ushort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "literal type characters, US"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "UShort data type"
  - "US literal type characters"
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# UShort Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

0 ～ 65,535 の範囲の、16 ビット \(2 バイト\) の符号なし整数値を格納します。  
  
## 解説  
 `UShort` データ型は、`Byte` を使うには大きすぎるバイナリ データを格納する際に使用します。  
  
 `UShort` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **負の数。** `UShort` 型は符号を持たないので、負の数を表現できません。  `UShort` 型を評価する式で単項マイナス演算子 \(`-`\) を使用すると、Visual Basic では、最初に式が `Integer` 型に変換されます。  
  
-   **CLS への準拠。** `UShort` データ型は、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS: Common Language Specification\) の一部ではありません。したがって、CLS 準拠のコードでは、このデータ型を使用しているコンポーネントを使用できません。  
  
-   **拡大変換。** `UShort` データ型は、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、および `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `UShort` を変換できることを意味します。  
  
-   **型宣言文字。**あるリテラルにリテラルの型文字 `US` を付けると、そのリテラルは `UShort` に変換されます。  `UShort` には識別子の型文字はありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.UInt16?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.UInt16>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)