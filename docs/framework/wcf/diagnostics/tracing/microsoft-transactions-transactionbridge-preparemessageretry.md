---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8199398e4e0bfe8ad42f6c8ba8adb11e883236e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a>Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
応答しない参加要素に、準備メッセージの再試行が送信されました。  
  
## <a name="description"></a>説明  
 ローカル トランザクション マネージャーが一定時間内に応答を受信せず、下位の参加要素に準備メッセージを再送信する必要があった場合にトレースされます。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。  このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。 いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下する場合があります。  
  
## <a name="see-also"></a>関連項目  
 [トレース](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [トレースを使用して、アプリケーションのトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理と診断](../../../../../docs/framework/wcf/diagnostics/index.md)
