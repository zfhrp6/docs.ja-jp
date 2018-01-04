---
title: "UDP トランスポートを使用するマルチキャスト アプリケーションの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57c30c8b6b381be931789f3f64cbd26943bb2b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="9009a-102">UDP トランスポートを使用するマルチキャスト アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="9009a-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="9009a-103">マルチキャスト アプリケーションは、ポイント ツー ポイント接続を確立することなく多数の受信者に小さいメッセージを同時に送信します。</span><span class="sxs-lookup"><span data-stu-id="9009a-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="9009a-104">このようなアプリケーションの重点は、信頼性よりも速度です。</span><span class="sxs-lookup"><span data-stu-id="9009a-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="9009a-105">つまり、特定のメッセージが実際に受信されるということよりも、迅速にデータを送信することの方が重要です。</span><span class="sxs-lookup"><span data-stu-id="9009a-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="9009a-106">WCF は、<xref:System.ServiceModel.UdpBinding> を使用して、書き込みマルチキャスト アプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="9009a-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="9009a-107">このトランスポートは、サービスが複数のクライアントに小さいメッセージを同時に送信する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="9009a-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="9009a-108">株価表示器のアプリケーションは、このようなサービスの例です。</span><span class="sxs-lookup"><span data-stu-id="9009a-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="9009a-109">マルチキャスト アプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="9009a-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="9009a-110">マルチキャストのアプリケーションを実装するには、サービス コントラクトを定義し、マルチキャストのメッセージに応答する必要がある各ソフトウェア コンポーネントについては、サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="9009a-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="9009a-111">たとえば、株価表示器のアプリケーションは、サービス コントラクトを定義する場合があります:</span><span class="sxs-lookup"><span data-stu-id="9009a-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```  
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="9009a-112">マルチキャストのメッセージを受信する各アプリケーションはこのインターフェイスを公開するサービスをホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9009a-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="9009a-113">たとえば、マルチキャストのメッセージを受信する方法を示すコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9009a-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```  
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="9009a-114">アプリケーションはすべてのサービスがリッスンする UDP アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9009a-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="9009a-115">新しい <xref:System.ServiceModel.ServiceHost> が作成され、サービス エンドポイントは <xref:System.ServiceModel.UdpBinding>を使用して公開されます。</span><span class="sxs-lookup"><span data-stu-id="9009a-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="9009a-116"><xref:System.ServiceModel.ServiceHost> が開き、受信メッセージをリッスンし始めます。</span><span class="sxs-lookup"><span data-stu-id="9009a-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="9009a-117">このような場合、実際にマルチキャストのメッセージを送信するのはクライアントです。</span><span class="sxs-lookup"><span data-stu-id="9009a-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="9009a-118">正しい UDP アドレスでリッスンする各サービスはマルチキャストのメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="9009a-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="9009a-119">マルチキャストのメッセージを送信するクライアントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9009a-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```  
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory 
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="9009a-120">このコードは、株式の情報を生成し、サービス コントラクト IStockTicker を使用してマルチキャストのメッセージを送信することによって、正しい UDP アドレスでリッスンするサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9009a-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="9009a-121">UDP および信頼できるメッセージング</span><span class="sxs-lookup"><span data-stu-id="9009a-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="9009a-122">UDP バインディングでは、UDP プロトコルに軽量という性質があるために信頼できるメッセージングをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="9009a-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="9009a-123">メッセージがリモート エンドポイントによって受信されることを確認する必要がある場合は、HTTP や TCP などの信頼できるメッセージングをサポートするトランスポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="9009a-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="9009a-124">信頼できるメッセージングの詳細については、http://go.microsoft.com/fwlink/?LinkId=231830 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9009a-124">For more information about reliable messaging see http://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="9009a-125">双方向マルチキャストのメッセージング</span><span class="sxs-lookup"><span data-stu-id="9009a-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="9009a-126">マルチキャストのメッセージは通常、一方向ですが、UdpBinding は要求または応答メッセージ交換をサポートします。</span><span class="sxs-lookup"><span data-stu-id="9009a-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="9009a-127">UDP トランスポートを使用して送信されたメッセージには送信者と宛先のアドレスの両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9009a-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="9009a-128">送信者のアドレスを使う場合は、送信中に悪意により変更されることがあるため、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="9009a-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="9009a-129">アドレスは、次のコードを使用してチェックすることができます。</span><span class="sxs-lookup"><span data-stu-id="9009a-129">The address can be checked using the following code:</span></span>  
  
```  
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="9009a-130">このコードは、送信者のアドレスの先頭バイトをチェックして、アドレスがマルチキャスト アドレスであることを示す 0xE0 が含まれているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="9009a-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="9009a-131">セキュリティの考慮事項</span><span class="sxs-lookup"><span data-stu-id="9009a-131">Security Considerations</span></span>  
 <span data-ttu-id="9009a-132">マルチキャストのメッセージをリッスンする場合、マルチキャストのアドレスでリッスンしていることを通知するルーターに ICMP パケットが送信されます。</span><span class="sxs-lookup"><span data-stu-id="9009a-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="9009a-133">アクセス許可を持つローカル サブネット上に存在するすべてのユーザーが、これらの型のパケットをリッスンし、リッスンしているマルチキャストのアドレスとポートを特定できます。</span><span class="sxs-lookup"><span data-stu-id="9009a-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="9009a-134">セキュリティ上の目的に送信者の IP アドレスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="9009a-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="9009a-135">この情報は偽装され、アプリケーションが間違ったコンピューターに応答を送信する原因となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9009a-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="9009a-136">この脅威を軽減する方法には、メッセージ レベルのセキュリティを有効にすることがあります。</span><span class="sxs-lookup"><span data-stu-id="9009a-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="9009a-137">ネットワーク レベルでは、IPsec (インターネット プロトコル セキュリティ) や NAP (ネットワーク アクセス保護) も使用できます。</span><span class="sxs-lookup"><span data-stu-id="9009a-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
