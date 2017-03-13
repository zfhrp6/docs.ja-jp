---
title: "How to: Convert a String to an Array of Characters in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "character arrays, converting strings"
  - "arrays [Visual Basic], converting strings to"
  - "examples [Visual Basic], string conversion"
  - "strings [Visual Basic], converting to arrays"
  - "string conversion [Visual Basic], arrays"
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Convert a String to an Array of Characters in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列を解析する際などに、文字列内の文字、およびそれらの文字の文字列内の位置に関するデータが取得できると便利な場合があります。  次の例では、文字列の <xref:System.String.ToCharArray%2A> メソッドを呼び出して、文字列内の文字の配列を取得する方法を示します。  
  
## 使用例  
 文字列を分割して `Char` 型の配列に格納する方法、および文字列を分割して Unicode テキスト文字の `String` 型の配列に格納する方法は次の例のようになります。  このような違いがあるのは、Unicode テキスト文字は 2 つ以上の `Char` 型の文字 \(サロゲート ペアまたは組み合わせ文字の並びなど\) で構成される場合があるからです。  詳細については、www.unicode.org の「<xref:System.Globalization.TextElementEnumerator>」および 「The Unicode Standard」を参照してください。  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## 使用例  
 文字列を Unicode テキスト文字に分割することは非常に困難ですが、これは文字列のビジュアル表現に関する情報が必要な場合には必要です。  次の例では、<xref:System.Globalization.StringInfo.SubstringByTextElements%2A> メソッドを使用して、文字列を構成する Unicode テキスト文字に関する情報を取得します。  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## 参照  
 <xref:System.String.Chars%2A>   
 <xref:System.Globalization.StringInfo?displayProperty=fullName>   
 [How to: Access Characters in Strings](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)   
 [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)