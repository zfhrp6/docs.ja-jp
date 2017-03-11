---
title: "File Encodings (Visual Basic) | Microsoft Docs"
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
  - "character encodings"
  - "files, encoding"
  - "Unicode, file encoding"
  - "file encoding"
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# File Encodings (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキスト処理での文字の表現方法を指定するものです。  どの言語の文字を処理できるか \(またはできないか\) という点から見て、あるエンコーディングが別のエンコーディングより好ましい場合もありますが、通常は Unicode が好まれます。  
  
 ファイルに対する読み取りと書き込みでは、ファイル エンコーディングがきちんと一致しないと、例外が発生したり、不正な結果となる場合があります。  
  
## エンコーディングの種類  
 ファイルを扱うときには、Unicode は好ましいエンコーディングです。  Unicode は、世界共通の文字エンコーディング規則で、技術的な記号や出版で使用される特殊文字などを含む、現在のコンピューティングで使用されるすべての文字を、16 ビットのコード値で表します。  
  
 これまでの文字エンコーディング規則は、Windows ANSI 文字セットなどの従来からある文字セットで構成されており、8 ビットのコード値や 8 ビット値の組み合わせを使用して、特定の言語や地域で使用する文字を表していました。  
  
## Encoding クラス  
 <xref:System.Text.Encoding> クラスは文字エンコーディングを表します。  次の表は、利用可能なエンコーディングの型の一覧とそれぞれの説明です。  
  
|||  
|-|-|  
|名前|Description|  
|<xref:System.Text.ASCIIEncoding>|Unicode 文字の ASCII 文字エンコーディングを表します。|  
|<xref:System.Text.UnicodeEncoding>|Unicode 文字の UTF\-16 エンコーディングを表します。|  
|<xref:System.Text.UTF32Encoding>|Unicode 文字の UTF\-32 エンコーディングを表します。|  
|<xref:System.Text.UTF7Encoding>|Unicode 文字の UTF\-7 エンコーディングを表します。|  
|<xref:System.Text.UTF8Encoding>|Unicode 文字の UTF\-8 エンコーディングを表します。|  
  
## 参照  
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)