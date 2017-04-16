---
title: "System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
メッセージの受信速度が速すぎます。  
  
## 説明  
 このトレースは、受信メッセージの処理を試みたときに行われます。  特定の近隣ノードでクォータ セットが超過しているため、メッセージをその近隣ノードに転送できません。  応答しない近隣ノードが、メッセージ保留のバックログをクリアできなかった場合にこの状態が発生します。  
  
## トラブルシューティング  
 メッシュ内でメッセージが送信される速度を遅くしてください。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)