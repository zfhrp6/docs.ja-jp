---
title: "&#39;&lt;functionname&gt;&#39; is not declared (Smart Device/Visual Basic Compiler Error) | Microsoft Docs"
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
  - "bc30766"
  - "vbc30766"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30766"
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;functionname&gt;&#39; is not declared (Smart Device/Visual Basic Compiler Error)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

\<`functionname`\> が宣言されていません。  通常、ファイル I\/O 機能は `Microsoft.VisualBasic` 名前空間で使用できますが、.NET Compact Framework のターゲット バージョンではサポートされていません。  
  
 **Error ID:** BC30766  
  
### このエラーを解決するには  
  
-   `System.IO` 名前空間で定義された関数を使用してファイル操作を実行します。  
  
## 参照  
 <xref:System.IO>   
 [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)