---
title: "Integer Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Integer"
  - "Integer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, whole"
  - "enumerated values"
  - "whole numbers"
  - "integral data types"
  - "integer numbers"
  - "numbers, integer"
  - "integers, data types"
  - "literal type characters, I"
  - "integers, types"
  - "data types [Visual Basic], integral"
  - "% identifier type character"
  - "data types [Visual Basic], assigning"
  - "identifier type characters, %"
  - "I literal type character"
  - "Integer data type"
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Integer Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

\-2,147,483,648 から 2,147,483,647 までの符号付き 32 ビット \(4 バイト\) の整数を保持します。  
  
## 解説  
 `Integer` データ型は、32 ビットのプロセッサでパフォーマンスが最大になります。  他の整数型では、メモリとの間の読み込みと格納により長い時間がかかります。  
  
 `Integer` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **相互運用の考慮事項。**オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントを使用する場合、他の環境では整数型 \(`Integer`\) のデータ幅 \(16 ビット\) が異なることに注意してください。  そのようなコンポーネントに 16 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 \(`Integer`\) ではなく短整数型 \(`Short`\) として宣言します。  
  
-   **拡大変換。** `Integer` データ型は、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `Integer` を変換できることを意味します。  
  
-   **型宣言文字。**あるリテラルにリテラルの型文字 `I` を付けると、そのリテラルは `Integer` に変換されます。  ある識別子に識別子の型文字 `%` を付けると、その識別子は整数型 \(`Integer`\) に変換されます。  
  
-   **Framework のデータ型**.NET Framework において対応する型は、<xref:System.Int32?displayProperty=fullName> 構造体です。  
  
## 範囲  
 整数型の変数をその型の範囲外の数値に設定しようとすると、エラーが発生します。  小数に設定しようとすると、最も近い整数値に丸められます。  2 つの整数値に等しく近い場合は、最も近い偶数の整数に丸められます。  この処理により、常に中間値を単一方向に丸めるために発生する丸め誤差が最小限に抑えられます。  丸めの例を次のコードに示します。  
  
```  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```  
  
## 参照  
 <xref:System.Int32?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)