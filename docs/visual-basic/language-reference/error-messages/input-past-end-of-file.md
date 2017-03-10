---
title: "Input past end of file | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID62"
dev_langs: 
  - "VB"
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Input past end of file
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Input` ステートメントで空のファイルまたはすべてのデータが使用されているファイルからデータを読み取っているか、バイナリ アクセスで開いたファイルで `EOF` 関数が使用されました。  
  
### このエラーを解決するには  
  
1.  `Input` ステートメントの直前に `EOF` 関数を使用して、ファイルの終わりを検出します。  
  
2.  ファイルをバイナリ アクセスで開いている場合は、`Seek` および `Loc` を使用します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>