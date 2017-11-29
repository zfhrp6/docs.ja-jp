---
title: "WCF Data Services の定義"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 888f0af14e31c432cd4ad737232a22ed6f079a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="5fb6c-102">WCF Data Services の定義</span><span class="sxs-lookup"><span data-stu-id="5fb6c-102">Defining WCF Data Services</span></span>
<span data-ttu-id="5fb6c-103">このセクションで作成および構成する方法を説明する[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]としてデータを公開する、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードします。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-103">This section describes how to create and configure [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5fb6c-104">データ サービスを作成するために必要な基本的な手順を参照してください[データ サービスとして公開する](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-104"> the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5fb6c-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5fb6c-105">In This Section</span></span>  
 [<span data-ttu-id="5fb6c-106">データ サービスの構成</span><span class="sxs-lookup"><span data-stu-id="5fb6c-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-107">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] によって提供されるデータ サービス構成オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-107">Describes the data service configuration options provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="5fb6c-108">データ サービス プロバイダー</span><span class="sxs-lookup"><span data-stu-id="5fb6c-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-109">データ サービスとしてデータを公開するプロバイダー モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-109">Describes the provider models for exposing data as a data service.</span></span>  
  
 [<span data-ttu-id="5fb6c-110">サービス操作</span><span class="sxs-lookup"><span data-stu-id="5fb6c-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-111">サーバー上でメソッドを公開するサービス操作を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-111">Describes how to define service operations that expose methods on the server.</span></span>  
  
 [<span data-ttu-id="5fb6c-112">フィードのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5fb6c-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-113">データ サービス プロバイダーおよびデータ フィードの要素によって定義されるデータ モデルのエンティティ間のマッピングを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>  
  
 [<span data-ttu-id="5fb6c-114">インターセプター</span><span class="sxs-lookup"><span data-stu-id="5fb6c-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-115">インターセプター メソッドを定義してデータ サービスへの要求に対してカスタム ビジネス ロジックを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>  
  
 [<span data-ttu-id="5fb6c-116">開発および WCF Data Services の配置</span><span class="sxs-lookup"><span data-stu-id="5fb6c-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-117">Visual Studio を使用してデータ サービスを開発および配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>  
  
 [<span data-ttu-id="5fb6c-118">WCF Data Services のセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="5fb6c-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-119">データ サービスの認証と承認およびセキュリティに関するその他の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-119">Describes authentication and authorization for the data service and other security considerations.</span></span>  
  
 [<span data-ttu-id="5fb6c-120">データ サービスのホスティング</span><span class="sxs-lookup"><span data-stu-id="5fb6c-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-121">データ サービスのホストを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-121">Describes how to select a host for your data service.</span></span>  
  
 [<span data-ttu-id="5fb6c-122">データ サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="5fb6c-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)  
 <span data-ttu-id="5fb6c-123">異なるバージョンの [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-123">Describes how to work with different versions of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span>  
  
 [<span data-ttu-id="5fb6c-124">WCF Data Services プロトコル実装の詳細</span><span class="sxs-lookup"><span data-stu-id="5fb6c-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)  
 <span data-ttu-id="5fb6c-125">WCF Data Services で現在実装されていない [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのオプション機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="5fb6c-125">Describes optional functionalities of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol that are not currently implemented by WCF Data Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb6c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fb6c-126">See Also</span></span>  
 [<span data-ttu-id="5fb6c-127">WCF Data Services クライアント ライブラリ</span><span class="sxs-lookup"><span data-stu-id="5fb6c-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="5fb6c-128">データ サービス リソースへのアクセス</span><span class="sxs-lookup"><span data-stu-id="5fb6c-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [<span data-ttu-id="5fb6c-129">はじめに</span><span class="sxs-lookup"><span data-stu-id="5fb6c-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
