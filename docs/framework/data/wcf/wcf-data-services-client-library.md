---
title: "WCF Data Services クライアント ライブラリ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65b02945aa81fdf18ad328a833f8f85744035871
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="1240a-102">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="1240a-102">WCF Data Services Client Library</span></span>
<span data-ttu-id="1240a-103">HTTP 要求を送信し、データ サービスが返す [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードを処理できるのであれば、どのようなアプリケーションでも [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのデータ サービスと対話できます。</span><span class="sxs-lookup"><span data-stu-id="1240a-103">Any application can interact with an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-based data service if it can send an HTTP request and process the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that a data service returns.</span></span> <span data-ttu-id="1240a-104">この相互運用性によって、広範な Web 対応アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスにアクセスすることが可能になります。</span><span class="sxs-lookup"><span data-stu-id="1240a-104">This interoperability enables you to access [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based services from a broad range of Web-enabled applications.</span></span> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="1240a-105">使用する際に、豊富なプログラミングの経験を提供するクライアント ライブラリを含む[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].NET Framework や Silverlight ベースのアプリケーションからのフィードです。</span><span class="sxs-lookup"><span data-stu-id="1240a-105"> includes client libraries that provide a richer programming experience when you consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="1240a-106">クライアント ライブラリの 2 つの主要なクラスは、<xref:System.Data.Services.Client.DataServiceContext> クラスと <xref:System.Data.Services.Client.DataServiceQuery%601> クラスです。</span><span class="sxs-lookup"><span data-stu-id="1240a-106">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="1240a-107"><xref:System.Data.Services.Client.DataServiceContext> クラスは、特定のデータ サービスに対してサポートされている操作をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="1240a-107">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="1240a-108">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] サービスはステートレスですが、コンテキストはステートレスではありません。</span><span class="sxs-lookup"><span data-stu-id="1240a-108">Although [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] services are stateless, the context is not.</span></span> <span data-ttu-id="1240a-109">したがって、使用することができます、<xref:System.Data.Services.Client.DataServiceContext>変更管理などの機能をサポートするために、データ サービスとのやり取りの間でクライアントの状態を維持するクラス。</span><span class="sxs-lookup"><span data-stu-id="1240a-109">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="1240a-110">このクラスは、ID の管理と変更の追跡も行います。</span><span class="sxs-lookup"><span data-stu-id="1240a-110">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="1240a-111"><xref:System.Data.Services.Client.DataServiceQuery%601> クラスは、特定のエンティティ セットに対するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="1240a-111">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="1240a-112">このセクションでは、クライアント ライブラリを使用して .NET Framework クライアント アプリケーションからデータにアクセスしてデータを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-112">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="1240a-113">使用する方法についての詳細、 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Silverlight ベースのアプリケーションでは、クライアント ライブラリを参照してください[WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016)です。</span><span class="sxs-lookup"><span data-stu-id="1240a-113">For more information about how to use the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016).</span></span> <span data-ttu-id="1240a-114">その他のクライアント ライブラリが用意されて使用できるようにする、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]他の種類のアプリケーションでフィードします。</span><span class="sxs-lookup"><span data-stu-id="1240a-114">Other client libraries are available that enable you to consume an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in other kinds of applications.</span></span> <span data-ttu-id="1240a-115">詳細については、次を参照してください。、 [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)です。</span><span class="sxs-lookup"><span data-stu-id="1240a-115">For more information, see the [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1240a-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1240a-116">In This Section</span></span>  
 [<span data-ttu-id="1240a-117">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="1240a-117">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="1240a-118">クライアント ライブラリおよびに基づくクライアント データ サービス クラスを生成する方法について説明します[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。</span><span class="sxs-lookup"><span data-stu-id="1240a-118">Describes how to generate a client library and client data service classes that are based on [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="1240a-119">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="1240a-119">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="1240a-120">クライアント ライブラリを使用して .NET Framework ベースのアプリケーションからデータ サービスを照会する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-120">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="1240a-121">遅延コンテンツの読み込み</span><span class="sxs-lookup"><span data-stu-id="1240a-121">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="1240a-122">最初のクエリ応答に含まれない追加のコンテンツを読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-122">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="1240a-123">データ サービスの更新</span><span class="sxs-lookup"><span data-stu-id="1240a-123">Updating the Data Service</span></span>](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="1240a-124">クライアント ライブラリを使用してエンティティおよびリレーションシップを作成、変更、および削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-124">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="1240a-125">非同期操作</span><span class="sxs-lookup"><span data-stu-id="1240a-125">Asynchronous Operations</span></span>](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="1240a-126">非同期でデータ サービスを操作するためにクライアント ライブラリで提供される機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-126">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="1240a-127">操作のバッチ処理</span><span class="sxs-lookup"><span data-stu-id="1240a-127">Batching Operations</span></span>](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 <span data-ttu-id="1240a-128">クライアント ライブラリを使用して複数の要求を 1 つのバッチでデータ サービスに送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-128">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="1240a-129">コントロールへのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="1240a-129">Binding Data to Controls</span></span>](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="1240a-130">コントロールにバインドする方法について説明します、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]データ サービスによって返されるフィード。</span><span class="sxs-lookup"><span data-stu-id="1240a-130">Describes how to bind controls to a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="1240a-131">サービス操作の呼び出し</span><span class="sxs-lookup"><span data-stu-id="1240a-131">Calling Service Operations</span></span>](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="1240a-132">クライアント ライブラリを使用してサービス操作を呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-132">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="1240a-133">データ サービス コンテキストを管理します。</span><span class="sxs-lookup"><span data-stu-id="1240a-133">Managing the Data Service Context</span></span>](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="1240a-134">クライアント ライブラリの動作を管理するオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-134">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="1240a-135">バイナリ データの操作</span><span class="sxs-lookup"><span data-stu-id="1240a-135">Working with Binary Data</span></span>](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="1240a-136">データ サービスによってデータ ストリームとして返されるバイナリ データにアクセスしてバイナリ データを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1240a-136">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1240a-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="1240a-137">See Also</span></span>  
 [<span data-ttu-id="1240a-138">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="1240a-138">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="1240a-139">はじめに</span><span class="sxs-lookup"><span data-stu-id="1240a-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
