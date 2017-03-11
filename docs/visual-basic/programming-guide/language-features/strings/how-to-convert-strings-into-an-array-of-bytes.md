---
title: "How to: Convert Strings into an Array of Bytes in Visual Basic | Microsoft Docs"
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
  - "string conversion, arrays"
  - "arrays [Visual Basic], converting strings to"
  - "byte arrays"
  - "examples [Visual Basic], string conversion"
  - "arrays [Visual Basic], byte arrays"
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# How to: Convert Strings into an Array of Bytes in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックでは、文字列をバイトの配列に変換する方法を示します。  
  
## 使用例  
 この例では、<xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> エンコーディング クラスの <xref:System.Text.Encoding.GetBytes%2A> メソッドを使用して、文字列をバイトの配列に変換します。  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/how-to-convert-strings-i_1.vb)]  
  
 文字列をバイト配列に変換する場合、エンコーディング オプションを選択できます。  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: ASCII \(7 ビット\) 文字セットのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: ビッグ エンディアンのバイト順を使用する UTF\-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: システムの現在の ANSI コード ページのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: リトル エンディアンのバイト順を使用する UTF\-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: リトル エンディアンのバイト順を使用する UTF\-32 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: UTF\-7 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: UTF\-8 形式のエンコーディングを取得します。  
  
## 参照  
 <xref:System.Text.Encoding?displayProperty=fullName>   
 <xref:System.Text.Encoding.GetBytes%2A>   
 [How to: Convert an Array of Bytes into a String in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)