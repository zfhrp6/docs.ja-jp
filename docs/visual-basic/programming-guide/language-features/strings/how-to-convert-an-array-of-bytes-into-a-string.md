---
title: "How to: Convert an Array of Bytes into a String in Visual Basic | Microsoft Docs"
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
  - "string conversion, arrays"
  - "byte arrays, converting to strings"
  - "examples [Visual Basic], strings"
  - "arrays [Visual Basic], converting to strings"
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Convert an Array of Bytes into a String in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このトピックでは、バイト配列内のバイトを文字列に変換する方法を解説します。  
  
## 使用例  
 この例では、<xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName> エンコーディング クラスの <xref:System.Text.Encoding.GetString%2A> メソッドを使用して、バイト配列内のすべてのバイトを文字列に変換します。  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 バイト配列を文字列に変換する場合、エンコーディング オプションを選択できます。  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName>: ASCII \(7 ビット\) 文字セットのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=fullName>: ビッグ エンディアンのバイト順を使用する UTF\-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=fullName>: システムの現在の ANSI コード ページのエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=fullName>: リトル エンディアンのバイト順を使用する UTF\-16 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=fullName>: リトル エンディアンのバイト順を使用する UTF\-32 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=fullName>: UTF\-7 形式のエンコーディングを取得します。  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=fullName>: UTF\-8 形式のエンコーディングを取得します。  
  
## 参照  
 <xref:System.Text.Encoding?displayProperty=fullName>   
 <xref:System.Text.Encoding.GetString%2A>   
 [How to: Convert Strings into an Array of Bytes in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)