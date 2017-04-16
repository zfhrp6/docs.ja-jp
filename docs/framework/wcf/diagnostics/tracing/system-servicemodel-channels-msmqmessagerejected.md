---
title: "System.ServiceModel.Channels.MsmqMessageRejected | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMessageRejected
MSMQ はメッセージを拒否しました。  
  
## 説明  
 このトレースは、MSMQ メッセージが拒否されたことを示します。  
  
 MSMQ メッセージは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] が \(NetMsmqBinding または MsmqIntegrationBinding のいずれかを使用して\) メッセージを処理できない場合に拒否されることがあります。このようなメッセージは、有害メッセージと呼ばれます。有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。拒否されたメッセージは、送信側の「[配信不能キューを使用したメッセージ転送エラー処理](http://go.microsoft.com/fwlink/?LinkID=99544)」に戻されます。  
  
 メッセージが有害となる場合の詳細、および有害メッセージをサービスで適切に処理する方法については、「[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)」を参照してください。  
  
 MSMQ でメッセージが拒否されることの意味の詳細については、「[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)」を参照してください。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [有害メッセージ処理](http://go.microsoft.com/fwlink/?LinkID=99546)   
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)