---
title: "ULong Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ulong"
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
  - "literal type characters, UL"
  - "ULong data type"
  - "UL literal type characters"
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# ULong Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

0 から 18,446,744,073,709,551,615 \(1.84 の 10 ^ 19 倍よりも大きい\) までの範囲の、符号なし 64 ビット \(8 バイト\) 整数値を格納します。  
  
## 解説  
 `ULong` データ型は、`UInteger` には大きすぎるバイナリ データや、非常に大きい符号なし整数値を格納する場合に使用します。  
  
 `ULong` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **負の数。** `ULong` 型は符号を持たないので、負の数を表現できません。  バイト型 \(`ULong`\) を評価する式で単項マイナス演算子 \(`-`\) を使用すると、Visual Basic では、最初に式が `Decimal` 型に変換されます。  
  
-   **CLS への準拠。** `ULong` データ型は、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS: Common Language Specification\) の一部ではありません。したがって、CLS 準拠のコードでは、このデータ型を使用しているコンポーネントを使用できません。  
  
-   **相互運用の考慮事項。**たとえばオートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントを使用する場合は、`ulong` などの型のデータ幅 \(32 ビット\) が環境によって異なる場合があることに注意してください。  そのようなコンポーネントに 32 ビットの引数を渡す場合は、Visual Basic のマネージ コードで、`ULong` 型ではなく `UInteger` 型で宣言してください。  
  
     さらに、Windows 95、Windows 98、Windows ME、または Windows 2000 では、オートメーションで 64 ビット整数型がサポートされていません。  これらのプラットフォームでは、Visual Basic の長整数型 \(`ULong`\) の引数をオートメーション コンポーネントに渡すことはできません。  
  
-   **拡大変換。** `ULong` データ型は、`Decimal`、`Single`、および `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `ULong` を変換できることを意味します。  
  
-   **型宣言文字。**あるリテラルにリテラルの型文字 `UL` を付けると、そのリテラルは `ULong` に変換されます。  `ULong` には識別子の型文字はありません。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.UInt64?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.UInt64>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)