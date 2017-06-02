---
title: "System.ServiceModel.TxFailedToNegotiateOleTx | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.TxFailedToNegotiateOleTx
指定されたコーディネーション コンテキストのための OleTransactions プロトコル ネゴシエーションに失敗しました。  
  
## 説明  
 OleTx 情報が添付された受信トランザクションがその OleTx 情報を使用できず、代わりに WS\-AT 使用した場合にトレースされます。  
  
## トラブルシューティング  
 コンピューター間の MSDTC RPC 通信に潜在的な問題があることを示しています。これらのトレースが多数ログに記録されている場合は、大幅なパフォーマンス低下が発生している可能性があります。OleTx が必要ない場合は、WS\-AT のレジストリ構成で `OleTxUpgradeEnabled` を 0 に設定してください。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)