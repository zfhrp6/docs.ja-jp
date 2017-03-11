---
title: "&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30014"
  - "bc30014"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30014"
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`#ElseIf` は条件付きコンパイル ディレクティブです。  `#ElseIf` 句の前には、対応する `#If` 句か `#ElseIf` 句が必要です。  
  
 **Error ID:** BC30014  
  
### このエラーを解決するには  
  
1.  先行する `#If`  または `#ElseIf` と、この `#ElseIf` とが、間に条件付きコンパイル ブロックを挿入することによって分離されていないこと、または `#End If` 句を間違った場所に記述したために分離されていないことを確認します。  
  
2.  `#ElseIf` の前に `#Else` ディレクティブがある場合は、その `#Else` を削除するか、`#ElseIf` に変更します。  
  
3.  すべて問題ない場合は、条件付きコンパイル ブロックの先頭に `#If` ディレクティブを追加します。  
  
## 参照  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)