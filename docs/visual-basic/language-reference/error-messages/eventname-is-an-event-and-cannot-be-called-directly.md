---
title: "&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly | Microsoft Docs"
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
  - "bc32022"
  - "vbc32022"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32022"
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<`eventname`\>' はイベントであるため、直接呼び出すことはできません。  `RaiseEvent` ステートメントを使用して、イベントを発生させます。  
  
 プロシージャの呼び出しで、プロシージャ名についてイベントが指定されています。  イベント ハンドラーはプロシージャですが、イベント自体はシグナル デバイスであり、発生および処理する必要があります。  
  
 **Error ID:** BC32022  
  
### このエラーを解決するには  
  
1.  `RaiseEvent` ステートメントを使用してイベントを通知し、それを処理するプロシージャを呼び出します。  
  
## 参照  
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)