---
title: "Windows Communication Foundation のトランスポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62eb27919e762004667b3d5179c35cb04d9a9422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation のトランスポート
トランスポート層は、チャネル スタックの最も低いレベルにあります。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で使用される主なトランスポートは、HTTP、HTTPS、TCP、および名前付きパイプです。 このセクションのトピックでは、このようなトランスポートの選択、トランスポートの構成、およびチューニング プロパティの設定について説明します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には追加のトランスポートが含まれています。 トランスポートのメッセージ キュー (MSMQ とも呼ばれます) については、次を参照してください。[キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)です。 ピア ツー ピアのトランスポートの詳細については、次を参照してください。[ピア ツー ピア ネットワー キング](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 3 つの主なトランスポートについて説明し、そのうちの 1 つを選択する際の考慮事項を示します。  
  
 [メッセージ エンコーダーを選択する](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 メッセージ エンコーディングのバインド要素を選択する際に考慮する必要のある要因について説明します。  
  
 [メッセージ転送ストリーミング](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 ストリーミングが行われるようにトランスポート層を構成する方法について説明します。  
  
 [HTTP および HTTPS の構成](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 HTTP および HTTPS トランスポート バインド要素の構成方法について説明します。  
  
 [方法 : WCF URL 予約を制限付きの予約に置き換える](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の URL 制限付き予約の使用方法について説明します。  
  
 [トランスポート クォータ](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 トランスポート層で使用できるクォータを設定する際の考慮事項について説明します。  
  
 [NAT とファイアウォールの使用](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 ファイアウォールを介してメッセージを送受信する場合や、ネットワーク アドレス交換 (NAT) が存在する場合にトランスポート層を構成する方法について説明します。  
  
 [Net.TCP ポート共有](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の Net.TCP ポート共有コンポーネントの使用方法について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>関連項目  
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)
