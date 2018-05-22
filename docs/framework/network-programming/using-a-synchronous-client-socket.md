---
title: 同期クライアント ソケットの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c9101957c6c4b9961ca5985bda8b8f82d69b45d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-synchronous-client-socket"></a><span data-ttu-id="d2c84-102">同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="d2c84-102">Using a Synchronous Client Socket</span></span>
<span data-ttu-id="d2c84-103">ネットワーク操作が完了するまで、同期クライアント ソケットはアプリケーション プログラムを一時停止させます。</span><span class="sxs-lookup"><span data-stu-id="d2c84-103">A synchronous client socket suspends the application program while the network operation completes.</span></span> <span data-ttu-id="d2c84-104">同期ソケットは動作のためにネットワークを多用するアプリケーションには適しませんが、それ以外のアプリケーションの場合、ネットワーク サービスへの簡単アクセスを可能にします。</span><span class="sxs-lookup"><span data-stu-id="d2c84-104">Synchronous sockets are not suitable for applications that make heavy use of the network for their operation, but they can enable simple access to network services for other applications.</span></span>  
  
 <span data-ttu-id="d2c84-105">データを送信するには、<xref:System.Net.Sockets.Socket> クラスのデータ送信メソッド (<xref:System.Net.Sockets.Socket.Send%2A> と <xref:System.Net.Sockets.Socket.SendTo%2A>) のいずれかにバイト配列を渡します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-105">To send data, pass a byte array to one of the <xref:System.Net.Sockets.Socket> class's send-data methods (<xref:System.Net.Sockets.Socket.Send%2A> and <xref:System.Net.Sockets.Socket.SendTo%2A>).</span></span> <span data-ttu-id="d2c84-106">次の例では、<xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> プロパティを利用してバイト配列バッファーに文字列をエンコードし、**Send** メソッドを利用してネットワーク デバイスにバッファーを送信しています。</span><span class="sxs-lookup"><span data-stu-id="d2c84-106">The following example encodes a string into a byte array buffer using the <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> property and then transmits the buffer to the network device using the **Send** method.</span></span> <span data-ttu-id="d2c84-107">**Send** メソッドは、ネットワーク デバイスに送信されたバイトの数を返します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-107">The **Send** method returns the number of bytes sent to the network device.</span></span>  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 <span data-ttu-id="d2c84-108">**Send** メソッドは、バッファーからバイトを取り除き、ネットワーク インターフェイスで、ネットワーク デバイスに送信するための待ち行列に入れます。</span><span class="sxs-lookup"><span data-stu-id="d2c84-108">The **Send** method removes the bytes from the buffer and queues them with the network interface to be sent to the network device.</span></span> <span data-ttu-id="d2c84-109">ネットワーク インターフェイスはデータをすぐには送信しないかもしれませんが、<xref:System.Net.Sockets.Socket.Shutdown%2A> メソッドで接続が通常どおり閉じられる限り、いずれは送信します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-109">The network interface might not send the data immediately, but it will send it eventually, as long as the connection is closed normally with the <xref:System.Net.Sockets.Socket.Shutdown%2A> method.</span></span>  
  
 <span data-ttu-id="d2c84-110">ネットワーク デバイスからデータを受け取るには、**Socket** クラスのデータ受信メソッド (<xref:System.Net.Sockets.Socket.Receive%2A> と <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>) のいずれかにバッファーを渡します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-110">To receive data from a network device, pass a buffer to one of the **Socket** class's receive-data methods (<xref:System.Net.Sockets.Socket.Receive%2A> and <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>).</span></span> <span data-ttu-id="d2c84-111">同期ソケットは、ネットワークからバイトが届くまで、あるいは、ソケットが閉じられるまで、アプリケーションを一時停止させます。</span><span class="sxs-lookup"><span data-stu-id="d2c84-111">Synchronous sockets will suspend the application until bytes are received from the network or until the socket is closed.</span></span> <span data-ttu-id="d2c84-112">次の例では、ネットワークからデータを受信し、コンソールに表示しています。</span><span class="sxs-lookup"><span data-stu-id="d2c84-112">The following example receives data from the network and then displays it on the console.</span></span> <span data-ttu-id="d2c84-113">この例では、ネットワークから届くデータが ASCII エンコード テキストであると想定しています。</span><span class="sxs-lookup"><span data-stu-id="d2c84-113">The example assumes that the data coming from the network is ASCII-encoded text.</span></span> <span data-ttu-id="d2c84-114">**Receive** メソッドは、ネットワークから受信したバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-114">The **Receive** method returns the number of bytes received from the network.</span></span>  
  
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
  
 <span data-ttu-id="d2c84-115">ソケットが不要になったら、解放する必要があります。<xref:System.Net.Sockets.Socket.Shutdown%2A> メソッドを呼び出し、**Close** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-115">When the socket is no longer needed, you need to release it by calling the <xref:System.Net.Sockets.Socket.Shutdown%2A> method and then calling the **Close** method.</span></span> <span data-ttu-id="d2c84-116">次の例では、**Socket** を解放しています。</span><span class="sxs-lookup"><span data-stu-id="d2c84-116">The following example releases a **Socket**.</span></span> <span data-ttu-id="d2c84-117"><xref:System.Net.Sockets.SocketShutdown> 列挙は、送信、受信、あるいは両方のためにソケットを閉じるかどうかを示す定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="d2c84-117">The <xref:System.Net.Sockets.SocketShutdown> enumeration defines constants that indicate whether the socket should be closed for sending, for receiving, or for both.</span></span>  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2c84-118">参照</span><span class="sxs-lookup"><span data-stu-id="d2c84-118">See Also</span></span>  
 [<span data-ttu-id="d2c84-119">非同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="d2c84-119">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="d2c84-120">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="d2c84-120">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="d2c84-121">同期クライアント ソケットの例</span><span class="sxs-lookup"><span data-stu-id="d2c84-121">Synchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
