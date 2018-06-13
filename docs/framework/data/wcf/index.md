---
title: WCF Data Services 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 148e6e50e81552b2418abba9f6655234fc023c4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365957"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="3bcae-102">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="3bcae-102">WCF Data Services 4.5</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="3bcae-103"> (従来の "ADO.NET Data Services") は .NET Framework のコンポーネントです。このコンポーネントを使用すると、[Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919) のセマンティクスを使用し、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] を使用して Web またはイントラネット上のデータを公開および使用するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-103"> (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919).</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="3bcae-104"> は、URI でアドレス指定できるリソースとしてデータを公開します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-104"> exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="3bcae-105">標準的な HTTP 動詞である GET、PUT、POST、および DELETE を使用してデータにアクセスし、変更できます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-105">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="3bcae-106"> は、[Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) のエンティティとリレーションシップの規則を使用して、アソシエーションによって関連付けられたエンティティのセットとしてリソースを公開します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-106"> uses the entity-relationship conventions of the [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="3bcae-107"> は、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルを使用してリソースのアドレス指定および更新を行います。</span><span class="sxs-lookup"><span data-stu-id="3bcae-107"> uses the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol for addressing and updating resources.</span></span> <span data-ttu-id="3bcae-108">このようにして、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] をサポートしている任意のクライアントからこれらのサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-108">In this way, you can access these services from any client that supports [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]<span data-ttu-id="3bcae-109"> を使用すると、XML としてデータを交換および更新するための標準のセットである Atom と、AJAX アプリケーションで広範に使用されるテキスト ベースのデータ交換形式である JavaScript Object Notation (JSON) という広く知られている転送形式を使用して、データをリソースに要求または書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-109"> enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX application.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="3bcae-110"> では、さまざまなソースからのデータを [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-110"> can expose data that originates from various sources as [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span> <span data-ttu-id="3bcae-111">Visual Studio のツールを使用すると、ADO.NET Entity Framework データ モデルを使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ベースのサービスを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-111">Visual Studio tools make it easier for you to create an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="3bcae-112">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードは、共通言語ランタイム (CLR) クラスに基づいて作成できます。また、遅延バインディング データまたは型指定されていないデータに基づいて作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="3bcae-112">You can also create [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="3bcae-113"> には、クライアント ライブラリのセット (一般的な .NET Framework クライアント アプリケーション用と Silverlight ベースのアプリケーション用) も含まれています。</span><span class="sxs-lookup"><span data-stu-id="3bcae-113"> also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="3bcae-114">これらのクライアント ライブラリは、.NET Framework や Silverlight などの環境から [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードにアクセスするときにオブジェクト ベースのプログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-114">These client libraries provide an object-based programming model when you access an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed from environments such as the .NET Framework and Silverlight.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="3bcae-115">開始すべき場所</span><span class="sxs-lookup"><span data-stu-id="3bcae-115">Where Should I Start?</span></span>  
 <span data-ttu-id="3bcae-116">各自の興味に応じて、次のトピックのいずれかから [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の使用を開始することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3bcae-116">Depending on your interests, consider getting started with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] in one of the following topics.</span></span>  
  
 <span data-ttu-id="3bcae-117">すぐに使用を開始したい</span><span class="sxs-lookup"><span data-stu-id="3bcae-117">I want to jump right in…</span></span>  
 -   [<span data-ttu-id="3bcae-118">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="3bcae-118">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-119">はじめに</span><span class="sxs-lookup"><span data-stu-id="3bcae-119">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-120">Silverlight クイックスタート</span><span class="sxs-lookup"><span data-stu-id="3bcae-120">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="3bcae-121">Windows Phone 開発用の Silverlight クイック スタート</span><span class="sxs-lookup"><span data-stu-id="3bcae-121">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 <span data-ttu-id="3bcae-122">コードを見たい</span><span class="sxs-lookup"><span data-stu-id="3bcae-122">Just show me some code…</span></span>  
 -   [<span data-ttu-id="3bcae-123">クイック スタート</span><span class="sxs-lookup"><span data-stu-id="3bcae-123">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-124">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="3bcae-124">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-125">方法: Windows Presentation Foundation 要素にデータをバインドする</span><span class="sxs-lookup"><span data-stu-id="3bcae-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 <span data-ttu-id="3bcae-126">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] について詳しく知りたい</span><span class="sxs-lookup"><span data-stu-id="3bcae-126">I want to know more about [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]…</span></span>  
 -   [<span data-ttu-id="3bcae-127">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="3bcae-127">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="3bcae-128">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="3bcae-128">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [<span data-ttu-id="3bcae-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="3bcae-129">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [<span data-ttu-id="3bcae-130">OData: よく寄せられる質問</span><span class="sxs-lookup"><span data-stu-id="3bcae-130">OData: Frequently Asked Questions</span></span>](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 <span data-ttu-id="3bcae-131">ビデオを見たい</span><span class="sxs-lookup"><span data-stu-id="3bcae-131">I want to watch some videos…</span></span>  
 -   [<span data-ttu-id="3bcae-132">WCF Data Services のビギナーズ ガイド</span><span class="sxs-lookup"><span data-stu-id="3bcae-132">Beginner's Guide to WCF Data Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [<span data-ttu-id="3bcae-133">WCF Data Services 開発者用ビデオ</span><span class="sxs-lookup"><span data-stu-id="3bcae-133">WCF Data Services Developer Videos</span></span>](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [<span data-ttu-id="3bcae-134">OData: 開発者 Web サイト</span><span class="sxs-lookup"><span data-stu-id="3bcae-134">OData: Developers Web site</span></span>](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 <span data-ttu-id="3bcae-135">エンド ツー エンドのサンプルを見たい</span><span class="sxs-lookup"><span data-stu-id="3bcae-135">I want to see end-to-end samples</span></span>  
 -   [<span data-ttu-id="3bcae-136">MSDN サンプル ギャラリーの WCF Data Services ドキュメントのサンプル</span><span class="sxs-lookup"><span data-stu-id="3bcae-136">WCF Data Services Documentation Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [<span data-ttu-id="3bcae-137">MSDN サンプル ギャラリーのその他の WCF Data Services サンプル</span><span class="sxs-lookup"><span data-stu-id="3bcae-137">Other WCF Data Services Samples on MSDN Samples Gallery</span></span>](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [<span data-ttu-id="3bcae-138">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="3bcae-138">OData: SDK</span></span>](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 <span data-ttu-id="3bcae-139">Visual Studio との統合について知りたい</span><span class="sxs-lookup"><span data-stu-id="3bcae-139">How does it integrate with Visual Studio?</span></span>  
 -   [<span data-ttu-id="3bcae-140">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="3bcae-140">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-141">データ サービスの作成</span><span class="sxs-lookup"><span data-stu-id="3bcae-141">Creating the Data Service</span></span>](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [<span data-ttu-id="3bcae-142">Entity Framework プロバイダー</span><span class="sxs-lookup"><span data-stu-id="3bcae-142">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 <span data-ttu-id="3bcae-143">何に使用できるかを知りたい</span><span class="sxs-lookup"><span data-stu-id="3bcae-143">What can I do with it?</span></span>  
 -   [<span data-ttu-id="3bcae-144">概要</span><span class="sxs-lookup"><span data-stu-id="3bcae-144">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [<span data-ttu-id="3bcae-145">ホワイト ペーパー: OData の概要</span><span class="sxs-lookup"><span data-stu-id="3bcae-145">Whitepaper: Introducing OData</span></span>](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [<span data-ttu-id="3bcae-146">アプリケーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="3bcae-146">Application Scenarios</span></span>](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 <span data-ttu-id="3bcae-147">Silverlight を使用したい</span><span class="sxs-lookup"><span data-stu-id="3bcae-147">I want to use Silverlight…</span></span>  
 -   [<span data-ttu-id="3bcae-148">Silverlight クイックスタート</span><span class="sxs-lookup"><span data-stu-id="3bcae-148">Silverlight Quickstart</span></span>](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [<span data-ttu-id="3bcae-149">WCF Data Services (Silverlight)</span><span class="sxs-lookup"><span data-stu-id="3bcae-149">WCF Data Services (Silverlight)</span></span>](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [<span data-ttu-id="3bcae-150">Silverlight について</span><span class="sxs-lookup"><span data-stu-id="3bcae-150">Getting Started with Silverlight</span></span>](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 <span data-ttu-id="3bcae-151">Windows Phone アプリケーションを作成したい</span><span class="sxs-lookup"><span data-stu-id="3bcae-151">I want to create a Windows Phone application…</span></span>  
 -   [<span data-ttu-id="3bcae-152">Windows Phone 開発用の Silverlight クイック スタート</span><span class="sxs-lookup"><span data-stu-id="3bcae-152">Silverlight Quickstart for Windows Phone Development</span></span>](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [<span data-ttu-id="3bcae-153">Windows Phone の Open Data Protocol (OData) クライアント</span><span class="sxs-lookup"><span data-stu-id="3bcae-153">Open Data Protocol (OData) Client for Windows Phone</span></span>](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 <span data-ttu-id="3bcae-154">LINQ を使用したい</span><span class="sxs-lookup"><span data-stu-id="3bcae-154">I want to use LINQ…</span></span>  
 -   [<span data-ttu-id="3bcae-155">データ サービスに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="3bcae-155">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-156">LINQ に関する留意点</span><span class="sxs-lookup"><span data-stu-id="3bcae-156">LINQ Considerations</span></span>](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [<span data-ttu-id="3bcae-157">方法: データ サービス クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="3bcae-157">How to: Execute Data Service Queries</span></span>](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 <span data-ttu-id="3bcae-158">より詳しい情報が欲しい</span><span class="sxs-lookup"><span data-stu-id="3bcae-158">I still need some more information…</span></span>  
 -   [<span data-ttu-id="3bcae-159">WCF Data Services チームのブログ</span><span class="sxs-lookup"><span data-stu-id="3bcae-159">WCF Data Services Team Blog</span></span>](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [<span data-ttu-id="3bcae-160">リソース</span><span class="sxs-lookup"><span data-stu-id="3bcae-160">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [<span data-ttu-id="3bcae-161">WCF Data Services デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3bcae-161">WCF Data Services Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [<span data-ttu-id="3bcae-162">Open Data Protocol Web サイト</span><span class="sxs-lookup"><span data-stu-id="3bcae-162">Open Data Protocol Web site</span></span>](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a><span data-ttu-id="3bcae-163">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3bcae-163">In This Section</span></span>  
 [<span data-ttu-id="3bcae-164">概要</span><span class="sxs-lookup"><span data-stu-id="3bcae-164">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 <span data-ttu-id="3bcae-165">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用可能な機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-165">Provides an overview of the features and functionality available in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="3bcae-166">WCF Data Services の新機能</span><span class="sxs-lookup"><span data-stu-id="3bcae-166">What's New in WCF Data Services</span></span>](http://msdn.microsoft.com/library/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 <span data-ttu-id="3bcae-167">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] の新機能と、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の新機能のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-167">Describes new functionality in [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] and support for new [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] features.</span></span>  
  
 [<span data-ttu-id="3bcae-168">はじめに</span><span class="sxs-lookup"><span data-stu-id="3bcae-168">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 <span data-ttu-id="3bcae-169">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用して [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-169">Describes how to expose and consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds by using [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="3bcae-170">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="3bcae-170">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 <span data-ttu-id="3bcae-171">[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを公開するデータ サービスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-171">Describes how to create and configure a data service that exposes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="3bcae-172">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="3bcae-172">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 <span data-ttu-id="3bcae-173">クライアント ライブラリを使用して .NET Framework クライアント アプリケーションから [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] フィードを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bcae-173">Describes how to use client libraries to consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from a .NET Framework client application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcae-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bcae-174">See Also</span></span>  
 [<span data-ttu-id="3bcae-175">Representational State Transfer (REST)</span><span class="sxs-lookup"><span data-stu-id="3bcae-175">Representational State Transfer (REST)</span></span>](http://go.microsoft.com/fwlink/?LinkId=113919)
