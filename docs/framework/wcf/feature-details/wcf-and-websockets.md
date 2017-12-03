---
title: "WCF と WebSocket"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 225bff20f514a653382f01becf133659dec4c5f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-websockets"></a>WCF と WebSocket
.NET Framework 4.5 では、Windows Communication Foundation の WebSocket のサポートが導入されています。  Websocket は、標準的な HTTP ポート 80 と 443 を介した双方向通信を有効にする効率的な標準ベース テクノロジです。 標準 HTTP ポートを使用することで、Websocket は中継局を通じて Web 全体で通信できます。  2 つの新しい標準バインディングが WebSocket トランスポート経由の通信をサポートするために追加されました。 <xref:System.ServiceModel.NetHttpBinding> および <xref:System.ServiceModel.NetHttpsBinding>。 Websocket 固有の設定を構成できます、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>にアクセスして、<xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A>プロパティです。
  
## <a name="in-this-section"></a>このセクションの内容  
 [NetHttpBinding の使用](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <xref:System.ServiceModel.NetHttpBinding> とその構成方法について説明します。  
  
 [方法: Websocket 経由で通信する WCF サービスの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Websocket 経由で通信する WCF サービスを作成する方法について説明します。  
  
## <a name="reference"></a>参照  
  
## <a name="related-sections"></a>関連項目
