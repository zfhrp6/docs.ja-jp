---
title: "Return Values for the CStr Function (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "times, CStr Function return values"
  - "type conversion"
  - "dates [Visual Basic], CStr Function return values"
  - "CStr function"
  - "strings [Visual Basic], return value"
  - "Date data type, converting"
  - "dates [Visual Basic]"
  - "String data type, converting"
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Return Values for the CStr Function (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

異なる型の `expression` に対する `CStr` の戻り値を次の表に示します。  
  
|`expression` の型|`CStr` の戻り値|  
|---------------------|-----------------|  
|[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|"True" または "False" を表す文字列|  
|[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)|システムで設定されている短い形式の日付で `Date` 型の値 \(日付と時刻\) を表す文字列|  
|[Numeric Data Types](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|数値を表す文字列|  
  
## CStr と日付データ型  
 日付データ型 \(`Date`\) には、常に日付と時刻の両方の情報が含まれます。  型変換のために、Visual Basic は 1\/1\/0001 \(西暦 1 年 1 月 1 日\) を日付の基準値と見なし、00:00:00 \(午前 0 時\) を時刻の*基準値*と見なします。  `CStr` は、結果の文字列に基準値を含めません。  たとえば、`#January 1, 0001 9:30:00#` を文字列に変換すると、結果は "9:30:00 AM" となり、日付情報が省略されます。  ただし、元の日付型 \(`Date`\) の値には日付情報が残っており、<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> などの関数を使って復元できます。  
  
> [!NOTE]
>  `CStr` 関数は、アプリケーションにおける現在のカルチャ設定に基づいて変換処理を実行します。  特定のカルチャにおける数の文字表現を調べるには、その数の `ToString(IFormatProvider)` メソッドを使用します。  たとえば、倍精度浮動小数点型 \(`Double`\) の値を文字列型 \(`String`\) に変換するときには、<xref:System.Double.ToString%2A?displayProperty=fullName> を使用します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)