---
title: "How to: Convert Hexadecimal Strings to Numbers (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "numbers, hexadecimals"
  - "hexadecimals, decimals"
  - "examples [Visual Basic], string conversion"
  - "decimals, hexadecimals"
  - "string conversion, hexadecimal to numbers"
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Convert Hexadecimal Strings to Numbers (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

次の例は、<xref:System.Convert.ToInt32%2A> メソッドを使用して、16 進文字列を整数に変換します。  
  
### 16 進文字列を数値に変換するには  
  
-   <xref:System.Convert.ToInt32%2A> メソッドを使用して、ベース 16 で表現された数値を整数に変換します。  
  
     <xref:System.Convert.ToInt32%2A> メソッドの最初の引数が変換する文字列です。  2 番目の引数には、数値がどのベースで表現されているかを指定します。16 進であればベース 16 です。  
  
     [!code-vb[VbVbalrStrings#62](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>   
 <xref:System.Convert.ToInt32%2A>