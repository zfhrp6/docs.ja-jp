---
title: "探索アナウンスとアナウンス クライアント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6da9c2e251a6592bb0af039d552d02e7e4fd3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="4f618-102">探索アナウンスとアナウンス クライアント</span><span class="sxs-lookup"><span data-stu-id="4f618-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="4f618-103">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の探索機能では、コンポーネントがその可用性をアナウンスできます。</span><span class="sxs-lookup"><span data-stu-id="4f618-103">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="4f618-104">そのように構成されている場合、サービスは Hello アナウンスと Bye アナウンスを送信します。</span><span class="sxs-lookup"><span data-stu-id="4f618-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="4f618-105">クライアントまたはその他のコンポーネントは、それらのアナウンス メッセージをリッスンして、対応します。</span><span class="sxs-lookup"><span data-stu-id="4f618-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="4f618-106">これにより、クライアントは別の手段でサービスを認識します。</span><span class="sxs-lookup"><span data-stu-id="4f618-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="4f618-107">アナウンス機能にはいくつかの用途があります。たとえば、サービスがネットワークに頻繁に出入りする場合は、サービスを検索するよりも、アナウンスを利用する方が効果的です。</span><span class="sxs-lookup"><span data-stu-id="4f618-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="4f618-108">この方法を使用すると、ネットワーク トラフィックが減少し、クライアントは、アナウンスを受信するとすぐに、そのサービスが存在するかどうかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="4f618-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="4f618-109">探索アナウンス</span><span class="sxs-lookup"><span data-stu-id="4f618-109">Discovery Announcements</span></span>  
 <span data-ttu-id="4f618-110">アナウンスが構成されたサービスがネットワークに参加し、探索可能になると、そのサービスは、リッスンしているクライアントにそのサービスの可用性をアナウンスする Hello メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="4f618-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="4f618-111">このメッセージには、サービスのコントラクト、エンドポイント アドレス、および関連付けられたスコープなど、探索関連の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f618-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="4f618-112">アナウンス メッセージを送信する先を <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> クラスで指定できます。</span><span class="sxs-lookup"><span data-stu-id="4f618-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="4f618-113">アナウンス エンドポイントが <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> の場合、Hello および Bye はマルチキャストです。また、アナウンス エンドポイントがユニキャストの場合、メッセージは指定されたエンドポイントに直接送信されます。</span><span class="sxs-lookup"><span data-stu-id="4f618-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f618-114">アナウンスは、サービス ホストが開いたときと閉じたときに送信されます。</span><span class="sxs-lookup"><span data-stu-id="4f618-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="4f618-115">これらの呼び出しが適切に終了しない場合は、アナウンス メッセージが送信されないことがあります。たとえば、サービスがエラーになった場合は、Bye アナウンス メッセージが送信されません。</span><span class="sxs-lookup"><span data-stu-id="4f618-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="4f618-116">アナウンス機能をカスタマイズして、選択したタイミングでアナウンスを送信することができます。</span><span class="sxs-lookup"><span data-stu-id="4f618-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="4f618-117"> では、<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> および <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> が標準エンドポイントとして定義されているため、サービスとクライアントが簡単に Hello アナウンスと Bye アナウンスを送信できます。</span><span class="sxs-lookup"><span data-stu-id="4f618-117"> defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="4f618-118">サービスのアナウンス</span><span class="sxs-lookup"><span data-stu-id="4f618-118">Announcements on the Service</span></span>  
 <span data-ttu-id="4f618-119">アナウンスを送信するようにサービスを構成するには、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> をアナウンス エンドポイントと共に追加します。</span><span class="sxs-lookup"><span data-stu-id="4f618-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="4f618-120">次の例は、この動作をプログラムでサービス ホストに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f618-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="4f618-121">この例では、アナウンスが、その標準エンドポイントで指定される場所へのマルチキャストであることを暗黙で示す `UdpAnnouncementEndpoint` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="4f618-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="4f618-122">この動作は、次の例に示すように、構成ファイルで構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f618-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
```xml  
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
 <span data-ttu-id="4f618-123">前の例では、サービスが自動的にアナウンス メッセージを送信するように構成します。</span><span class="sxs-lookup"><span data-stu-id="4f618-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="4f618-124"><xref:System.ServiceModel.Discovery.AnnouncementClient> クラスを使用して、アナウンス メッセージを明示的に送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="4f618-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="4f618-125">クライアントのアナウンス</span><span class="sxs-lookup"><span data-stu-id="4f618-125">Announcements on the Client</span></span>  
 <span data-ttu-id="4f618-126">クライアント アプリケーションは、アナウンス サービスをホストして Hello メッセージと Bye メッセージに応答し、<xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> イベントと <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> イベントを定期受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f618-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="4f618-127">その方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="4f618-127">The following example shows how to do this.</span></span>  
  
```  
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();
  
// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
  
// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{  
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();
  
    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}  
```  
  
 <span data-ttu-id="4f618-128">Hello メッセージまたは Bye メッセージを受信したら、次の例に示すように、<xref:System.ServiceModel.Discovery.AnnouncementEventArgs> を介してエンドポイント探索メタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4f618-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}
```
