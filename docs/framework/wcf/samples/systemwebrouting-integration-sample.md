---
title: "SystemWebRouting 統合サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1718ea9c6ea1e029b66955e88fd54e20db1a3527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="b4fc6-102">SystemWebRouting 統合サンプル</span><span class="sxs-lookup"><span data-stu-id="b4fc6-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="b4fc6-103">このサンプルでは、<xref:System.Web.Routing> 名前空間のクラスとのホスト層の統合を示します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="b4fc6-104"><xref:System.Web.Routing> 名前空間のクラスを使用すると、物理リソースに直接対応しない URL をアプリケーションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="b4fc6-105">開発者は Web ルーティングを使用することで、後で実際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにマップされる HTTP の仮想アドレスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="b4fc6-106">これは、物理ファイルやリソースを配置せずに WCF サービスをホストする必要がある場合、または .html や .aspx などのファイルがない URL を使用してサービスにアクセスする必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="b4fc6-107">このサンプルでは、<xref:System.Web.Routing.RouteTable> クラスを使用して、global.asax で定義された実行中のサービスにマップされる仮想 URI を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="b4fc6-108">この例では、`movies` フィードと `channels` フィードという、WCF を使用して作成された 2 つの RSS フィードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="b4fc6-109">拡張機能が含まれていないおよびに登録されているサービスをアクティブ化する Url、`Application_Start`のメソッド、`Global`から派生したクラス、<xref:System.Web.HttpApplication.Application_Start>クラスです。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4fc6-110"><xref:System.Web.Routing> 名前空間のクラスは、HTTP でホストされるサービスに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4fc6-111">このサンプルは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] でのみ機能します。[!INCLUDE[iis60](../../../../includes/iis60-md.md)] では、拡張子がない URL を別の方法でサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4fc6-112">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b4fc6-113">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b4fc6-114">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4fc6-115">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b4fc6-116">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="b4fc6-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="b4fc6-117">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、WebRoutingIntegration.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="b4fc6-118">ソリューションを実行して Web 開発サーバーを起動するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="b4fc6-119">サンプルのディレクトリの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="b4fc6-120">ファイル拡張子が .svc のファイルがないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="b4fc6-121">アドレス バーで、URL が http://localhost:[port]/movies の形式になるように `movies` を追加し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="b4fc6-122">movies フィードがブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="b4fc6-123">アドレス バーで、URL が http://localhost:[port]/channels の形式になるように `channels` を追加し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="b4fc6-124">channels フィードがブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="b4fc6-125">Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="b4fc6-126">開発サーバーがまだ終了していない場合、通知エリア アイコンを右クリックし **停止**です。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="b4fc6-127">このサンプルを使用するには (IIS でホストする場合)</span><span class="sxs-lookup"><span data-stu-id="b4fc6-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="b4fc6-128">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、WebRoutingIntegration.sln ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="b4fc6-129">Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b4fc6-130">インターネット インフォメーション サービス (IIS) マネージャーで Web アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="b4fc6-131">IIS マネージャーで、右クリックして、**既定の Web サイト**選択**アプリケーションを追加**です。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="b4fc6-132">**エイリアス**、入力`WebRoutingIntegration`です。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="b4fc6-133">**物理パス**プロジェクト内の Service フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="b4fc6-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4fc6-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="b4fc6-135">Web アプリケーションを右クリックしてアプリケーションを起動**アプリケーションの管理**し**参照**です。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="b4fc6-136">アドレス バーで、URL が http://localhost:[port]/movies の形式になるように `movies` を追加し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="b4fc6-137">movies フィードがブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="b4fc6-138">アドレス バーで、URL が http://localhost:[port]/channels の形式になるように `channels` を追加し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="b4fc6-139">channels フィードがブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="b4fc6-140">Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="b4fc6-141">このサンプルは、HTTP でホストされたサービスの要求をルーティングするために、<xref:System.Web.Routing> 名前空間のクラスを使用してホスト層を構成できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4fc6-142">既定のアプリケーション プールのバージョンが 2 に設定されている場合は、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] に更新してください。</span><span class="sxs-lookup"><span data-stu-id="b4fc6-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fc6-143">参照</span><span class="sxs-lookup"><span data-stu-id="b4fc6-143">See Also</span></span>  
 [<span data-ttu-id="b4fc6-144">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="b4fc6-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
