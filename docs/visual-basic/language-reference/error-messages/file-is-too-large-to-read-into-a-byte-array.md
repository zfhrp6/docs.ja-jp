---
title: "File is too large to read into a byte array | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# File is too large to read into a byte array
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

バイト配列に読み込もうとしているファイルのサイズが 4 GB を超えています。  `My.Computer.FileSystem.ReadAllBytes` メソッドではこのサイズよりも大きいファイルを読み込むことができません。  
  
### このエラーを解決するには  
  
-   <xref:System.IO.StreamReader> を使ってファイルを読み込んでください。  詳細については、「[.NET Framework のファイル I\/O とファイル システムの基礎 \(Visual Basic\)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:System.IO.StreamReader>   
 [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)   
 [How to: Read Text from Files with a StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)