---
title: "方法: ソケットを作成する | Microsoft Docs"
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
  - "ネットワーク"
  - "送信 (データの)、ソケット"
  - "データ要求、ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "ソケット クラス、ソケットの作成"
  - "ネットワーク リソース"
  - "受信 (データの)、ソケット"
  - "プロトコル、ソケット"
  - "インターネット、ソケット"
  - "ソケット、作成"
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# 方法: ソケットを作成する
リモート デバイスと通信するためにソケットを使用するにはソケット プロトコルとネットワーク アドレス情報を初期化する必要があります。  <xref:System.Net.Sockets.Socket> クラスのコンストラクターはソケットが接続にするために使用する住所ファミリ、ソケットの型およびプロトコル タイプを指定するパラメータがあります。  
  
## 使用例  
 次の例では、TCP\/IP ベースのネットワークの通信に使用できるインターネットなどのソケットを作成します。  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
  
```  
  
 TCP にではなく、UDP を使用するには、次の例でプロトコル タイプを変更します:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
  
```  
  
 <xref:System.Net.Sockets.AddressFamily> の列挙型は、ネットワーク アドレスを決済するには **\[ソケット\]** クラスで使用される標準の住所のファミリーを指定します \(たとえば、**AddressFamily.InterNetwork** のメンバは、IP \(バージョン 4 の住所のファミリーを指定します。  
  
 <xref:System.Net.Sockets.SocketType> の列挙型はソケットのタイプを指定します \(たとえば、**SocketType.Stream** のメンバは、フロー制御して、データを送受信するための標準ソケットを表示します\)。  
  
 ソケットが TCP を使用することを <xref:System.Net.Sockets.ProtocolType> の **\[ソケット\]** の通信使用するネットワーク プロトコルをいつ指定します \(たとえば、**ProtocolType.Tcp** ;を表示します **ProtocolType.Udp** はソケットを UDP を使用することを示します。\)  
  
 **\[ソケット\]** が作成された後、エンドポイントへのリモート接続を開始またはデバイスのリモート接続を受け入れることができます。  
  
## 参照  
 [クライアント ソケットの使用](../../../docs/framework/network-programming/using-client-sockets.md)   
 [リッスン \(ソケットで\)](../../../docs/framework/network-programming/listening-with-sockets.md)