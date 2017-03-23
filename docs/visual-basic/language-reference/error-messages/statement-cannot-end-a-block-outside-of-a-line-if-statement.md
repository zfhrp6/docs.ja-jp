---
title: "Statement cannot end a block outside of a line &#39;If&#39; statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32005"
  - "bc32005"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32005"
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Statement cannot end a block outside of a line &#39;If&#39; statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

単一行の `If` ステートメントに、コロン \(:\) で区切られた複数のステートメントが含まれています。そのうちの 1 つは、この単一行 `If` ステートメントの外側にあるコントロール ブロックの `End` ステートメントです。  単一行の `If` ステートメントでは `End If` ステートメントを使用しません。  
  
 **Error ID:** BC32005  
  
### このエラーを解決するには  
  
-   `End If` ステートメントを含むコントロール ブロックの外側に、単一行の `If` ステートメントを移動します。  
  
## 参照  
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)