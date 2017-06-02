---
title: "CoordinatorRecoveryLogEntryCorrupt | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# CoordinatorRecoveryLogEntryCorrupt
ID: 139  
  
 重大度 : エラー  
  
 カテゴリ : TransactionBridge  
  
## 説明  
 このイベントは、コーディネーターの回復ログ エントリが破損し、逆シリアル化できなかったことを示します。このエラーが原因で、データの損失が発生することがあります。イベントには、トランザクション ID、回復データ \(Base64 エンコード\)、例外、プロセス名、およびプロセス ID が表示されます。  
  
## 参照  
 [イベント ログ](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)   
 [イベント一覧](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)