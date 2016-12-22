---
title: "Troubleshooting: Reading from and Writing to Text Files (Visual Basic) | Microsoft Docs"
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
  - "troubleshooting file I/O"
  - "writing text to files, troubleshooting"
  - "troubleshooting Visual Basic, text files"
  - "I/O [Visual Basic], troubleshooting text files"
  - "writing to files, troubleshooting"
  - "reading text files, troubleshooting"
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting: Reading from and Writing to Text Files (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このトピックでは、テキスト ファイルを扱うときに生じる一般的な問題について説明し、それぞれの対処方法を示します。  
  
## 一般的な問題  
 テキスト ファイルを扱うときに特によくある問題点には、セキュリティ例外、ファイル エンコーディング、および無効なパスがあります。  
  
### セキュリティ例外  
 セキュリティ エラーが発生すると <xref:System.Security.SecurityException> がスローされます。  これは、ユーザーに必要なアクセス許可がないことが原因で生じる場合が多く、アクセス許可を追加するか、またはファイルを分離ストレージで扱うことにより解決できることがあります。  詳細については、「[例外のトラブルシューティング : System.Security.SecurityException](../Topic/Troubleshooting%20Exceptions:%20System.Security.SecurityException.md)」を参照してください。  
  
### ファイル エンコーディング  
 ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキスト処理での文字の表現方法を指定するものです。  テキスト ファイルに予期しない文字が含まれていると、エンコーディングが不正となる場合があります。  大半のファイルでは、どの言語の文字を処理できるか \(またはできないか\) という点から見て、あるエンコーディングが別のエンコーディングより好ましいという場合があります。ただし通常は Unicode が好まれます。  詳細については、「[File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)」および「<xref:System.Text.Encoding>」を参照してください。  
  
### 不正なパス  
 ファイル パス \(特に相対パス\) を解析するときには、間違ったデータを指定しがちです。  多くの問題は、正しいパスを指定しているかどうかを確認することで修正できます。  詳細については、「[方法 : ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)