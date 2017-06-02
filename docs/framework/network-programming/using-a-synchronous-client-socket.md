---
title: "同期クライアント ソケットの使用 | Microsoft Docs"
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
  - "同期クライアント ソケット"
  - "Socket クラス、同期クライアント ソケット"
  - "受信 (データの)、ソケット"
  - "ソケット、同期クライアント ソケット"
  - "プロトコル、ソケット"
  - "インターネット、ソケット"
  - "クライアント ソケット"
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 同期クライアント ソケットの使用
クライアントの同期はソケット ネットワーク アクションが完了すると、アプリケーション プログラムを中断します。  同期はソケット工程のネットワーク大量に使用できる、他のアプリケーションのネットワーク サービスへの簡単なアクセスできるようにすることもできますアプリケーションに適していない。  
  
 データを送信するには、<xref:System.Net.Sockets.Socket> クラスの送信データの方法のうち 1 バイトを配列に出荷します \(<xref:System.Net.Sockets.Socket.Send%2A> と <xref:System.Net.Sockets.Socket.SendTo%2A>\)。  次の例では、<xref:System.Text.Encoding.ASCII%2A?displayProperty=fullName> のプロパティを使用してバイト配列のバッファ、文字列をエンコードし、ネットワークのデバイスに **\[送信\]** 方法を使用してバッファを送信します。  **\[送信\]** 方法は、ネットワークのデバイスに送信されるバイト数を返します。  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **\[送信\]** 方法はバッファからバイトが削除され、ネットワークのデバイスに送信されるネットワークのインターフェイスでの列を作らせます。  接続が <xref:System.Net.Sockets.Socket.Shutdown%2A> 方法として通常、終了、ネットワークのインターフェイスはデータを直ちになく場合がありますが、最終的を送信します。  
  
 ネットワークのデバイスからデータを取得するには、**\[ソケット\]** クラスの受信データ メソッドのバッファを 1 に出荷します \(<xref:System.Net.Sockets.Socket.Receive%2A> と <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>\)。  同期はバイト ソケットがネットワークから入庫またはソケットが閉じられるまでアプリケーションを中断します。  次の例では、ネットワーク、表示のデータをコンソールで表示されます。  たとえば、ネットワークから送られてくるデータが ASCII エンコードしたテキストであるとします。  **\[受信\]** 方法は、ネットワークから受け取ったバイト数を返します。  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 ソケットが不要にしない場合、<xref:System.Net.Sockets.Socket.Shutdown%2A> 方法を追加し、**\[閉じる\]** 方法をとしてそれをリリースする必要があります。  次の例では、**\[ソケット\]**をリリースします。  <xref:System.Net.Sockets.SocketShutdown> の列挙型はソケット、受け入れた送信については、またはの両方に終了するかどうかを指定する定数を定義します。  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## 参照  
 [非同期クライアント ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)   
 [リッスン \(ソケットで\)](../../../docs/framework/network-programming/listening-with-sockets.md)   
 [同期クライアント ソケットの例](../../../docs/framework/network-programming/synchronous-client-socket-example.md)