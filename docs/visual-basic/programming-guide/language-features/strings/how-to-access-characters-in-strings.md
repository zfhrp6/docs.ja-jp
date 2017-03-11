---
title: "How to: Access Characters in Strings in Visual Basic | Microsoft Docs"
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
  - "strings [Visual Basic], accessing characters"
  - "characters [Visual Basic], accessing in strings"
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Access Characters in Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.String.Chars%2A> プロパティを使用して、文字列の指定された位置にある文字にアクセスする方法は次のようになります。  
  
## 使用例  
 文字列内の文字に関するデータを取得したり、文字列内の文字の位置を調べたりできます。  文字列は、文字 \(`Char` 型のインスタンス\) の配列と見なすことができるため、<xref:System.String.Chars%2A> プロパティを使って文字のインデックスを参照すると、特定の文字を取得できます。  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/how-to-access-characters_1.vb)]  
  
 <xref:System.String.Chars%2A> プロパティの `index` パラメーターは、0 から始まります。  
  
## 信頼性の高いプログラミング  
 <xref:System.String.Chars%2A> プロパティは、指定された位置にある文字を返します。  ただし、Unicode 文字は複数の文字で表現される場合もあります。  Unicode 文字の詳細については、「[How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)」を参照してください。  
  
 <xref:System.String.Chars%2A> プロパティは、`index` パラメーターが文字列の長さ以上である場合、またはゼロよりも小さい場合に <xref:System.IndexOutOfRangeException> 例外をスローします。  
  
## 参照  
 <xref:System.String.Chars%2A>   
 [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)   
 [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)