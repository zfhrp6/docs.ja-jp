---
title: "カスタム データ サービス プロバイダー (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7db780b97c1a7eadffbfa71f60be4afe590ccb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a><span data-ttu-id="08317-102">カスタム データ サービス プロバイダー (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="08317-102">Custom Data Service Providers (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="08317-103"> には、遅延バインディング データ型に基づいてデータ モデルを定義できるプロバイダーのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08317-103"> includes a set of providers that enables you to define a data model based on late-bound data types.</span></span>  
  
|<span data-ttu-id="08317-104">プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-104">Provider</span></span>|<span data-ttu-id="08317-105">説明</span><span class="sxs-lookup"><span data-stu-id="08317-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="08317-106">メタデータ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-106">Metadata provider</span></span>|<span data-ttu-id="08317-107">これは、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを実装することによって実行時にカスタム データ モデルを定義できるコア カスタム データ サービス プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="08317-107">This is the core custom data service provider that enables you to define a custom data model at runtime by implementing the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span>|  
|<span data-ttu-id="08317-108">クエリ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-108">Query provider</span></span>|<span data-ttu-id="08317-109">このプロバイダーを使用すると、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを使用して定義されたカスタム データ モデルに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="08317-109">This provider enables you to execute queries against a custom data model that is defined by using the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span> <span data-ttu-id="08317-110">クエリ プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceQueryProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="08317-110">The query provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.</span></span>|  
|<span data-ttu-id="08317-111">更新プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-111">Update provider</span></span>|<span data-ttu-id="08317-112">このプロバイダーを使用すると、カスタム データ サービス プロバイダー内で公開されている型を更新して同時実行を管理できます。</span><span class="sxs-lookup"><span data-stu-id="08317-112">This provider enables you to make updates to types that are exposed in a custom data service provider and to manage concurrency.</span></span> <span data-ttu-id="08317-113">更新プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceUpdateProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="08317-113">An update provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface</span></span>|  
|<span data-ttu-id="08317-114">ページング プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-114">Paging provider</span></span>|<span data-ttu-id="08317-115">このプロバイダーは、サーバー ドリブン ページング サポートを有効にするためにカスタム データ サービス プロバイダーと一緒に使用します。</span><span class="sxs-lookup"><span data-stu-id="08317-115">This provider is used with the custom data service provider to enable server-driven paging support.</span></span> <span data-ttu-id="08317-116">カスタム データ サービスのページング プロバイダーは、<xref:System.Data.Services.Providers.IDataServicePagingProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="08317-116">A paging provider for a custom data service is created by implementing the <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.</span></span>|  
|<span data-ttu-id="08317-117">ストリーミング プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-117">Streaming provider</span></span>|<span data-ttu-id="08317-118">このプロバイダーを使用すると、ストリームとしてバイナリ ラージ オブジェクト データ型を公開できます。</span><span class="sxs-lookup"><span data-stu-id="08317-118">This provider enables you to expose binary large object data types as a stream.</span></span> <span data-ttu-id="08317-119">ストリーミング プロバイダーは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="08317-119">A streaming provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interface.</span></span> <span data-ttu-id="08317-120">ストリーミング プロバイダーは、Entity Framework プロバイダーおよびリフレクション データ ソース プロバイダーと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="08317-120">The streaming provider can also be used with Entity Framework and reflection data source providers.</span></span> <span data-ttu-id="08317-121">詳細については、次を参照してください。[ストリーミング プロバイダー](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="08317-121">For more information, see [Streaming Provider](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).</span></span>|  
  
 <span data-ttu-id="08317-122">詳細については、記事を参照してください。[カスタム データ サービス プロバイダー](http://go.microsoft.com/fwlink/?LinkID=186850)と[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]プロバイダー ツールキット、 [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069)です。</span><span class="sxs-lookup"><span data-stu-id="08317-122">For more information, see the article [Custom Data Service Providers](http://go.microsoft.com/fwlink/?LinkID=186850) and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Provider Toolkit in the [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08317-123">参照</span><span class="sxs-lookup"><span data-stu-id="08317-123">See Also</span></span>  
 [<span data-ttu-id="08317-124">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-124">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="08317-125">Entity Framework プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-125">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [<span data-ttu-id="08317-126">リフレクション プロバイダー</span><span class="sxs-lookup"><span data-stu-id="08317-126">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
