---
title: WCF Data Services 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b6b9ddd27422c09f21833548634afd7945afa89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="a1cee-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="a1cee-102">WCF Data Services 4.5</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a1cee-103"> (従来の "ADO.NET Data Services") は .NET Framework のコンポーネントです。このコンポーネントを使用すると、[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) のセマンティクスを使用し、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を使用して Web またはイントラネット上のデータを公開および使用するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-103"> (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="a1cee-104"> は、URI でアドレス指定できるリソースとしてデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-104"> exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="a1cee-105">標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="a1cee-106"> は、[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) のエンティティとリレーションシップの規則を使用して、アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-106"> uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a1cee-107"> は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルを使用してリソースのアドレス指定および更新を行います。</span><span class="sxs-lookup"><span data-stu-id="a1cee-107"> uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="a1cee-108">このようにして、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] をサポートしている任意のクライアントからこれらのサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="a1cee-109"> を使用すると、XML としてデータを交換および更新するための標準のセットである Atom と、AJAX アプリケーションで広範に使用されるテキスト ベースのデータ交換形式である JavaScript Object Notation (JSON) という広く知られている転送形式を使用して、データをリソースに要求または書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-109"> enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a1cee-110"> では、さまざまなソースからのデータを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-110"> can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="a1cee-111">Visual Studio のツールを使用すると、ADO.NET Entity Framework データ モデルを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="a1cee-112">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードは、共通言語ランタイム (CLR) クラスに基づいて作成できます。また、遅延バインディング データまたは型指定されていないデータに基づいて作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a1cee-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a1cee-113"> には、クライアント ライブラリのセット (一般的な .NET Framework クライアント アプリケーション用と Silverlight ベースのアプリケーション用) も含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1cee-113"> also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="a1cee-114">これらのクライアント ライブラリは、.NET Framework や Silverlight などの環境から [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスするときにオブジェクト ベースのプログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="a1cee-115">開始すべき場所</span><span class="sxs-lookup"><span data-stu-id="a1cee-115">Where Should I Start?</span></span>  
 <span data-ttu-id="a1cee-116">各自の興味に応じて、次のトピックのいずれかから [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の使用を開始することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a1cee-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="a1cee-117">すぐに使用を開始したい</span><span class="sxs-lookup"><span data-stu-id="a1cee-117">I want to jump right in…</span></span>  
 -   [<span data-ttu-id="a1cee-118">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="a1cee-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="a1cee-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-120">Silverlight クイックスタート</span><span class="sxs-lookup"><span data-stu-id="a1cee-120">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="a1cee-121">Windows Phone 開発用の Silverlight クイック スタート</span><span class="sxs-lookup"><span data-stu-id="a1cee-121">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 <span data-ttu-id="a1cee-122">コードを見たい</span><span class="sxs-lookup"><span data-stu-id="a1cee-122">Just show me some code…</span></span>  
 -   [<span data-ttu-id="a1cee-123">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="a1cee-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-124">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="a1cee-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-125">方法: Windows Presentation Foundation 要素にデータをバインドする</span><span class="sxs-lookup"><span data-stu-id="a1cee-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 <span data-ttu-id="a1cee-126">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] について詳しく知りたい</span><span class="sxs-lookup"><span data-stu-id="a1cee-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   [<span data-ttu-id="a1cee-127">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="a1cee-127">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="a1cee-128">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="a1cee-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="a1cee-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="a1cee-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [<span data-ttu-id="a1cee-130">OData: よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="a1cee-130">OData: Frequently Asked Questions</span></span>](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 <span data-ttu-id="a1cee-131">ビデオを見たい</span><span class="sxs-lookup"><span data-stu-id="a1cee-131">I want to watch some videos…</span></span>  
 -   [<span data-ttu-id="a1cee-132">WCF Data Services のビギナーズ ガイド</span><span class="sxs-lookup"><span data-stu-id="a1cee-132">Beginner's Guide to WCF Data Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [<span data-ttu-id="a1cee-133">WCF Data Services 開発者用ビデオ</span><span class="sxs-lookup"><span data-stu-id="a1cee-133">WCF Data Services Developer Videos</span></span>](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [<span data-ttu-id="a1cee-134">OData: 開発者 Web サイト</span><span class="sxs-lookup"><span data-stu-id="a1cee-134">OData: Developers Web site</span></span>](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 <span data-ttu-id="a1cee-135">エンド ツー エンドのサンプルを見たい</span><span class="sxs-lookup"><span data-stu-id="a1cee-135">I want to see end-to-end samples</span></span>  
 -   [<span data-ttu-id="a1cee-136">MSDN サンプル ギャラリーの WCF Data Services ドキュメントのサンプル</span><span class="sxs-lookup"><span data-stu-id="a1cee-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [<span data-ttu-id="a1cee-137">MSDN サンプル ギャラリーのその他の WCF Data Services サンプル</span><span class="sxs-lookup"><span data-stu-id="a1cee-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [<span data-ttu-id="a1cee-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="a1cee-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="a1cee-139">Visual Studio との統合について知りたい</span><span class="sxs-lookup"><span data-stu-id="a1cee-139">How does it integrate with Visual Studio?</span></span>  
 -   [<span data-ttu-id="a1cee-140">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="a1cee-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-141">データ サービスの作成</span><span class="sxs-lookup"><span data-stu-id="a1cee-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [<span data-ttu-id="a1cee-142">Entity Framework プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a1cee-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 <span data-ttu-id="a1cee-143">何に使用できるかを知りたい</span><span class="sxs-lookup"><span data-stu-id="a1cee-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="a1cee-144">概要</span><span class="sxs-lookup"><span data-stu-id="a1cee-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [<span data-ttu-id="a1cee-145">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="a1cee-145">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="a1cee-146">アプリケーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="a1cee-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 <span data-ttu-id="a1cee-147">Silverlight を使用したい</span><span class="sxs-lookup"><span data-stu-id="a1cee-147">I want to use Silverlight…</span></span>  
 -   [<span data-ttu-id="a1cee-148">Silverlight クイックスタート</span><span class="sxs-lookup"><span data-stu-id="a1cee-148">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="a1cee-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="a1cee-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [<span data-ttu-id="a1cee-150">Silverlight について</span><span class="sxs-lookup"><span data-stu-id="a1cee-150">Getting Started with Silverlight</span></span>](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 <span data-ttu-id="a1cee-151">Windows Phone アプリケーションを作成したい</span><span class="sxs-lookup"><span data-stu-id="a1cee-151">I want to create a Windows Phone application…</span></span>  
 -   [<span data-ttu-id="a1cee-152">Windows Phone 開発用の Silverlight クイック スタート</span><span class="sxs-lookup"><span data-stu-id="a1cee-152">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [<span data-ttu-id="a1cee-153">Windows Phone の Open Data Protocol (OData) クライアント</span><span class="sxs-lookup"><span data-stu-id="a1cee-153">Open Data Protocol (OData) Client for Windows Phone</span></span>](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 <span data-ttu-id="a1cee-154">LINQ を使用したい</span><span class="sxs-lookup"><span data-stu-id="a1cee-154">I want to use LINQ…</span></span>  
 -   [<span data-ttu-id="a1cee-155">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="a1cee-155">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-156">LINQ に関する留意点</span><span class="sxs-lookup"><span data-stu-id="a1cee-156">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [<span data-ttu-id="a1cee-157">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="a1cee-157">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 <span data-ttu-id="a1cee-158">より詳しい情報が欲しい</span><span class="sxs-lookup"><span data-stu-id="a1cee-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="a1cee-159">WCF Data Services チームのブログ</span><span class="sxs-lookup"><span data-stu-id="a1cee-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="a1cee-160">リソース</span><span class="sxs-lookup"><span data-stu-id="a1cee-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [<span data-ttu-id="a1cee-161">WCF Data Services デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="a1cee-161">WCF Data Services Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [<span data-ttu-id="a1cee-162">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="a1cee-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="a1cee-163">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a1cee-163">In This Section</span></span>  
 [<span data-ttu-id="a1cee-164">概要</span><span class="sxs-lookup"><span data-stu-id="a1cee-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="a1cee-165">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用可能な機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="a1cee-166">WCF Data Services の新機能</span><span class="sxs-lookup"><span data-stu-id="a1cee-166">What's New in WCF Data Services</span></span>](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 <span data-ttu-id="a1cee-167">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の新機能と、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="a1cee-168">はじめに</span><span class="sxs-lookup"><span data-stu-id="a1cee-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="a1cee-169">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="a1cee-170">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="a1cee-170">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 <span data-ttu-id="a1cee-171">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開するデータ サービスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="a1cee-172">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="a1cee-172">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 <span data-ttu-id="a1cee-173">クライアント ライブラリを使用して .NET Framework クライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1cee-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1cee-174">参照</span><span class="sxs-lookup"><span data-stu-id="a1cee-174">See Also</span></span>  
 [<span data-ttu-id="a1cee-175">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="a1cee-175">Representational State Transfer (REST)</span></span>](http://go.microsoft.com/fwlink/?LinkId=113919)
