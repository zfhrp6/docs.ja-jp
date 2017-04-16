---
title: "System.ServiceModel.Channels.MsmqPoisonMessageRejected | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqPoisonMessageRejected
有害メッセージは拒否されました。  
  
## 説明  
 このトレースは、有害メッセージが検出され、続いて拒否されたことを示します。これは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると発生します。拒否されたメッセージは、送信側の [配信不能キューを使用したメッセージ転送エラー処理](http://go.microsoft.com/fwlink/?LinkId=99544) に戻されます。  
  
 メッセージが有害となる場合の詳細、および有害メッセージをサービスで適切に処理する方法については、「[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkId=99546)」を参照してください。MSMQ でメッセージが拒否されることの意味の詳細については、「[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)」を参照してください。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [有害メッセージ処理](http://go.microsoft.com/fwlink/?LinkId=99546)   
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)