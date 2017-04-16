---
title: "WCF と WebSocket | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF と WebSocket
.NET Framework 4.5 では、Windows Communication Foundation の WebSocket のサポートが導入されています。Websocket は、標準的な HTTP ポート 80 と 443 を介した双方向通信を有効にする効率的な標準ベース テクノロジです。標準 HTTP ポートを使用することで、Websocket は中継局を通じて Web 全体で通信できます。2 つの新しい標準バインディングが WebSocket トランスポート経由の通信をサポートするために追加されました。<xref:System.ServiceModel.NetHttpBinding> および <xref:System.ServiceModel.NetHttpsBinding>。WebSocket 固有の設定は、<xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> プロパティにアクセスして、<xref:> System.ServiceModel.Channels.HttpTransportBinding?qualifyHint=False&autoUpgrade=True 要素で構成できます。  
  
## このセクションの内容  
 [NetHttpBinding の使用](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <xref:System.ServiceModel.NetHttpBinding> とその構成方法について説明します。  
  
 [WebSockets 上で通信する WCF サービスを作成する用法](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Websocket 経由で通信する WCF サービスを作成する方法について説明します。  
  
## 関連項目  
  
## 関連項目