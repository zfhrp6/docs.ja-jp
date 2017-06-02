---
title: "NetworkInformation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ネットワーク"
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# NetworkInformation
<xref:System.Net.NetworkInformation> の名前空間は、ネットワークのイベント、変更、統計量およびプロパティに関する情報を収集することができます。  また、リモート ホストが <xref:System.Net.NetworkInformation.Ping?displayProperty=fullName> クラスの使用によって到達可能にするかどうかを決定できます。  
  
## ネットワークの使用可能性とイベント  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=fullName> クラスは、ネットワーク アドレスまたは状態が変更されたかどうかを決定することができます。  このクラスを使用するには、変更を処理するようにイベント ハンドラーを作成および <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> または <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>としてを関連付けます。  詳細については、「[方法: ネットワークの可用性とアドレスの変更を検出する](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md)」を参照してください。  
  
## ネットワークの統計量およびプロパティ  
 インターフェイスまたはプロトコル基準のネットワーク統計量およびプロパティを集計できます。  <xref:System.Net.NetworkInformation.IPInterfaceProperties>、<xref:System.Net.NetworkInformation.IPGlobalProperties>、<xref:System.Net.NetworkInformation.IPGlobalStatistics>、<xref:System.Net.NetworkInformation.TcpStatistics>と <xref:System.Net.NetworkInformation.UdpStatistics> クラスは、レイヤー 3 と 4 のレイヤ パケットに関する情報を提供するが、<xref:System.Net.NetworkInformation.NetworkInterface>、<xref:System.Net.NetworkInformation.NetworkInterfaceType>と <xref:System.Net.NetworkInformation.PhysicalAddress> クラスは、特定のネットワークのインターフェイスに関する情報が表示されます。  詳細については、「[方法: インターフェイス情報とプロトコル情報を取得する](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md)」を参照してください。  
  
## リモート ホストが到達可能にするかどうかを決定します  
 リモートが、ネットワーク ホストは、到達高くなる可能かどうかを判断するために <xref:System.Net.NetworkInformation.Ping> クラスを使用できます。  詳細については、「[方法: ホストに対して ping を実行](../../../docs/framework/network-programming/how-to-ping-a-host.md)」を参照してください。  
  
## 参照  
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)   
 [ネットワークの情報技術個](http://go.microsoft.com/fwlink/?LinkID=179564)   
 [NetStat ツール テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179562)   
 [Ping のクライアント テクノロジのサンプル](http://go.microsoft.com/fwlink/?LinkID=179565)