---
title: リッスン (ソケットで)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f85b63b151bcc20db635f56ec1dfec8df6c92241
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395779"
---
# <a name="listening-with-sockets"></a>リッスン (ソケットで)
リスナーまたはサーバー ソケットは、ネットワーク上のポートを開き、クライアントがそのポートに接続するまで待機します。 他のネットワーク アドレス ファミリとプロトコルもありますが、この例では、TCP/IP ネットワーク用のリモート サービスを作成する方法を説明します。  
  
 TCP/IP サービスの一意のアドレスは、ホストの IP アドレスとサービスのポート番号を組み合わせて、そのサービスのエンドポイントを作成することで定義します。 <xref:System.Net.Dns> クラスには、ローカル ネットワーク デバイスでサポートされているネットワーク アドレスに関する情報を返すメソッドがあります。 ローカル ネットワーク デバイスに複数のネットワーク アドレスがある場合、またはローカル システムが複数のネットワーク デバイスをサポートしている場合、**Dns** クラスは、すべてのネットワーク アドレスに関する情報を返します。また、アプリケーションはそのサービスに適切なアドレスを選択する必要があります。 Internet Assigned Numbers Authority (IANA) は、一般的なサービスのポート番号を定義しています (詳細については、www.iana.org/assignments/port-numbers を参照してください)。 他のサービスが、1,024 から 65,535 の範囲内でポート番号を登録している可能性があります。  
  
 次の例では、ホスト コンピューターの **Dns** から返される最初の IP アドレスと、登録されているポート番号範囲から選択されたポート番号を組み合わせて、サーバーの <xref:System.Net.IPEndPoint> を作成しています。  
  
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
  
 ローカル エンドポイントを決定した後、<xref:System.Net.Sockets.Socket.Bind%2A> メソッドを使用して <xref:System.Net.Sockets.Socket> をそのエンドポイントと関連付け、<xref:System.Net.Sockets.Socket.Listen%2A> メソッドを使用してエンドポイントをリッスンするように設定する必要があります。 特定のアドレスとポートの組み合わせが既に使用されている場合、**Bind** は例外をスローします。 **Socket** と **IPEndPoint** を関連付ける例を次に示します。  
  
```vb  
Dim listener As New Socket(ipAddress.AddressFamily, _  
    SocketType.Stream, ProtocolType.Tcp) 
listener.Bind(localEndPoint)  
listener.Listen(100)  
```  
  
```csharp  
Socket listener = new Socket(ipAddress.AddressFamily,
    SocketType.Stream, ProtocolType.Tcp);
listener.Bind(localEndPoint);  
listener.Listen(100);  
```  
  
 **Listen** メソッドには、**Socket** に対する保留中の接続数の上限を指定する 1 つのパラメーターがあります。この上限を超えると、サーバー ビジー エラーが接続クライアントに返されます。 この例では、接続キューに格納できるクライアント数の上限は 100 個で、クライアント番号 101 にはサーバー ビジー応答が返されます。  
  
## <a name="see-also"></a>参照  
 [同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [非同期サーバー ソケットの使用](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [クライアント ソケットの使用](../../../docs/framework/network-programming/using-client-sockets.md)  
 [方法: ソケットを作成する](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [ソケット](../../../docs/framework/network-programming/sockets.md)
