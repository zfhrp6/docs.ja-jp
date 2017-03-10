---
title: "Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31423"
  - "bc31423"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31423"
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] はイベントを実装できません。そのイベントのデリゲート型がインターフェイスのイベントのデリゲート型と一致しないためです。  このエラーは、インターフェイス内で複数のイベントを定義し、同じイベントを使用してそれらのイベントを実装しようとすると発生する場合があります。  1 つのイベントが 2 つ以上のイベントを実装できるのは、実装されるすべてのイベントが `As` 構文を使用して宣言され、同じデリゲート型を指定している場合だけです。  
  
 **Error ID:** BC31423  
  
### このエラーを解決するには  
  
-   イベントを個別に実装します。  
  
     または  
  
-   インターフェイス内のイベントを `As` 構文を使用して定義し、同じデリゲート型を指定します。  
  
## 参照  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)