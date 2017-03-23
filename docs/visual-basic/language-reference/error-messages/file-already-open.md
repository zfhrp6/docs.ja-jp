---
title: "File already open | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID55"
dev_langs: 
  - "VB"
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# File already open
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

先にファイルを閉じてから、別の `FileOpen` または他の操作を実行する必要のある場合があります。  このエラーでは以下の原因が考えられます。  
  
-   既に開いているファイルに対して、シーケンシャル出力モードの `FileOpen` 操作が実行されました。  
  
-   ステートメントが、開いているファイルを参照しています。  
  
### このエラーを解決するには  
  
1.  ファイルを閉じてからステートメントを実行します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>