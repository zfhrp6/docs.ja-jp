---
title: "UInteger Data Type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.uinteger"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "UInteger data type"
  - "literal type characters, UI"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "integers, types"
  - "UI literal type characters"
  - "data types [Visual Basic], integral"
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# UInteger Data Type
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

0 から 4,294,967,295 までの符号なし 32 ビット \(4 バイト\) の整数です。  
  
## 解説  
 `UInteger` データ型では、符号なしの最大値を最も効率的なデータ幅で表示します。  
  
 `UInteger` の既定値は 0 です。  
  
## プログラミングのヒント  
 `UInteger` および `Integer` データ型は、32 ビット プロセッサで最良のパフォーマンスを発揮します。より小さな整数型 \(`UShort`、`Short`、`Byte`、`SByte`\) では、読み込み、格納、フェッチの際に、使用するビットは少なくて済みますが、より多くの時間がかかるためです。  
  
-   **負の数。** `UInteger` 型は符号を持たないので、負の数を表現できません。  `UInteger` 型を評価する式で単項マイナス演算子 \(`-`\) を使用すると、Visual Basic では、最初に式が `Long` 型に変換されます。  
  
-   **CLS への準拠。** `UInteger` データ型は、[言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS: Common Language Specification\) の一部ではありません。したがって、CLS 準拠のコードでは、このデータ型を使用しているコンポーネントを使用できません。  
  
-   **相互運用の考慮事項。** たとえばオートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントを使用する場合は、`uint` などの型のデータ幅 \(16 ビット\) が環境によって異なる場合があることに注意してください。  そのようなコンポーネントに 16 ビットの引数を渡す場合は、Visual Basic のマネージ コードで、`UInteger` 型ではなく `UShort` 型で宣言してください。  
  
-   **拡大変換。** `UInteger` データ型は、`Long`、`ULong`、`Decimal`、`Single`、および `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `UInteger` を変換できることを意味します。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `UI` を付けると、そのリテラルは `UInteger` に変換されます。  `UInteger` には識別子の型文字はありません。  
  
-   **Framework のデータ型。** .NET Framework において対応する型は、<xref:System.UInt32?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.UInt32>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)