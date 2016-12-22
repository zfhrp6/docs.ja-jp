---
title: "Double Data Type (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Double"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "identifier type characters, #"
  - "trailing zeros"
  - "real numbers"
  - "trailing 0 characters"
  - "0 characters, trailing"
  - "literal type characters, R"
  - "data types [Visual Basic], assigning"
  - "Double data type [Visual Basic]"
  - "# identifier type character"
  - "double-precision numbers"
  - "floating-point numbers, Double data type"
  - "R literal type character"
  - "zeros, trailing"
  - "Double data type"
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Double Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

IEEE 64 ビット \(8 バイト\) の符号付き浮動小数点数を格納します。負の値は \-1.79769313486231570E\+308 ～ \-4.94065645841246544E\-324、正の値は 4.94065645841246544E\-324 ～ 1.79769313486231570E\+308 の範囲の値をとります。  倍精度の数値には、実数の近似値が格納されます。  
  
## 解説  
 `Double` データ型に格納できる数値の範囲は、最大値はどのデータ型よりも大きく、最小値はどのデータ型よりも小さいという広範なものです。  
  
 `Double` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **精度。**浮動小数点数を扱う場合、これらの値がメモリ内で常に正確に表現されているわけではないことに注意してください。  このため、値の比較や `Mod` 演算子など、特定の処理で予期しない結果が返される可能性があります。  詳細については、「[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。  
  
-   **後続のゼロ。**浮動小数点のデータ型には、後続のゼロの文字に対する内部表現がありません。  たとえば、4.2000 と 4.2 は区別されません。  したがって、浮動小数点数の値を表示または印刷するとき、後続のゼロの文字は出力されません。  
  
-   **型宣言文字。**あるリテラルにリテラルの型文字 `R`  を付けると、そのリテラルは `Double` に変換されます。  たとえば、整数値の後が `R` の場合、その値は `Double` に変更されます。  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     ある識別子に識別子の型文字 `#` を付けると、その識別子は整数型 \(`Double`\) に変換されます。  次の例では、`num` 変数が `Double` として型指定されています。  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Double?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.Double?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)