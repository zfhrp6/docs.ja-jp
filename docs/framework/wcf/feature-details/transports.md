---
title: "Windows Communication Foundation のトランスポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "トランスポート [WCF]"
  - "WCF, トランスポート"
  - "Windows Communication Foundation, トランスポート"
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# Windows Communication Foundation のトランスポート
トランスポート層は、チャネル スタックの最も低いレベルにあります。[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で使用される主なトランスポートは、HTTP、HTTPS、TCP、および名前付きパイプです。このセクションのトピックでは、このようなトランスポートの選択、トランスポートの構成、およびチューニング プロパティの設定について説明します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には追加のトランスポートが含まれています。メッセージ キュー \(MSMQ とも呼ばれます\) については、「[キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)」を参照してください。ピアツーピア トランスポートについては、「[ピアツーピア ネットワーク](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)」を参照してください。  
  
## このセクションの内容  
 [トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 3 つの主なトランスポートについて説明し、そのうちの 1 つを選択する際の考慮事項を示します。  
  
 [メッセージ エンコーダーを選択する](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 メッセージ エンコーディングのバインド要素を選択する際に考慮する必要のある要因について説明します。  
  
 [メッセージ転送ストリーミング](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 ストリーミングが行われるようにトランスポート層を構成する方法について説明します。  
  
 [HTTP および HTTPS の構成](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 HTTP および HTTPS トランスポート バインド要素の構成方法について説明します。  
  
 [方法: WCF URL 予約を制限付きの予約に置き換える](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の URL 制限付き予約の使用方法について説明します。  
  
 [トランスポート クォータ](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 トランスポート層で使用できるクォータを設定する際の考慮事項について説明します。  
  
 [NAT とファイアウォールの使用](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 ファイアウォールを介してメッセージを送受信する場合や、ネットワーク アドレス交換 \(NAT\) が存在する場合にトランスポート層を構成する方法について説明します。  
  
 [Net.TCP ポート共有](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の Net.TCP ポート共有コンポーネントの使用方法について説明します。  
  
## 関連項目  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## 関連項目  
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)