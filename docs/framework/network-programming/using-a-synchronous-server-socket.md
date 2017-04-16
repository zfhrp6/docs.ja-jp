---
title: "同期サーバー ソケットの使用 | Microsoft Docs"
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
  - "同期サーバー ソケット"
  - "送信 (データの)、ソケット"
  - "データ要求、ソケット"
  - "要求 (インターネットからデータを)、ソケット"
  - "サーバー ソケット"
  - "受信 (データの)、ソケット"
  - "ソケット クラス、非同期サーバー ソケット"
  - "プロトコル、ソケット"
  - "ソケット、同期サーバー ソケット"
  - "インターネット、ソケット"
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 同期サーバー ソケットの使用
サーバーの同期はソケット接続要求がソケットに入庫されるまでアプリケーションの実行を中断します。  サーバーの同期はソケット工程ネットワークの大量に使用できる、簡易ネットワーク アプリケーションに適してようにアプリケーションに適していない。  
  
 <xref:System.Net.Sockets.Socket> が <xref:System.Net.Sockets.Socket.Bind%2A> と <xref:System.Net.Sockets.Socket.Listen%2A> 方法を使用してエンドポイントのリッスンに設定されていると、<xref:System.Net.Sockets.Socket.Accept%2A> 方法を使用して接続順を承認すると、準備が整いました。  アプリケーションは **\[同意する\]** 方法が呼び出されたときに接続要求を受け取るまで中断されます。  
  
 接続要求を受け取った場合、**\[同意する\]** は、接続のクライアントに関連付けられている **\[ソケット\]** の新しいインスタンスを返します。  次の例は、クライアントからデータを読み、コンソールの表示、およびクライアントにデータを移動エコーします。  メッセージング プロトコルを **\[ソケット\]** は、その文字列「」\<EOF\>のマーキングをメッセージのデータ決算指定しません。  `listener`という **\[ソケット\]** をエンドポイントに初期化され、バインドされたとします。  
  
```vb  
Console.WriteLine("Waiting for a connection...")  
Dim handler As Socket = listener.Accept()  
Dim data As String = Nothing  
  
While True  
    bytes = New Byte(1024) {}  
    Dim bytesRec As Integer = handler.Receive(bytes)  
    data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
    If data.IndexOf("<EOF>") > - 1 Then  
        Exit While  
    End If  
End While  
  
Console.WriteLine("Text received : {0}", data)  
  
Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
handler.Send(msg)  
handler.Shutdown(SocketShutdown.Both)  
handler.Close()  
  
```  
  
```csharp  
Console.WriteLine("Waiting for a connection...");  
Socket handler = listener.Accept();  
String data = null;  
  
while (true) {  
    bytes = new byte[1024];  
    int bytesRec = handler.Receive(bytes);  
    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
    if (data.IndexOf("<EOF>") > -1) {  
        break;  
    }  
}  
  
Console.WriteLine( "Text received : {0}", data);  
  
byte[] msg = Encoding.ASCII.GetBytes(data);  
handler.Send(msg);  
handler.Shutdown(SocketShutdown.Both);  
handler.Close();  
```  
  
## 参照  
 [非同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)   
 [同期サーバー ソケットの例](../../../docs/framework/network-programming/synchronous-server-socket-example.md)   
 [リッスン \(ソケットで\)](../../../docs/framework/network-programming/listening-with-sockets.md)