---
title: "TCP/UDP | Microsoft Docs"
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
  - "プロトコル、TCP/UDP"
  - "ネットワーク リソース、TCP/UDP"
  - "送信 (データを)、TCP/UDP"
  - "TCP/UDP"
  - "TcpClient クラス、TcpClient クラスの概要"
  - "アプリケーション プロトコル、TCP/UDP"
  - "受信 (データを)、TCP/UDP"
  - "TcpListener クラス、TcpListener クラスの概要"
  - "Socket クラス、Socket クラスの概要"
  - "UDP"
  - "データ要求、TCP/UDP"
  - "要求 (インターネットからデータを)、TCP/UDP"
  - "インターネット、TCP/UDP"
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# TCP/UDP
アプリケーションは、サービス <xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener>と <xref:System.Net.Sockets.UdpClient> クラスの伝送制御 Protocol \(TCP\) およびユーザー データグラム Protocol \(UDP\) の使用できます。  これらのプロトコル クラスは、<xref:System.Net.Sockets.Socket?displayProperty=fullName> クラスの上に構築、移動のデータの詳細を使用します。  
  
 プロトコル クラスは、管理のステータス情報やセキュリティ対応するソケットの設定の詳細を把握することの間接費なしでネットワーク サービスに簡単で、簡単なアクセスを提供するに **\[ソケット\]** クラスの同期方法を使用します。  への **\[ソケット\]** 非同期な方法を使用するには、<xref:System.Net.Sockets.NetworkStream> クラスによって指定された非同期な方法を使用できます。  **\[ソケット\]** への機能にアクセスするには、プロトコル クラスによって公開されていない **\[ソケット\]** クラスを使用して分類します。  
  
 **TcpClient** と **TcpListener** は **\[NetworkStream\]** クラスを使用してネットワークを表します。  ネットワーク ストリームを戻すために <xref:System.Net.Sockets.TcpClient.GetStream%2A> 方法を使用し、ベースの <xref:System.Net.Sockets.NetworkStream.Read%2A> と <xref:System.Net.Sockets.NetworkStream.Write%2A> 方法を追加します。  **\[NetworkStream\]** はプロトコル クラスの下にあるソケットを所有ので、それを閉じるにはソケットに影響しません。  
  
 **UdpClient** のクラスは、UDP データグラムを保留にバイトのアレイを使用します。  仕入データグラムを表示する場合は、ネットワーク、<xref:System.Net.Sockets.UdpClient.Receive%2A> 方法にデータを送信するに <xref:System.Net.Sockets.UdpClient.Send%2A> 方法を使用します。  
  
## 参照  
 [TCP サービスの使用](../../../docs/framework/network-programming/using-tcp-services.md)   
 [UDP サービスの使用](../../../docs/framework/network-programming/using-udp-services.md)   
 [ネットワーク上でストリームを使用する](../../../docs/framework/network-programming/using-streams-on-the-network.md)   
 [非同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [非同期クライアント ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)