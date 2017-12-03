---
title: "スコープを使用した探索のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 184c4a5c31969ee060f72d937ab02af733340ca4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-with-scopes-sample"></a><span data-ttu-id="4be5f-102">スコープを使用した探索のサンプル</span><span class="sxs-lookup"><span data-stu-id="4be5f-102">Discovery with Scopes Sample</span></span>
<span data-ttu-id="4be5f-103">このサンプルでは、スコープを使用して、探索可能なエンドポイントを分類する方法、および <xref:System.ServiceModel.Discovery.DiscoveryClient> を使用して、エンドポイントの非同期検索を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-103">This sample shows how to use scopes to categorize discoverable endpoints as well how to use <xref:System.ServiceModel.Discovery.DiscoveryClient> to perform an asynchronous search for endpoints.</span></span> <span data-ttu-id="4be5f-104">サービスに関しては、エンドポイント探索動作を追加し、その動作を使用してエンドポイントにスコープを追加し、さらにエンドポイントの探索可能性を制御することによって、各エンドポイントの探索をカスタマイズする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-104">On the service, this sample shows how to customize discovery for each endpoint by adding an endpoint discovery behavior and using it to add a scope to the endpoint as well as controlling the endpoint’s discoverability.</span></span> <span data-ttu-id="4be5f-105">クライアントに関しては、<xref:System.ServiceModel.Discovery.DiscoveryClient> を作成し、<xref:System.ServiceModel.Discovery.FindCriteria> にスコープを追加してスコープが条件となるように検索パラメーターを最適に調整する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-105">On the client, the sample goes over how clients can create a <xref:System.ServiceModel.Discovery.DiscoveryClient> and fine tune search parameters to include scopes by adding scopes to the <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span> <span data-ttu-id="4be5f-106">また、終了条件を追加することによってクライアントで応答を制限する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-106">This sample also shows how clients can restrict responses by adding a termination criterion.</span></span>  
  
## <a name="service-features"></a><span data-ttu-id="4be5f-107">サービス機能</span><span class="sxs-lookup"><span data-stu-id="4be5f-107">Service Features</span></span>  
 <span data-ttu-id="4be5f-108">このプロジェクトでは、<xref:System.ServiceModel.ServiceHost> に 2 つのサービス エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-108">This project shows two service endpoints being added to a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="4be5f-109">各エンドポイントには <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> が関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="4be5f-109">Each endpoint has a <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> associated with it.</span></span> <span data-ttu-id="4be5f-110">この動作は、両方のエンドポイントの URI スコープを追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-110">This behavior is used to add URI scopes for both endpoints.</span></span> <span data-ttu-id="4be5f-111">スコープは、クライアントが検索を最適に調整できるように、これらのエンドポイントを区別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-111">Scopes are used to distinguish each of these endpoints so that the clients can fine tune the search.</span></span> <span data-ttu-id="4be5f-112">2 番目のエンドポイントについては、<xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> プロパティを `false` に設定して探索可能性を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4be5f-112">For the second endpoint, the discoverability can be disabled by setting the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> property to `false`.</span></span> <span data-ttu-id="4be5f-113">これにより、このエンドポイントに関連付けられている探索メタデータが探索メッセージの一部として送信されなくなります。</span><span class="sxs-lookup"><span data-stu-id="4be5f-113">This ensures that the discovery metadata associated with this endpoint is not sent as part of any discovery messages.</span></span>  
  
## <a name="client-features"></a><span data-ttu-id="4be5f-114">クライアント機能</span><span class="sxs-lookup"><span data-stu-id="4be5f-114">Client Features</span></span>  
 <span data-ttu-id="4be5f-115">`FindCalculatorServiceAddress()` メソッドは、<xref:System.ServiceModel.Discovery.DiscoveryClient> を使用し、2 つの制限が設定された <xref:System.ServiceModel.Discovery.FindCriteria> を渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-115">The `FindCalculatorServiceAddress()` method shows how to use a <xref:System.ServiceModel.Discovery.DiscoveryClient> and pass in a <xref:System.ServiceModel.Discovery.FindCriteria> with two restrictions.</span></span> <span data-ttu-id="4be5f-116">スコープを条件に追加し、<xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> プロパティを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-116">A scope is added to the criteria and the <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> property is set to 1.</span></span> <span data-ttu-id="4be5f-117">このスコープにより、同じスコープを公開するサービスのみに結果が限定されます。</span><span class="sxs-lookup"><span data-stu-id="4be5f-117">The scope limits the results to only the services that publish the same scope.</span></span> <span data-ttu-id="4be5f-118"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> を 1 に設定すると、<xref:System.ServiceModel.Discovery.DiscoveryClient> が待機する応答が最大で 1 つのエンドポイントに制限されます。</span><span class="sxs-lookup"><span data-stu-id="4be5f-118">Setting <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> to 1 limits the responses the <xref:System.ServiceModel.Discovery.DiscoveryClient> waits for to, at most, 1 endpoint.</span></span> <span data-ttu-id="4be5f-119"><xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> の呼び出しは、タイムアウトになるかエンドポイントが 1 つ見つかるまでスレッドをブロックする同期操作です。</span><span class="sxs-lookup"><span data-stu-id="4be5f-119">The <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> call is a synchronous operation that blocks the thread until a timeout is reached or one endpoint is found.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4be5f-120">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="4be5f-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="4be5f-121">このサンプルでは HTTP エンドポイントを使用します。このサンプルを実行するには、適切な URL ACL を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4be5f-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="4be5f-122">参照してください[を構成する HTTP および HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="4be5f-122">See [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="4be5f-123">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4be5f-123">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="4be5f-124">そのままではコマンドが動作しない場合は、代わりに、お使いのドメインとユーザー名を引数に指定して実行してみてください。`netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`</span><span class="sxs-lookup"><span data-stu-id="4be5f-124">You may want to substitute your Domain and Username for the following arguments if the command does not work as is: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`</span></span>  
  
2.  <span data-ttu-id="4be5f-125">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4be5f-125">Build the solution.</span></span>  
  
3.  <span data-ttu-id="4be5f-126">ビルド ディレクトリからサービス実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-126">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="4be5f-127">クライアント実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="4be5f-127">Run the client executable.</span></span> <span data-ttu-id="4be5f-128">クライアントでサービスを検索できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4be5f-128">Note that the client is able to locate the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4be5f-129">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4be5f-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4be5f-130">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4be5f-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4be5f-131">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="4be5f-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4be5f-132">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4be5f-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## <a name="see-also"></a><span data-ttu-id="4be5f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="4be5f-133">See Also</span></span>
