---
title: "Handles clause requires a WithEvents variable defined in the containing type or one of its base types | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30506"
  - "bc30506"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30506"
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Handles clause requires a WithEvents variable defined in the containing type or one of its base types
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Handles` 句に `WithEvents` 変数が指定されませんでした。  プロシージャ宣言の末尾に `Handles` キーワードを指定すると、そのプロシージャは、`WithEvents` キーワードを使って宣言されたオブジェクト変数が発生させるイベントを処理します。  
  
 **Error ID:** BC30506  
  
### このエラーを解決するには  
  
-   必要な `WithEvents` 変数を指定します。  
  
## 参照  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)