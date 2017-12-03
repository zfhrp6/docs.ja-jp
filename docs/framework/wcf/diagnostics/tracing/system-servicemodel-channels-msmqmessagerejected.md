---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3194409ef6daf417d3643eed20afa18944e29ad3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ はメッセージを拒否しました。  
  
## <a name="description"></a>説明  
 このトレースは、MSMQ メッセージが拒否されたことを示します。  
  
 MSMQ メッセージは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] が (NetMsmqBinding または MsmqIntegrationBinding のいずれかを使用して) メッセージを処理できない場合に拒否されることがあります。 このようなメッセージは、有害メッセージと呼ばれます。 有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。 拒否されたメッセージは、送信者に送り返す配信[配信不能キュー](http://go.microsoft.com/fwlink/?LinkID=99544)です。  
  
 参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。  
  
 参照してください[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)拒否されたメッセージは MSMQ では意味の詳細についてはします。  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [トレースを使用して、アプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [有害メッセージ処理](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
