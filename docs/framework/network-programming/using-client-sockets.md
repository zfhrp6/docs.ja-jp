---
title: "クライアント ソケットの使用 | Microsoft Docs"
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
  - "データ要求、ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "受信 (データの)、ソケット"
  - "ソケット クラス、クライアント ソケット"
  - "プロトコル、ソケット"
  - "インターネット、ソケット"
  - "ソケット、クライアント ソケット"
  - "クライアント ソケット"
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# クライアント ソケットの使用
<xref:System.Net.Sockets.Socket>によって通話内容を開始する前に、アプリケーションとリモート デバイス間でデータのパイプを作成する必要があります。  そのほかのネットワーク アドレスとプロトコル ファミリがあるが、この例に示します。サービスへのリモート接続 TCP\/IP を作成する方法に。  
  
 TCP\/IP は、ネットワーク アドレスとサービスを識別するためにサービスのポート番号を使用します。  ネットワーク アドレスは、ネットワークの特定のデバイスを識別します; ポート番号は、関連付ける場合は、そのデバイスの特定のサービスを識別します。  ネットワーク アドレス、およびサービスのポートの組み合わせが <xref:System.Net.EndPoint> クラスが .NET Framework で使用するエンドポイントと呼ばれます。  **EndPoint** その子孫は、サポート住所ファミリに対して定義です; IP アドレス ファミリについては、クラスは、<xref:System.Net.IPEndPoint>です。  
  
 <xref:System.Net.Dns> クラスには、TCP\/IP インターネット サービスを使用するアプリケーションにドメインの名前でサービスを提供します。  <xref:System.Net.Dns.Resolve%2A> 方法は、数値インターネット アドレスにわかりやすいのドメイン名を host.contoso.com \(「」など\) にマップします。DNS サーバーをクエリ \(192.168.1.1\)。  **Resolve** は [IPHostEnty](frlrfsystemnetiphostentryclasstopic) を返します要求された名前の住所とエイリアスの一覧が表示されます。  ほとんどの場合、<xref:System.Net.IPHostEntry.AddressList%2A> のアレイで再び最初の住所を使用できます。  次のコードは host.contoso.com サーバーの IP アドレスを含む <xref:System.Net.IPAddress> が表示されます。  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 インター ネット住所を \(Iana\) 管理、共通のサービスのポート番号を定義します \(詳細については、www.iana.org\/assignments\/port\-numbers\) を参照してください。  他のサービス範囲は 1,024 に 65,535 のポート番号を登録できます。  次のコードはポート番号がリモート接続のエンドポイントを作成するには、host.contoso.com の IP アドレスを連結します。  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 リモート デバイスの住所を決定する、接続に使用するポートを選択するとアプリケーションはリモート デバイスを使用して接続の設定を試みることができます。  次の例では、リモート デバイスに接続して既存の **IPEndPoint** を使用して、投げられる例外をつかまえます。  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## 参照  
 [同期クライアント ソケットの使用](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)   
 [非同期クライアント ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [方法: ソケットを作成する](../../../docs/framework/network-programming/how-to-create-a-socket.md)   
 [ソケット](../../../docs/framework/network-programming/sockets.md)