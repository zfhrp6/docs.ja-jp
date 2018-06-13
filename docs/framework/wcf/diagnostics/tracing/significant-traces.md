---
title: 重要なトレース
ms.date: 03/30/2017
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
ms.openlocfilehash: c230c65b4d3fd45c4905d4ae5f4cbbf90e10faad
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804714"
---
# <a name="significant-traces"></a>重要なトレース
このトピックでは、Windows Communication Foundation (WCF) によって出力される主要なトレースの一部を示します。  
  
## <a name="significant-traces"></a>重要なトレース  
  
|トレース|説明|  
|-----------|-----------------|  
|Message Log トレース|WCF メッセージは、メッセージ ログで記録されたときに、トレースが出力されます機能、`System.ServiceModel.MessageLogging`トレース ソースが有効にします。 このトレースをクリックすると、メッセージが表示されます。 メッセージには、構成可能なログ ポイントが 4 つ (`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。|  
|Message Received トレース|場合、WCF メッセージを受信すると、このトレースが出力、`System.ServiceModel`トレース ソースが information レベルか verbose レベルで有効にします。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Message Sent トレース|場合、WCF メッセージが送信されるときにこのトレースが出力、`System.ServiceModel`トレース ソースが information レベルか verbose レベルで有効にします。 このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。|  
|Get ChannelEndpointElement|このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。 このトレースには、クライアントが対話しているエンドポイントの説明 (リモート アドレス、バインディング、コントラクト名など) が表示されます。|  
|Get ServiceElement|このトレースは、情報レベルで Construct サービス ホストに出力されます。 サービス コントラクトとバインディングの説明が提供されます。|  
|SocketConnection Create|このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。 ローカルとリモートの IP アドレスを提供します。 情報レベルで出力されます。|
