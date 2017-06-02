---
title: "リッスン (ソケットで) | Microsoft Docs"
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
  - "送信 (データの)、ソケット"
  - "ソケット、リッスン (ソケットで)"
  - "データ要求、ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "受信 (データの)、ソケット"
  - "プロトコル、ソケット"
  - "リッスン (ソケットで)"
  - "インターネット、ソケット"
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# リッスン (ソケットで)
リスナーまたはサーバーのはソケット ネットワークのポートを開き、そのポートに接続するクライアントを待機しています。  そのほかのネットワーク アドレスとプロトコル ファミリがあるが、この例に示します。TCP\/IP ネットワークのリモート サービスを作成する方法に。  
  
 TCP\/IP サービスの固有住所がサービス用にエンドポイントを作成するには、サービスのポート番号でホストの IP アドレスを組み合わせることによって定義されます。  <xref:System.Net.Dns> クラスは、ネットワーク住所に関する情報が返品のローカル ネットワーク上のデバイスによって支えた方法を提供します。  ローカル ネットワーク上のデバイスが複数のネットワーク アドレスが存在する場合、ローカル システムが複数のネットワーク デバイスをサポートしている場合、**\[DNS\]** のクラスがすべてのネットワーク アドレスに関する情報を返品、アプリケーションは、サービスの適切な住所を選択する必要があります。  インター ネット住所を \(Iana\) 管理、共通のサービスのポート番号を定義します \(詳細については、www.iana.org\/assignments\/port\-numbers\) を参照してください。  他のサービス範囲は 1,024 に 65,535 のポート番号を登録できます。  
  
 次の例では、ホスト コンピュータの **\[DNS\]** によって返された登録したポート番号から選択するポート番号によって最初の IP アドレスを組み合わせることによってサーバーの <xref:System.Net.IPEndPoint> 及びますを作成します。  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
```  
  
 保管場所のエンドポイントの決定したら、<xref:System.Net.Sockets.Socket> は <xref:System.Net.Sockets.Socket.Bind%2A> 方法、セットを使用してそのエンドポイントと <xref:System.Net.Sockets.Socket.Listen%2A> 方法を使用してエンドポイントにリッスンに関連付けられている必要があります。  **Bind** を必ず絶対アドレスとポートの組み合わせが既に使用中の場合は例外を投げます。  次の例では、**IPEndPoint**と **\[ソケット\]** を関連付けることを示します。  
  
```vb  
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 **Listen** 方法は、サーバーのビジーなエラーが接続をクライアントに戻る前に **\[ソケット\]** によって保留中の接続を割り当てるか指定する一つのパラメータを取ります。  この場合、100 文字までのクライアントが接続のキューにサーバーのビジー応答がクライアント 101 番目に戻る前に設定されます。  
  
## 参照  
 [同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)   
 [非同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [クライアント ソケットの使用](../../../docs/framework/network-programming/using-client-sockets.md)   
 [方法: ソケットを作成する](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [ソケット](../../../docs/framework/network-programming/sockets.md)