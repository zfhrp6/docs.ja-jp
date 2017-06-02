---
title: "System.ServiceModel.Channels.MsmqMessageDropped | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMessageDropped
MSMQ はメッセージを破棄しました。  
  
## 説明  
 このトレースは、MSMQ メッセージが破棄されたことを示します。[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] を NetMsmqBinding または MsmqIntegrationBinding と共に使用したときに、MSMQ メッセージを処理できない場合は、これらのメッセージが破棄されることがあります。このようなメッセージは、有害メッセージと呼ばれます。  
  
 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。破棄されたメッセージはキューから削除され、元に戻すことはできません。  
  
 メッセージが有害となる場合の詳細、および有害メッセージをサービスで適切に処理する方法については、「[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)」を参照してください。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)   
 [有害メッセージ処理](http://go.microsoft.com/fwlink/?LinkID=99546)