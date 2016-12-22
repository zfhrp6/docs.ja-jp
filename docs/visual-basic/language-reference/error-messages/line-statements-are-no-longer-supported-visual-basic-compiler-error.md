---
title: "&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error) | Microsoft Docs"
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
  - "bc30830"
  - "vbc30830"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30830"
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Line ステートメントはサポートされていません。  ファイル I\/O 機能を利用するには `Microsoft.VisualBasic.FileSystem.LineInput` を使用します。グラフィックス機能を利用するには `System.Drawing.Graphics.DrawLine` を使用します。  
  
 **Error ID:** BC30830  
  
### このエラーを解決するには  
  
1.  ファイルにアクセスしている場合は、`Microsoft.VisualBasic.FileSystem.LineInput` を使用します。  
  
2.  グラフィックス処理を行っている場合は、`System.Drawing.Graphics.Drawline` を使用します。  
  
## 参照  
 <xref:System.IO>   
 <xref:System.Drawing>   
 [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)