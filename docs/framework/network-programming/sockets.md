---
title: "ソケット | Microsoft Docs"
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
  - "アプリケーション プロトコル、ソケット"
  - "送信 (データを)、ソケット"
  - "データ要求、ソケット"
  - "Windows ソケット"
  - "ソケット、ソケットの概要"
  - "Socket クラス、Socket クラスの概要"
  - "ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "ネットワーク、ソケット"
  - "受信 (データを)、ソケット"
  - "プロトコル、ソケット"
  - "インターネット、ソケット"
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# ソケット
<xref:System.Net.Sockets> の名前空間はソケット Windows インターフェイスの管理が適用されます。  <xref:System.Net> の名前空間のそのほかのネットワーク アクセスのすべてのクラスはソケットこの実装の先頭に基づきます。  
  
 .NET Framework の <xref:System.Net.Sockets.Socket> クラス API は Winsock32 によるソケットのサービス管理コードのバージョンです。  ほとんどの場合、**\[ソケット\]** クラスのメソッドはネイティブ Win32 の対応にデータを単にマーシャリングし、必要なセキュリティ検査を処理します。  
  
 **\[ソケット\]** のクラスが 2 基本モード、同期、非同期がサポートされます。  同期モードでは、決済を実行する機能への呼び出しは、ネットワーク アクション \(<xref:System.Net.Sockets.Socket.Send%2A> と <xref:System.Net.Sockets.Socket.Receive%2A>など\) 工程が呼び出されなかったのプログラムへ制御を行う前に完了するまで待機しています。  非同期モード リストで、これらの通話は、戻されます。  
  
## 参照  
 [方法: ソケットを作成する](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [TCP\/UDP](../../../docs/framework/network-programming/tcp-udp.md)   
 [アプリケーション プロトコルの使用](../../../docs/framework/network-programming/using-application-protocols.md)