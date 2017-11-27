---
title: "同期サーバー ソケットの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- synchronous server sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- Socket class, synchronous server sockets
- protocols, sockets
- sockets, synchronous server sockets
- Internet, sockets
ms.assetid: d1ce882e-653e-41f5-9289-844ec855b804
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ce50fa5cf8664f93753312ee5f1db2b3058c3fd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-synchronous-server-socket"></a>同期サーバー ソケットの使用
同期サーバー ソケットは、ソケットで接続要求が受け取られるまでアプリケーションの実行を一時停止させます。 同期ソケットは動作のためにネットワークを多用するアプリケーションには適しませんが、単純なネットワーク アプリケーションには適しています。  
  
 <xref:System.Net.Sockets.Socket.Bind%2A> メソッドと <xref:System.Net.Sockets.Socket.Listen%2A> メソッドを利用してエンドポイントで待ち受けるように <xref:System.Net.Sockets.Socket> を設定したら、<xref:System.Net.Sockets.Socket.Accept%2A> メソッドを利用し、入ってくる接続要求を受け取る準備が完了となります。 **Accept** メソッドが呼び出されると、接続要求が受け取られるまで、アプリケーションは一時停止となります。  
  
 接続要求が受け取られると、**Accept** は、接続元のクライアントに関連付けられている新しい **Socket** インスタンスを返します。 次の例では、クライアントからデータを読み込み、コンソールに表示し、クライアントにデータをエコー バックしています。 **Socket** からは、いかなるメッセージング プロトコルも指定されません。そのため、文字列 "\<EOF>" はメッセージ データの終わりに印を付けます。 `listener` という名前の **Socket** が初期化され、エンドポイントにバインドされていると想定しています。  
  
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
  
## <a name="see-also"></a>関連項目  
 [非同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [同期サーバー ソケットの例](../../../docs/framework/network-programming/synchronous-server-socket-example.md)  
 [リッスン (ソケットで)](../../../docs/framework/network-programming/listening-with-sockets.md)
