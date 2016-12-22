---
title: "Derived classes cannot raise base class events | Microsoft Docs"
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
  - "vbc30029"
  - "bc30029"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30029"
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Derived classes cannot raise base class events
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

イベントを発生させることができるのは、そのイベントが宣言されている宣言空間からだけです。  したがって、クラスは、派生元のクラスを含め、ほかのクラスからイベントを発生させることはできません。  
  
 **Error ID:** BC30029  
  
### このエラーを解決するには  
  
-   `Event` ステートメントまたは `RaiseEvent` ステートメントを移動して、両方のステートメントが同じクラス内に存在するようにします。  
  
## 参照  
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)