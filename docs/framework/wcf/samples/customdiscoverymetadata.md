---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b3272b642a04821d8343cae776e48f90d266cfe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="6f876-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="6f876-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="6f876-103">このサンプルでは、サービスによって公開される探索可能なエンドポイントの探索メタデータにカスタム XML メタデータを挿入する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6f876-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="6f876-104">次に、クライアントがサービスを検索してこのカスタム データを抽出する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6f876-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="6f876-105">このサンプルは、2 つのプロジェクト (サービスとクライアント) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="6f876-106">サービス</span><span class="sxs-lookup"><span data-stu-id="6f876-106">Service</span></span>  
 <span data-ttu-id="6f876-107">サンプルの `main` メソッドでは、<xref:System.Xml.Linq.XElement> 型のオブジェクトに必要なフィールドが設定され、このオブジェクトが <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="6f876-108">この <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> が特定のエンドポイントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="6f876-109">この特定のエンドポイントが探索されると、ここで追加されたカスタム データが探索メタデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="6f876-110">Client</span><span class="sxs-lookup"><span data-stu-id="6f876-110">Client</span></span>  
 <span data-ttu-id="6f876-111">サンプルでは、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> で <xref:System.ServiceModel.Discovery.DiscoveryClient> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="6f876-112">次に、生成された <xref:System.ServiceModel.Discovery.FindResponse> に対して適切かつ必要な XML 要素が照会されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="6f876-113">その後、これらの要素がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6f876-114">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="6f876-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="6f876-115">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でプロジェクト ソリューションを読み込み、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="6f876-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="6f876-116">まず、[ソリューションの基本ディレクトリ]\service\bin\debug に生成されたサービス アプリケーションを実行します。次に、[ソリューションの基本ディレクトリ]\Client\bin\debug に生成されたクライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="6f876-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="6f876-117">サービスがオンラインになると、クライアントはサービスを検索し、エンドポイントで公開されているメタデータを出力します。</span><span class="sxs-lookup"><span data-stu-id="6f876-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f876-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f876-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6f876-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6f876-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6f876-120">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6f876-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f876-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6f876-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="6f876-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f876-122">See Also</span></span>
