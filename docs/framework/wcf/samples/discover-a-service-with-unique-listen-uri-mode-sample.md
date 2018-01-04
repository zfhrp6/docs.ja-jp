---
title: "一意の ListenUri モードのサンプルを使用したサービスの探索"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 017a14794dfb2cb2c49cc32df038600a984acf3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a><span data-ttu-id="a28c1-102">一意の ListenUri モードのサンプルを使用したサービスの探索</span><span class="sxs-lookup"><span data-stu-id="a28c1-102">Discover a Service with Unique Listen Uri Mode Sample</span></span>
<span data-ttu-id="a28c1-103">このサンプルでは、<xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> プロパティが <xref:System.ServiceModel.Description.ListenUriMode.Unique> に設定されているサービスを探索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a28c1-103">This sample demonstrates how to discover a service that has the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>.</span></span> <span data-ttu-id="a28c1-104"><xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> プロパティが <xref:System.ServiceModel.Description.ListenUriMode.Unique> に設定されている場合は、ポートを一意に設定するか、GUID を付加することによってパスを一意に設定して、ListenUri を一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a28c1-104">When the <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique>, the ListenUri is ensured to be unique by either setting the port to be unique or for the path to be unique by appending a GUID.</span></span>  
  
### <a name="features-on-the-service"></a><span data-ttu-id="a28c1-105">サービスの機能</span><span class="sxs-lookup"><span data-stu-id="a28c1-105">Features on the Service</span></span>  
 <span data-ttu-id="a28c1-106">TCP エンドポイントの <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> プロパティは、<xref:System.ServiceModel.Description.ListenUriMode.Unique> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-106">The <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> property is set to <xref:System.ServiceModel.Description.ListenUriMode.Unique> for the TCP endpoint.</span></span> <span data-ttu-id="a28c1-107">これにより、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> エンドポイントを介してサービスを探索できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a28c1-107">The service is then made discoverable over a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span>  
  
### <a name="features-on-the-client"></a><span data-ttu-id="a28c1-108">クライアントの機能</span><span class="sxs-lookup"><span data-stu-id="a28c1-108">Features on the Client</span></span>  
 <span data-ttu-id="a28c1-109">このクライアントは、適切な `Via.Uri` を使用してサービスに接続します。この際、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-109">This client connects to the service using the correct `Via.Uri` by using the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method.</span></span> <span data-ttu-id="a28c1-110">このメソッドから返された <xref:System.ServiceModel.Discovery.FindResponse> は、有効な <xref:System.ServiceModel.Endpoint.ListenUri%2A> を含んでいるかどうか、および `Address.Uri` とは異なるかどうかについて照会されます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-110">The <xref:System.ServiceModel.Discovery.FindResponse> that is returned from the method is then queried for whether it contains a valid <xref:System.ServiceModel.Endpoint.ListenUri%2A> and whether it is different than `Address.Uri`.</span></span> <span data-ttu-id="a28c1-111">適切な情報は `InvokeCalculatorService` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-111">The appropriate information is then passed to the `InvokeCalculatorService` method.</span></span> <span data-ttu-id="a28c1-112">`InvokeCalculatorService` メソッドでは、呼び出し元から <xref:System.ServiceModel.Endpoint.ListenUri%2A> が渡され、適切な `ClientViaBehavior` が設定された `Via.Uri` がクライアントのエンドポイントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-112">In the `InvokeCalculatorService` method, the <xref:System.ServiceModel.Endpoint.ListenUri%2A> was passed in by the caller, then a `ClientViaBehavior` with the correct `Via.Uri` is added to the client’s endpoint.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="a28c1-113">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a28c1-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="a28c1-114">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で、UniqueListenUriMode.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-114">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open UniqueListenUriMode.sln.</span></span>  
  
2.  <span data-ttu-id="a28c1-115">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a28c1-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a28c1-116">[ソリューションの基本ディレクトリ]\service\bin\debug フォルダーに生成されたサービス アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a28c1-116">Run the service application, which is generated in the [solution base directory]\service\bin\debug folder.</span></span>  
  
4.  <span data-ttu-id="a28c1-117">[ソリューションの基本ディレクトリ]\Client\bin\debug フォルダーに生成されたクライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a28c1-117">Run the client application, which is generated in the [solution base directory]\Client\bin\debug folder.</span></span>  
  
     <span data-ttu-id="a28c1-118">クライアントは実行中のサービスを検索し、サービスのエンドポイントで公開されているメタデータをコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-118">The client locates the running service and writes to the console the metadata published by the service’s endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a28c1-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a28c1-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a28c1-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a28c1-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a28c1-121">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a28c1-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a28c1-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a28c1-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a><span data-ttu-id="a28c1-123">参照</span><span class="sxs-lookup"><span data-stu-id="a28c1-123">See Also</span></span>
