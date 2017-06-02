---
title: "System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
メッセージを移動または削除できません。  
  
## 説明  
 このトレースは、MSMQ メッセージの移動、削除、または拒否の試行中にエラーが発生したことを示しています。  
  
 MSMQ メッセージは \(NetMsmqBinding または MsmqIntegrationBinding のどちらかを使用する場合に\) [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] で使用されます。このトレースは NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティで選択された値と関係しています。  
  
 このトレースはシステム全体についてのエラーを示すものではありません。  ただし、選択した有害メッセージの処置に失敗したことを示しています。  メッセージが有害となる場合の詳細、および有害メッセージをサービスで適切に処理するための構成方法については、「[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)」を参照してください。  
  
## 参照  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [トレースを使用したアプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)