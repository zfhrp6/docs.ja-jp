---
title: "System.ServiceModel.MessageProcessingPaused | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.MessageProcessingPaused
System.ServiceModel.MessageProcessingPaused  
  
## 説明  
 メッセージの処理中にスレッドが切り替わりました。  
  
 メッセージ処理は、次の理由によって一時停止することがあります。  
  
-   ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。  
  
-   トランザクションが有効で、サービスが別のトランザクションを処理している。  
  
-   同期コンテキストが最新ではない。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)