---
title: "重要なトレース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6641fe633585caf6cbf068a804430f9171e5ece0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="significant-traces"></a>重要なトレース
ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] によって出力される主要なトレースの一部を示します。  
  
## <a name="significant-traces"></a>重要なトレース  
  
|トレース|説明|  
|-----------|-----------------|  
|Message Log トレース|このトレースは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースが有効な場合に、メッセージ ログ機能によって `System.ServiceModel.MessageLogging` メッセージがログに記録されるときに出力されます。 このトレースをクリックすると、メッセージが表示されます。 メッセージには、構成可能なログ ポイントが 4 つ (`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。|  
|Message Received トレース|このトレースは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースが情報レベルまたは詳細レベルで有効な場合に、`System.ServiceModel` メッセージが受信されるときに出力されます。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Message Sent トレース|このトレースは [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースが Information レベルか Verbose レベルで有効な場合に、`System.ServiceModel` メッセージが送信されるときに出力されます。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Get ChannelEndpointElement|このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。 このトレースには、クライアントが対話しているエンドポイントの説明 (リモート アドレス、バインディング、コントラクト名など) が表示されます。|  
|Get ServiceElement|このトレースは、情報レベルで Construct サービス ホストに出力されます。 サービス コントラクトとバインディングの説明が提供されます。|  
|SocketConnection Create|このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。 ローカルとリモートの IP アドレスを提供します。 情報レベルで出力されます。|
