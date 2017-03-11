---
title: "&#39;Class&#39; statement must end with a matching &#39;End Class&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30481"
  - "bc30481"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30481"
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &#39;Class&#39; statement must end with a matching &#39;End Class&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Class` は `Class` ブロックを開始するために使用します。したがって、ブロックの先頭にだけ記述でき、対応する `End Class` ステートメントでブロックの終了を示す必要があります。  余分な `Class` ステートメントがあります。または、`Class` ブロックが `End Class` で終了していません。  
  
 **Error ID:** BC30481  
  
### このエラーを解決するには  
  
-   必要のない `Class` ステートメントを探し、削除します。  
  
-   `Class` ブロックを対応する `End Class` で終了します。  
  
## 参照  
 [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)