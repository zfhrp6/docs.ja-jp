---
title: "Can&#39;t create necessary temporary file | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID322"
dev_langs: 
  - "VB"
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Can&#39;t create necessary temporary file
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

TEMP 環境変数で指定されているディレクトリのあるドライブがいっぱいであるか、TEMP 環境変数でドライブまたはディレクトリが、無効または読み取り専用になっています。  
  
### このエラーを解決するには  
  
1.  ドライブがいっぱいである場合は、ファイルを削除します。  
  
2.  TEMP 環境変数で別のドライブを指定します。  
  
3.  TEMP 環境変数で有効なドライブを指定します。  
  
4.  現在指定されているドライブまたはディレクトリから、読み取り専用の制限を削除します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)