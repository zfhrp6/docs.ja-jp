---
title: TCP-UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 04a3bb1c7499a60175aaaa9715e780ea5ddceb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tcp-udp"></a><span data-ttu-id="b2eef-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="b2eef-102">TCP-UDP</span></span>
<span data-ttu-id="b2eef-103">アプリケーションは、<xref:System.Net.Sockets.TcpClient>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.UdpClient> クラスで伝送制御プロトコル (TCP) サービスとユーザー データグラム プロトコル (UDP) サービスを利用できます。</span><span class="sxs-lookup"><span data-stu-id="b2eef-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="b2eef-104">これらのプロトコルのクラスは <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> クラスの上に構築され、データ転送の詳細を処理します。</span><span class="sxs-lookup"><span data-stu-id="b2eef-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="b2eef-105">このプロトコル クラスは **Socket** クラスの同期メソッドを利用し、ネットワーク サービスへの簡単なアクセスを提供します。状態情報を維持する必要がなく、プロトコル特有のソケットを設定するための詳細を知る必要もありません。</span><span class="sxs-lookup"><span data-stu-id="b2eef-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="b2eef-106">非同期 **Socket** メソッドを使用するには、<xref:System.Net.Sockets.NetworkStream> クラスが提供する非同期メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b2eef-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="b2eef-107">プロトコル クラスでは公開されない **Socket** クラスの機能にアクセスするには、**Socket** クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2eef-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="b2eef-108">**TcpClient** と **TcpListener** は、**NetworkStream** クラスを利用するネットワークを表します。</span><span class="sxs-lookup"><span data-stu-id="b2eef-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="b2eef-109"><xref:System.Net.Sockets.TcpClient.GetStream%2A> メソッドを利用してネットワーク ストリームを返し、ストリームの <xref:System.Net.Sockets.NetworkStream.Read%2A> メソッドと <xref:System.Net.Sockets.NetworkStream.Write%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b2eef-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="b2eef-110">**NetworkStream** にはプロトコル クラスの基盤となるソケットがありません。そのため、閉じてもソケットに影響はありません。</span><span class="sxs-lookup"><span data-stu-id="b2eef-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="b2eef-111">**UdpClient** クラスはバイトの配列を利用し、UDP データグラムを保持します。</span><span class="sxs-lookup"><span data-stu-id="b2eef-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="b2eef-112"><xref:System.Net.Sockets.UdpClient.Send%2A> メソッドを利用してデータをネットワークに送信し、<xref:System.Net.Sockets.UdpClient.Receive%2A> メソッドを利用し、入ってくるデータグラムを受信します。</span><span class="sxs-lookup"><span data-stu-id="b2eef-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2eef-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2eef-113">See Also</span></span>  
 [<span data-ttu-id="b2eef-114">TCP サービスの使用</span><span class="sxs-lookup"><span data-stu-id="b2eef-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)  
 [<span data-ttu-id="b2eef-115">UDP サービスの使用</span><span class="sxs-lookup"><span data-stu-id="b2eef-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)  
 [<span data-ttu-id="b2eef-116">ネットワーク上のストリームの使用</span><span class="sxs-lookup"><span data-stu-id="b2eef-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="b2eef-117">非同期サーバー ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="b2eef-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [<span data-ttu-id="b2eef-118">非同期クライアント ソケットの使用</span><span class="sxs-lookup"><span data-stu-id="b2eef-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [<span data-ttu-id="b2eef-119">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="b2eef-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
