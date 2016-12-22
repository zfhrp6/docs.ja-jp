---
title: "Long Data Type (Visual Basic) | Microsoft Docs"
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
  - "vb.Long"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "identifier type characters, &"
  - "numbers, whole"
  - "whole numbers"
  - "integral data types"
  - "& identifier type character"
  - "integer numbers"
  - "literal type characters, L"
  - "numbers, integer"
  - "integers, data types"
  - "L literal type character"
  - "integers, types"
  - "Long keyword"
  - "data types [Visual Basic], integral"
  - "data types [Visual Basic], assigning"
  - "Long data type"
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Long Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807 \(9.2...E\+18\) までの符号付き 64 ビット \(8 バイト\) の整数です。  
  
## 解説  
 大きすぎて `Integer` データ型に格納できない整数値を格納するには、`Long` データ型を使用します。  
  
 `Long` の既定値は 0 です。  
  
## プログラミングのヒント  
  
-   **相互運用の考慮事項。**オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントを使用する場合、他の環境では整数型 \(`Long`\) のデータ幅 \(32 ビット\) が異なることに注意してください。  そのようなコンポーネントに 32 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 \(`Long`\) ではなく短整数型 \(`Integer`\) として宣言します。  
  
     さらに、Windows 95、Windows 98、Windows ME、または Windows 2000 では、オートメーションで 64 ビット整数型がサポートされていません。  これらのオペレーティング システムでは、Visual Basic の長整数型 \(`Long`\) の引数をオートメーション コンポーネントに渡すことはできません。  
  
-   **拡大変換。** `Long` データ型は、`Decimal`、`Single`、または `Double` に拡大変換されます。  これは、<xref:System.OverflowException?displayProperty=fullName> エラーを発生させることなく、これらの型のいずれかに `Long` を変換できることを意味します。  
  
-   **型宣言文字。**あるリテラルにリテラルの型文字 `L` を付けると、そのリテラルは `Long` に変換されます。  ある識別子に識別子の型文字 `&` を付けると、その識別子は整数型 \(`Long`\) に変換されます。  
  
-   **Framework のデータ型。**.NET Framework において対応する型は、<xref:System.Int64?displayProperty=fullName> 構造体です。  
  
## 参照  
 <xref:System.Int64>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)