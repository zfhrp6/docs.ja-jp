---
title: "PiiLoggingNotAllowed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# PiiLoggingNotAllowed
ID : 108  
  
 重大度 : エラー  
  
 カテゴリ : トレース  
  
## 説明  
 このイベントは、既知の PII がログ記録されていないことを示します。  既知の PII はログ記録できません。  既知の PII をログ記録できるようにするには、Machine.config の "enableLoggingKnownPii" を `true` に設定します。  イベントには、プロセス名とプロセス ID が表示されます。  
  
## 参照  
 [イベント ログ](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)   
 [イベント一覧](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)