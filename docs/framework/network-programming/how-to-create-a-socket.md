---
title: '方法: ソケットを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 600ea82965c332c8620db689abb50965f15f0067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396949"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="7e66b-102">方法: ソケットを作成する</span><span class="sxs-lookup"><span data-stu-id="7e66b-102">How to: Create a Socket</span></span>
<span data-ttu-id="7e66b-103">ソケットを使用してリモート デバイスと通信するには、ソケットをプロトコルとネットワーク アドレスの情報を使用して事前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e66b-103">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="7e66b-104"><xref:System.Net.Sockets.Socket> クラスのコンストラクターには、アドレス ファミリ、ソケットの種類、およびソケットが接続を行うために使用するプロトコルの種類を指定するパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="7e66b-104">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e66b-105">例</span><span class="sxs-lookup"><span data-stu-id="7e66b-105">Example</span></span>  
 <span data-ttu-id="7e66b-106">次の例では、インターネットなどの TCP/IP ベースのネットワーク上で通信するために使用できるソケットを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e66b-106">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="7e66b-107">TCP ではなく UDP を使用するには、次の例のように、プロトコルの種類を変更します。</span><span class="sxs-lookup"><span data-stu-id="7e66b-107">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="7e66b-108"><xref:System.Net.Sockets.AddressFamily> 列挙体では、ネットワーク アドレスを解決するために **Socket** クラスで使用される標準のアドレス ファミリを指定します (たとえば、**AddressFamily.InterNetwork** メンバーは IPv4 アドレス ファミリを指定します)。</span><span class="sxs-lookup"><span data-stu-id="7e66b-108">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="7e66b-109"><xref:System.Net.Sockets.SocketType> 列挙体ではソケットの種類を指定します (たとえば、**SocketType.Stream** メンバーは、フロー制御付きでデータを送受信するための標準のソケットを示します)。</span><span class="sxs-lookup"><span data-stu-id="7e66b-109">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="7e66b-110"><xref:System.Net.Sockets.ProtocolType> 列挙体では、**Socket** での通信時に使用するネットワーク プロトコルを指定します (たとえば、**ProtocolType.Tcp** はソケットが TCP を使用することを示し、**ProtocolType.Udp** はソケットが UDP を使用することを示します)。</span><span class="sxs-lookup"><span data-stu-id="7e66b-110">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="7e66b-111">**Socket** が作成されたら、リモート エンドポイントへの接続を開始したり、リモート デバイスから接続を受信したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e66b-111">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e66b-112">参照</span><span class="sxs-lookup"><span data-stu-id="7e66b-112">See Also</span></span>  
 [<span data-ttu-id="7e66b-113">クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="7e66b-113">Using Client Sockets</span></span>](../../../docs/framework/network-programming/using-client-sockets.md)  
 [<span data-ttu-id="7e66b-114">リッスン (ソケットで)</span><span class="sxs-lookup"><span data-stu-id="7e66b-114">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
