---
title: "アナウンスのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 485a5f98ead246b02aab4ffc5abebd5c88ea92dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="announcements-sample"></a><span data-ttu-id="1fa57-102">アナウンスのサンプル</span><span class="sxs-lookup"><span data-stu-id="1fa57-102">Announcements Sample</span></span>
<span data-ttu-id="1fa57-103">このサンプルでは、探索機能のアナウンス機能を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="1fa57-104">アナウンス機能を使用すると、サービスに関するメタデータを含むアナウンス メッセージをサービスから送信できます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="1fa57-105">既定では、サービスが開始されたときに Hello アナウンスが送信され、サービスがシャットダウンされたときに Bye アナウンスが送信されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="1fa57-106">これらのアナウンスは、マルチキャストすることも、Point-to-Point 送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="1fa57-107">このサンプルは、2 つのプロジェクト (サービスとクライアント) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="1fa57-108">サービス</span><span class="sxs-lookup"><span data-stu-id="1fa57-108">Service</span></span>  
 <span data-ttu-id="1fa57-109">このプロジェクトには、自己ホスト型の電卓サービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1fa57-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="1fa57-110">`Main` メソッドでは、サービス ホストが作成され、それにサービス エンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="1fa57-111">次に、<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="1fa57-112">アナウンスを有効にする場合は、アナウンス エンドポイントを <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fa57-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="1fa57-113">この場合、UDP マルチキャストを使用して、標準エンドポイントをアナウンス エンドポイントとして追加します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="1fa57-114">これにより、既知の UDP アドレスからアナウンスがブロードキャストされます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="1fa57-115">クライアント</span><span class="sxs-lookup"><span data-stu-id="1fa57-115">Client</span></span>  
 <span data-ttu-id="1fa57-116">このプロジェクトでは、クライアントが <xref:System.ServiceModel.Discovery.AnnouncementService> をホストすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1fa57-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="1fa57-117">また、2 つのデリゲートがイベントに登録されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="1fa57-118">これらのイベントにより、オンラインおよびオフラインのアナウンスを受信したときのクライアントの処理が決定されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="1fa57-119">`OnOnlineEvent` メソッドと `OnOfflineEvent` メソッドはそれぞれ、Hello アナウンス メッセージと Bye アナウンス メッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1fa57-120">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="1fa57-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="1fa57-121">このサンプルは、HTTP エンドポイントを使用して、このサンプルを適切な URL Acl を実行する必要があります追加を参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="1fa57-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="1fa57-122">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="1fa57-123">そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="1fa57-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="1fa57-124">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1fa57-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="1fa57-125">client.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="1fa57-126">service.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-126">Run the service.exe application.</span></span> <span data-ttu-id="1fa57-127">クライアントは、オンライン アナウンスを受信します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="1fa57-128">service.exe アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-128">Close the service.exe application.</span></span> <span data-ttu-id="1fa57-129">クライアントは、オフライン アナウンスを受信します。</span><span class="sxs-lookup"><span data-stu-id="1fa57-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fa57-130">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1fa57-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1fa57-131">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1fa57-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1fa57-132">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1fa57-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1fa57-133">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1fa57-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="1fa57-134">参照</span><span class="sxs-lookup"><span data-stu-id="1fa57-134">See Also</span></span>
