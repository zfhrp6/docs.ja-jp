---
title: "リッスン (ソケットで)"
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
- sending data, sockets
- sockets, listening with sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- protocols, sockets
- listening with sockets
- Internet, sockets
ms.assetid: 40e426cc-13db-4371-95eb-f7388bd23ebf
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6f96463b4f9cb7e61c403cfd77f747c8aefd99a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="listening-with-sockets"></a><span data-ttu-id="5e49f-102">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="5e49f-102">Listening with Sockets</span></span>
<span data-ttu-id="5e49f-103">リスナーまたはサーバー ソケットは、ネットワーク上のポートを開き、クライアントがそのポートに接続するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="5e49f-103">Listener or server sockets open a port on the network and then wait for a client to connect to that port.</span></span> <span data-ttu-id="5e49f-104">他のネットワーク アドレス ファミリとプロトコルもありますが、この例では、TCP/IP ネットワーク用のリモート サービスを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="5e49f-104">Although other network address families and protocols exist, this example shows how to create remote service for a TCP/IP network.</span></span>  
  
 <span data-ttu-id="5e49f-105">TCP/IP サービスの一意のアドレスは、ホストの IP アドレスとサービスのポート番号を組み合わせて、そのサービスのエンドポイントを作成することで定義します。</span><span class="sxs-lookup"><span data-stu-id="5e49f-105">The unique address of a TCP/IP service is defined by combining the IP address of the host with the port number of the service to create an endpoint for the service.</span></span> <span data-ttu-id="5e49f-106"><xref:System.Net.Dns> クラスには、ローカル ネットワーク デバイスでサポートされているネットワーク アドレスに関する情報を返すメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="5e49f-106">The <xref:System.Net.Dns> class provides methods that return information about the network addresses supported by the local network device.</span></span> <span data-ttu-id="5e49f-107">ローカル ネットワーク デバイスに複数のネットワーク アドレスがある場合、またはローカル システムが複数のネットワーク デバイスをサポートしている場合、**Dns** クラスは、すべてのネットワーク アドレスに関する情報を返します。また、アプリケーションはそのサービスに適切なアドレスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e49f-107">When the local network device has more than one network address, or if the local system supports more than one network device, the **Dns** class returns information about all network addresses, and the application must choose the proper address for the service.</span></span> <span data-ttu-id="5e49f-108">Internet Assigned Numbers Authority (IANA) は、一般的なサービスのポート番号を定義しています (詳細については、www.iana.org/assignments/port-numbers を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5e49f-108">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="5e49f-109">他のサービスが、1,024 から 65,535 の範囲内でポート番号を登録している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e49f-109">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="5e49f-110">次の例では、ホスト コンピューターの **Dns** から返される最初の IP アドレスと、登録されているポート番号範囲から選択されたポート番号を組み合わせて、サーバーの <xref:System.Net.IPEndPoint> を作成しています。</span><span class="sxs-lookup"><span data-stu-id="5e49f-110">The following example creates an <xref:System.Net.IPEndPoint> for a server by combining the first IP address returned by **Dns** for the host computer with a port number chosen from the registered port numbers range.</span></span>  
  
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
  
 <span data-ttu-id="5e49f-111">ローカル エンドポイントを決定した後、<xref:System.Net.Sockets.Socket.Bind%2A> メソッドを使用して <xref:System.Net.Sockets.Socket> をそのエンドポイントと関連付け、<xref:System.Net.Sockets.Socket.Listen%2A> メソッドを使用してエンドポイントをリッスンするように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e49f-111">After the local endpoint is determined, the <xref:System.Net.Sockets.Socket> must be associated with that endpoint using the <xref:System.Net.Sockets.Socket.Bind%2A> method and set to listen on the endpoint using the <xref:System.Net.Sockets.Socket.Listen%2A> method.</span></span> <span data-ttu-id="5e49f-112">特定のアドレスとポートの組み合わせが既に使用されている場合、**Bind** は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="5e49f-112">**Bind** throws an exception if the specific address and port combination is already in use.</span></span> <span data-ttu-id="5e49f-113">**Socket** と **IPEndPoint** を関連付ける例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5e49f-113">The following example demonstrates associating a **Socket** with an **IPEndPoint**.</span></span>  
  
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
  
 <span data-ttu-id="5e49f-114">**Listen** メソッドには、**Socket** に対する保留中の接続数の上限を指定する 1 つのパラメーターがあります。この上限を超えると、サーバー ビジー エラーが接続クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="5e49f-114">The **Listen** method takes a single parameter that specifies how many pending connections to the **Socket** are allowed before a server busy error is returned to the connecting client.</span></span> <span data-ttu-id="5e49f-115">この例では、接続キューに格納できるクライアント数の上限は 100 個で、クライアント番号 101 にはサーバー ビジー応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="5e49f-115">In this case, up to 100 clients are placed in the connection queue before a server busy response is returned to client number 101.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e49f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e49f-116">See Also</span></span>  
 [<span data-ttu-id="5e49f-117">同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="5e49f-117">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="5e49f-118">非同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="5e49f-118">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="5e49f-119">クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="5e49f-119">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="5e49f-120">方法: ソケットを作成する</span><span class="sxs-lookup"><span data-stu-id="5e49f-120">How to: Create a Socket</span></span>](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
 [<span data-ttu-id="5e49f-121">ソケット</span><span class="sxs-lookup"><span data-stu-id="5e49f-121">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
