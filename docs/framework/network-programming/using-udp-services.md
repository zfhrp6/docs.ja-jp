---
title: "UDP サービスの使用"
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
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c535710175423ebd0d163edc9bce78cfb2e18168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-udp-services"></a><span data-ttu-id="08be3-102">UDP サービスの使用</span><span class="sxs-lookup"><span data-stu-id="08be3-102">Using UDP Services</span></span>
<span data-ttu-id="08be3-103"><xref:System.Net.Sockets.UdpClient> クラスは、UDP を使用してネットワーク サービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="08be3-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="08be3-104"><xref:System.Net.Sockets.UdpClient> クラスのプロパティとメソッドは、UDP を使用したデータの要求と受信用に <xref:System.Net.Sockets.Socket> を作成する詳細を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="08be3-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="08be3-105">ユーザー データグラム プロトコル (UDP) は、ベスト エフォートでリモート ホストにデータを配信する簡易プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="08be3-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="08be3-106">ただし、UDP プロトコルは接続プロトコルなので、リモート エンドポイントに送信された UDP データグラムの到達は保証されていません。また、送信されたときと同じ順序で到達することも保証されていません。</span><span class="sxs-lookup"><span data-stu-id="08be3-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="08be3-107">UDP を使用するアプリケーションには、データグラムの欠落、重複、順序の変更を処理する準備が必要です。</span><span class="sxs-lookup"><span data-stu-id="08be3-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="08be3-108">UDP を使用してデータグラムを送信するには、必要なサービスをホストするネットワーク デバイスのネットワーク アドレスと、サービスが通信に使用する UDP ポート番号を知っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="08be3-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="08be3-109">Internet Assigned Numbers Authority (IANA) は、一般的なサービスのポート番号を定義しています (www.iana.org/assignments/port-numbers を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="08be3-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="08be3-110">IANA の一覧に掲載されていないサービスが、1,024 から 65,535 の範囲のポート番号を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08be3-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="08be3-111">IP ベースのネットワークで UDP ブロードキャスト メッセージをサポートするために、特殊なネットワーク アドレスが使用されています。</span><span class="sxs-lookup"><span data-stu-id="08be3-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="08be3-112">次の説明では、例としてインターネット上で使用される IPv4 アドレスを使用しています。</span><span class="sxs-lookup"><span data-stu-id="08be3-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="08be3-113">IPv4 アドレスでは、32 ビットを使用してネットワーク アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="08be3-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="08be3-114">255.255.255.0 のネットマスクを使用するクラス C アドレスの場合、これらのビットは 4 オクテットに区切られます。</span><span class="sxs-lookup"><span data-stu-id="08be3-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="08be3-115">10 進数で表現する場合、4 オクテットで、192.168.100.2 などの使い慣れたドットで 4 つに区切った表記が形成されます。</span><span class="sxs-lookup"><span data-stu-id="08be3-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="08be3-116">最初の 2 つのオクテット (この例では 192.168) はネットワーク番号を形成し、3 番目のオクテット (100) はサブネットを定義し、最後のオクテット (2) はホスト識別子です。</span><span class="sxs-lookup"><span data-stu-id="08be3-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="08be3-117">IP アドレスのすべてのビットを 1、つまり 255.255.255.255 に設定すると、制限されたブロードキャスト アドレスが形成されます。</span><span class="sxs-lookup"><span data-stu-id="08be3-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="08be3-118">UDP データグラムをこのアドレスに設定すると、ローカル ネットワーク セグメント上のすべてのホストにメッセージが配信されます。</span><span class="sxs-lookup"><span data-stu-id="08be3-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="08be3-119">ルーターは、このアドレスに送信されたメッセージを転送しないため、ネットワーク セグメント上のホストのみがブロードキャスト メッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="08be3-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="08be3-120">ブロードキャストをネットワークの特定の部分に送信するには、ホスト識別子のすべてのビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="08be3-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="08be3-121">たとえば、192.168.1 から始まる IP アドレスで識別されるネットワーク上のすべてにホストにブロードキャストを送信するには、アドレス 192.168.1.255 を使用します。</span><span class="sxs-lookup"><span data-stu-id="08be3-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="08be3-122">次のコード例では、<xref:System.Net.Sockets.UdpClient> を使用して、ポート 11,000 上の指定されたブロードキャスト アドレス 192.168.1.255 に送信される UDP データグラムをリッスンしています。</span><span class="sxs-lookup"><span data-stu-id="08be3-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="08be3-123">クライアントは、メッセージ文字列を受信し、そのメッセージをコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="08be3-123">The client receives a message string and writes the message to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="08be3-124">次のコード例では、<xref:System.Net.Sockets.UdpClient> を使用して、ポート 11,000 を使用して、指定されたブロードキャスト アドレス 192.168.1.255 に UDP データグラムを送信しています。</span><span class="sxs-lookup"><span data-stu-id="08be3-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="08be3-125">クライアントは、コマンド ラインに指定されたメッセージ文字列を送信します。</span><span class="sxs-lookup"><span data-stu-id="08be3-125">The client sends the message string specified on the command line.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="08be3-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="08be3-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
