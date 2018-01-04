---
title: "SOAP エンドポイントおよび HTTP エンドポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef5059a886012c00d3d33327baeaae49a9d5b54c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="57207-102">SOAP エンドポイントおよび HTTP エンドポイント</span><span class="sxs-lookup"><span data-stu-id="57207-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="57207-103">このサンプルでは、RPC ベースのサービスを実装して、SOAP 形式で公開する方法と、"Plain Old XML"(POX) 形式を使用して、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web プログラミング モデルです。</span><span class="sxs-lookup"><span data-stu-id="57207-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming model.</span></span> <span data-ttu-id="57207-104">参照してください、[基本 HTTP サービス](../../../../docs/framework/wcf/samples/basic-http-service.md)サービス用の HTTP バインドの詳細についてはサンプルです。</span><span class="sxs-lookup"><span data-stu-id="57207-104">See the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="57207-105">このサンプルでは、さまざまなバインドを使用して SOAP および HTTP で RPC ベースのサービスを公開する方法について詳しく示します。</span><span class="sxs-lookup"><span data-stu-id="57207-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="57207-106">使用例</span><span class="sxs-lookup"><span data-stu-id="57207-106">Demonstrates</span></span>  
 <span data-ttu-id="57207-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用した SOAP および HTTP での RPC サービスの公開。</span><span class="sxs-lookup"><span data-stu-id="57207-107">Exposing an RPC service over SOAP and HTTP using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="57207-108">説明</span><span class="sxs-lookup"><span data-stu-id="57207-108">Discussion</span></span>  
 <span data-ttu-id="57207-109">このサンプルは、2 つのコンポーネントで構成されています。1 つは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを含む Web アプリケーション プロジェクト (Service) で、もう 1 つは SOAP バインドと HTTP バインドを使用してサービス操作を呼び出すコンソール アプリケーション (Client) です。</span><span class="sxs-lookup"><span data-stu-id="57207-109">This sample consists of two components: a Web Application project (Service) that contains a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="57207-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、入力として渡された文字列をエコーする、`GetData` と `PutData` の 2 つの操作を公開します。</span><span class="sxs-lookup"><span data-stu-id="57207-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="57207-111">サービス操作には、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用して注釈が付けられます。</span><span class="sxs-lookup"><span data-stu-id="57207-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="57207-112">これらの属性は、これらの操作の HTTP 投影を制御します。</span><span class="sxs-lookup"><span data-stu-id="57207-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="57207-113">また、サービス操作には、<xref:System.ServiceModel.OperationContractAttribute> を使用して注釈が付けられます。この属性では、サービス操作を SOAP バインディングで公開できます。</span><span class="sxs-lookup"><span data-stu-id="57207-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="57207-114">サービスの `PutData` メソッドは <xref:System.ServiceModel.Web.WebFaultException> をスローします。この例外は、HTTP では HTTP ステータス コードを使用して返送され、SOAP では SOAP エラーとして返送されます。</span><span class="sxs-lookup"><span data-stu-id="57207-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="57207-115">Web.config ファイルは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを次の 3 つのエンドポイントで設定します。</span><span class="sxs-lookup"><span data-stu-id="57207-115">The Web.config file configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with 3 endpoints:</span></span>  
  
-   <span data-ttu-id="57207-116">SOAP ベースのクライアントからアクセスするためのサービス メタデータを公開する ~/service.svc/mex エンドポイント</span><span class="sxs-lookup"><span data-stu-id="57207-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
-   <span data-ttu-id="57207-117">クライアントが HTTP バインディングを使用してサービスにアクセスできる ~/service.svc/http エンドポイント</span><span class="sxs-lookup"><span data-stu-id="57207-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
-   <span data-ttu-id="57207-118">クライアントが HTTP バインディングで SOAP を使用してサービスにアクセスできる ~/service.svc/soap endpoint エンドポイント</span><span class="sxs-lookup"><span data-stu-id="57207-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="57207-119">HTTP エンドポイントは、`webHttp` が `helpEnabled` に設定されている <`true`> 標準エンドポイントで設定されます。</span><span class="sxs-lookup"><span data-stu-id="57207-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="57207-120">その結果、サービスは、HTTP ベースのクライアントがサービスにアクセスするために使用できる、XHTML ベースのヘルプ ページ (~/service.svc/http/help) を公開します。</span><span class="sxs-lookup"><span data-stu-id="57207-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="57207-121">クライアント プロジェクトでは、SOAP プロキシを使用してサービスへのアクセスを示します (を通じて生成**サービス参照の追加**) を使用して、サービスへのアクセスと<xref:System.Net.WebClient>です。</span><span class="sxs-lookup"><span data-stu-id="57207-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="57207-122">サンプルは、1 つの Web ホスト サービスと 1 つのコンソール アプリケーションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="57207-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="57207-123">コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="57207-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="57207-124">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="57207-124">To run the sample</span></span>  
  
1.  <span data-ttu-id="57207-125">SOAP および HTTP エンドポイント サンプルのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="57207-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2.  <span data-ttu-id="57207-126">Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="57207-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="57207-127">これがまだ開いていない場合は ctrl キーを押しながら W キーと S を開くにはキーを押して、**ソリューション エクスプ ローラー**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="57207-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="57207-128">**ソリューション エクスプ ローラー**  ウィンドウを右クリックし、**サービス**プロジェクトし、カーソルを置きます、**デバッグ**コンテキスト メニュー オプションように、**新しい開始インスタンス**コンテキスト メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="57207-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="57207-129">をクリックして**新しいインスタンスを開始**です。</span><span class="sxs-lookup"><span data-stu-id="57207-129">Click **Start New Instance**.</span></span> <span data-ttu-id="57207-130">これで、サービスをホストする ASP.NET 開発サーバーが起動します。</span><span class="sxs-lookup"><span data-stu-id="57207-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="57207-131">ソリューション エクスプ ローラーのウィンドウからクライアント プロジェクトを右クリックし、カーソルを置きます、**デバッグ**コンテキスト メニュー オプションように、**新しいインスタンスを開始**コンテキスト メニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="57207-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="57207-132">をクリックして**新しいインスタンスを開始**です。</span><span class="sxs-lookup"><span data-stu-id="57207-132">Click **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="57207-133">クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。</span><span class="sxs-lookup"><span data-stu-id="57207-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="57207-134">ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="57207-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="57207-135">サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="57207-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="57207-136">クライアント コンソール アプリケーションを終了するには、任意のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="57207-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="57207-137">サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="57207-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="57207-138">Windows 通知領域には、ASP.NET 開発サーバーのアイコンを右クリックして**停止**コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="57207-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57207-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="57207-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="57207-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="57207-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="57207-141">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="57207-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57207-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="57207-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
