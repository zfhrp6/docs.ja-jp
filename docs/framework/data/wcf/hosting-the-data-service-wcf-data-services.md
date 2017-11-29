---
title: "データ サービスのホスティング (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a11e7e499f705f4aace791320057e04205db58c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-the-data-service-wcf-data-services"></a><span data-ttu-id="fc55d-102">データ サービスのホスティング (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="fc55d-102">Hosting the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="fc55d-103">使用して[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]、としてデータを公開するサービスを作成することができます、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。</span><span class="sxs-lookup"><span data-stu-id="fc55d-103">By using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can create a service that exposes data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="fc55d-104">このデータ サービスは、<xref:System.Data.Services.DataService%601> から継承されたクラスとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-104">This data service is defined as a class that inherits from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="fc55d-105">このクラスは、要求メッセージを処理、データ ソースに対する更新を実行に必要なの応答メッセージの生成に必要な機能を提供[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="fc55d-105">This class provides the functionality required to process request messages, perform updates against the data source, and generate responses messages, as required by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="fc55d-106">ただし、データ サービスにバインドできず着信 HTTP 要求のネットワーク ソケットでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="fc55d-106">However, a data service cannot bind to and listen on a network socket for incoming HTTP requests.</span></span> <span data-ttu-id="fc55d-107">この機能要件のため、データ サービスはホスティング コンポーネントに依存します。</span><span class="sxs-lookup"><span data-stu-id="fc55d-107">For this required functionality, the data service relies on a hosting component.</span></span>  
  
 <span data-ttu-id="fc55d-108">データ サービス ホストは、データ サービスに代わって次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="fc55d-108">The data service host performs the following tasks on behalf of the data service:</span></span>  
  
-   <span data-ttu-id="fc55d-109">要求をリッスンし、その要求をデータ サービスにルーティングする。</span><span class="sxs-lookup"><span data-stu-id="fc55d-109">Listens for requests and routes these requests to the data service.</span></span>  
  
-   <span data-ttu-id="fc55d-110">要求ごとにデータ サービスのインスタンスを作成する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-110">Creates an instance of the data service for each request.</span></span>  
  
-   <span data-ttu-id="fc55d-111">受信要求を処理するようデータ サービスに要求する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-111">Requests that the data service process the incoming request.</span></span>  
  
-   <span data-ttu-id="fc55d-112">データ サービスに代わって応答を送信する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-112">Sends the response on behalf of the data service.</span></span>  
  
 <span data-ttu-id="fc55d-113">データ サービスのホストを簡単に[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Windows Communication Foundation (WCF) を統合するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="fc55d-113">To simplify hosting a data service, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] is designed to integrate with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="fc55d-114">データ サービスでデータ サービス ホストとして機能する既定の WCF 実装を提供する、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="fc55d-114">The data service provides a default WCF implementation that serves as the data service host in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="fc55d-115">そのため、次のいずれかの方法でデータ サービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-115">Therefore, you can host a data service in one of the following ways:</span></span>  
  
-   <span data-ttu-id="fc55d-116">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fc55d-116">In an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
-   <span data-ttu-id="fc55d-117">自己ホスト型 WCF サービスをサポートするマネージ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="fc55d-117">In a managed application that supports self-hosted WCF services.</span></span>  
  
-   <span data-ttu-id="fc55d-118">その他のカスタム データ サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="fc55d-118">In some other custom data service host.</span></span>  
  
## <a name="hosting-a-data-service-in-an-aspnet-application"></a><span data-ttu-id="fc55d-119">ASP.NET アプリケーションでのデータ サービスのホスト</span><span class="sxs-lookup"><span data-stu-id="fc55d-119">Hosting a Data Service in an ASP.NET Application</span></span>  
 <span data-ttu-id="fc55d-120">使用すると、**新しい項目の追加** ダイアログ ボックス、ツール、ASP.NET アプリケーションでデータ サービスを定義する Visual Studio プロジェクトに 2 つの新しいファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-120">When you use the **Add New Item** dialog in Visual Studio to define a data service in an ASP.NET application, the tool generates two new files in the project.</span></span> <span data-ttu-id="fc55d-121">そのうち一方のファイル (拡張子は `.svc`) は、データ サービスのインスタンス化方法を WCF ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="fc55d-121">The first file has a `.svc` extension and instructs the WCF runtime how to instantiate the data service.</span></span> <span data-ttu-id="fc55d-122">完了したときに作成された Northwind サンプル データ サービスに対して、このファイルの例を次に示します、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span><span class="sxs-lookup"><span data-stu-id="fc55d-122">The following is an example of this file for the Northwind sample data service created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):</span></span>  
  
```  
<%@ ServiceHost Language="C#"   
    Factory="System.Data.Services.DataServiceHostFactory,   
            System.Data.Services, Version=4.0.0.0,   
            Culture=neutral, PublicKeyToken=b77a5c561934e089"   
    Service="NorthwindService.Northwind" %>   
```  
  
 <span data-ttu-id="fc55d-123">このディレクティブは、<xref:System.Data.Services.DataServiceHostFactory> クラスを使用して、名前付きのデータ サービス クラスのサービス ホストを作成するようアプリケーションに指示します。</span><span class="sxs-lookup"><span data-stu-id="fc55d-123">This directive tells the application to create the service host for the named data service class by using the <xref:System.Data.Services.DataServiceHostFactory> class.</span></span>  
  
 <span data-ttu-id="fc55d-124">`.svc` ファイルの分離コード ページには、データ サービス自体の実装であるクラスが含まれます。Northwind サンプル データ サービスの場合、このクラスは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-124">The code-behind page for the `.svc` file contains the class that is the implementation of the data service itself, which is defined as follows for the Northwind sample data service:</span></span>  
  
 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
 <span data-ttu-id="fc55d-125">データ サービスは WCF サービスと同様に動作するため、データ サービスは [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と統合され、WCF Web プログラミング モデルに従います。</span><span class="sxs-lookup"><span data-stu-id="fc55d-125">Because a data service behaves like a WCF service, the data service integrates with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] and follows the WCF Web programming model.</span></span> <span data-ttu-id="fc55d-126">詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)と[WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc55d-126">For more information, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) and [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>  
  
## <a name="self-hosted-wcf-services"></a><span data-ttu-id="fc55d-127">自己ホスト型 WCF サービス</span><span class="sxs-lookup"><span data-stu-id="fc55d-127">Self-Hosted WCF Services</span></span>  
 <span data-ttu-id="fc55d-128">WCF の実装が組み込まれている[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]自己ホスト型 WCF サービスとしてデータ サービスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fc55d-128">Because it incorporates a WCF implementation, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] support self-hosting a data service as a WCF service.</span></span> <span data-ttu-id="fc55d-129">サービスは、コンソール アプリケーションなどの任意の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションで自己ホスト型とすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-129">A service can be self-hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, such as a console application.</span></span> <span data-ttu-id="fc55d-130"><xref:System.Data.Services.DataServiceHost> を継承する <xref:System.ServiceModel.Web.WebServiceHost> クラスを使用して、特定のアドレスでデータ サービスをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="fc55d-130">The <xref:System.Data.Services.DataServiceHost> class, which inherits from <xref:System.ServiceModel.Web.WebServiceHost>, is used to instantiate the data service at a specific address.</span></span>  
  
 <span data-ttu-id="fc55d-131">自己ホストを使用するとサービスの配置とトラブルシューティングが容易になるので、開発時やテスト時に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-131">Self-hosting can be used for development and testing because it can make it easier to deploy and troubleshoot the service.</span></span> <span data-ttu-id="fc55d-132">ただし、この種類のホスティングでは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] またはインターネット インフォメーション サービス (IIS) に備わっている高度なホスト機能や管理機能を使用できません。</span><span class="sxs-lookup"><span data-stu-id="fc55d-132">However, this kind of hosting does not provide the advanced hosting and management features provided by [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] or by Internet Information Services (IIS).</span></span> <span data-ttu-id="fc55d-133">詳細については、次を参照してください。[マネージ アプリケーションのホスト](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc55d-133">For more information, see [Hosting in a Managed Application](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
## <a name="defining-a-custom-data-service-host"></a><span data-ttu-id="fc55d-134">カスタム データ サービス ホストの定義</span><span class="sxs-lookup"><span data-stu-id="fc55d-134">Defining a Custom Data Service Host</span></span>  
 <span data-ttu-id="fc55d-135">WCF ホストの実装の制限が厳格すぎる場合、データ サービスのカスタム ホストを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-135">For cases where the WCF host implementation is too restrictive, you can also define a custom host for a data service.</span></span> <span data-ttu-id="fc55d-136"><xref:System.Data.Services.IDataServiceHost> インターフェイスを実装する任意のクラスをデータ サービスのネットワーク ホストとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc55d-136">Any class that implements <xref:System.Data.Services.IDataServiceHost> interface can be used as the network host for a data service.</span></span> <span data-ttu-id="fc55d-137">カスタム ホストは、<xref:System.Data.Services.IDataServiceHost> インターフェイスを実装し、データ サービス ホストの次の基本的な役割を果たすことができるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc55d-137">A custom host must implement the <xref:System.Data.Services.IDataServiceHost> interface and be able to handle the following basic responsibilities of the data service host:</span></span>  
  
-   <span data-ttu-id="fc55d-138">データ サービスにサービス ルート パスを提供する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-138">Provide the data service with the service root path.</span></span>  
  
-   <span data-ttu-id="fc55d-139">適切な <xref:System.Data.Services.IDataServiceHost> メンバーの実装に対する要求ヘッダーおよび応答ヘッダーの情報を処理する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-139">Process request and response headers information to the appropriate <xref:System.Data.Services.IDataServiceHost> member implementation.</span></span>  
  
-   <span data-ttu-id="fc55d-140">データ サービスで発生する例外を処理する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-140">Handle exceptions raised by the data service.</span></span>  
  
-   <span data-ttu-id="fc55d-141">クエリ文字列のパラメーターを検証する。</span><span class="sxs-lookup"><span data-stu-id="fc55d-141">Validate parameters in the query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc55d-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc55d-142">See Also</span></span>  
 [<span data-ttu-id="fc55d-143">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="fc55d-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="fc55d-144">サービスとしてのデータの公開</span><span class="sxs-lookup"><span data-stu-id="fc55d-144">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)  
 [<span data-ttu-id="fc55d-145">データ サービスの構成</span><span class="sxs-lookup"><span data-stu-id="fc55d-145">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
