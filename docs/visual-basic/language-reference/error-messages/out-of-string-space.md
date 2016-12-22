---
title: "Out of string space (Visual Basic) | Microsoft Docs"
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
  - "vbrID14"
dev_langs: 
  - "VB"
ms.assetid: 16681c75-a400-422d-9351-c691d3c7614e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Out of string space (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic では、非常に大きな文字列を使用できます。  ただし、他のプログラムの要求や文字列の操作方法によっては、このエラーが発生する場合があります。  
  
### このエラーを解決するには  
  
1.  評価時に文字列を一時的に作成する必要がある式でこのエラーが発生していないかどうかを確認します。  
  
2.  不要なアプリケーションをメモリから削除して領域を拡張します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [String Manipulation Summary](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)