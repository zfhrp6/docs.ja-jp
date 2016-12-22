---
title: "二重引用符は、EscapeQuote が True に設定されている区切り符号で分けられたフィールドには有効なコメント トークンではありません。 | Microsoft Docs"
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
  - "vbrTextFieldParser_InvalidComment"
dev_langs: 
  - "VB"
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 二重引用符は、EscapeQuote が True に設定されている区切り符号で分けられたフィールドには有効なコメント トークンではありません。
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`TextFieldParser` の区切り記号として二重引用符が指定されましたが、`EscapeQuotes` に `True` が設定されています。  
  
### このエラーを解決するには  
  
-   `EscapeQuotes` を `False` に設定します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 [How to: Read From Comma\-Delimited Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)