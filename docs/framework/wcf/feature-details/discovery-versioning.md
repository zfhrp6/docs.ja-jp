---
title: "探索機能のバージョン指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 探索機能のバージョン指定
ここでは、新しい探索機能の実装の概要について簡単に説明します。  使用する探索バージョンを選択する方法の概要も示します。  
  
## 探索機能のバージョン指定  
 探索機能は、WS\_Discovery プロトコルの 3 つのバージョンをサポートします。  探索 API を使用すると、使用するプロトコルのバージョンを選択できます。  このドキュメントでは、バージョン指定に関連する設定について簡単に説明します。  
  
 次の Discovery クラスには <xref:System.ServiceModel.Discovery.DiscoveryVersion> プロパティがあり、コンストラクターで <xref:System.ServiceModel.Discovery.DiscoveryVersion> 引数を受け取ります。  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### DiscoveryVersion.WSDiscoveryApril2005  
 コンストラクターのパラメーターとして <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> を使用することで、WS\-Discovery プロトコルの April2005 バージョンが実装で使用されます。  このバージョンは、WS\-Discovery プロトコル仕様の発行済みバージョンに対応します。  このバージョンは、WS\-Discovery の April2005 バージョンを利用しているレガシ アプリケーションとの相互運用時に使用する必要があります。  
  
### DiscoveryVersion.WSDiscovery11  
 API で使用される既定の探索機能のバージョンは <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11> です。  これは、現在標準化されている WS\-Discovery プロトコルのバージョンです。  
  
## DiscoveryVersion.WSDiscoveryCD1  
 コンストラクターのパラメーターとして <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> を使用することで、WS\-Discovery プロトコルの Committee Draft 1 バージョンが実装で使用されます。  このバージョンのプロトコルは、WS\-Discovery プロトコルの CD1 バージョンを利用している実装との相互運用時に使用する必要があります。  
  
## 単一のサービス ホスト上にある異なる探索バージョン用の複数の UDP 探索エンドポイントのサポート  
 単一のサービス ホスト上にある、異なる探索バージョン用の複数の UDP 探索エンドポイントを公開する場合があります。  このような場合、UDP 探索エンドポイントごとに一意のアドレスを指定する必要があります。  その方法を次の例に示します。  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
  
```