---
title: "&#39;&lt;name1&gt;&#39; is ambiguous, imported from the namespaces or types &#39;&lt;name2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30561"
  - "bc30561"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30561"
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;name1&gt;&#39; is ambiguous, imported from the namespaces or types &#39;&lt;name2&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

あいまいな名前を指定したため、ほかの名前と競合しています。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のコンパイラには競合を解決するための規則がないため、あいまいでない名前に変更する必要があります。  
  
 **Error ID:** BC30561  
  
### このエラーを解決するには  
  
1.  名前空間インポートを削除して名前のあいまいさを解決します。  
  
2.  完全限定名を使います。  
  
## 参照  
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)