---
title: "ガイドラインと最適な使用方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, guidelines
- best practices [WCF], application design
- Windows Communication Foundation, best practices
- WCF, best practices
- Windows Communication Foundation, guidelines
ms.assetid: 5098ba46-6e8d-4e02-b0c5-d737f9fdad84
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 978cb7dcfd132ea253fcb5f13174e14c7341f11a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-and-best-practices"></a><span data-ttu-id="920db-102">ガイドラインと最適な使用方法</span><span class="sxs-lookup"><span data-stu-id="920db-102">Guidelines and Best Practices</span></span>
<span data-ttu-id="920db-103">このセクションには、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションを作成する際のガイドラインとなるトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="920db-103">This section contains topics that provide guidelines for creating [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="920db-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="920db-104">In This Section</span></span>  
 [<span data-ttu-id="920db-105">ベスト プラクティス: データ コントラクトのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="920db-105">Best Practices: Data Contract Versioning</span></span>](../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 <span data-ttu-id="920db-106">将来のバージョンが作成されても影響を受けることのないデータ コントラクトを作成する方法と、そのタイミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="920db-106">Explains how and when to create data contracts that do not break when future versions are created.</span></span>  
  
 [<span data-ttu-id="920db-107">サービスのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="920db-107">Service Versioning</span></span>](../../../docs/framework/wcf/service-versioning.md)  
 <span data-ttu-id="920db-108">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] でのバージョン管理の考え方について説明します。</span><span class="sxs-lookup"><span data-stu-id="920db-108">Explains how to consider versioning in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="920db-109">たとえば、変化するビジネス要件や IT 要件を満たしたり、問題を修復したりするために、展開後にサービス (およびサービスによって公開されるエンドポイント) を変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="920db-109">After deployment, services (and the endpoints they expose) might need to be changed, for example, to satisfy changing business requirements or IT requirements, or to fix issues.</span></span> <span data-ttu-id="920db-110">変更が発生するたびに、新しいバージョンのサービスが導入されます。</span><span class="sxs-lookup"><span data-stu-id="920db-110">Each change introduces a new version of the service.</span></span>  
  
 [<span data-ttu-id="920db-111">負荷分散</span><span class="sxs-lookup"><span data-stu-id="920db-111">Load Balancing</span></span>](../../../docs/framework/wcf/load-balancing.md)  
 <span data-ttu-id="920db-112">Web ファームでの負荷分散のガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="920db-112">Lists guidelines for load balancing with a Web farm.</span></span>  
  
 [<span data-ttu-id="920db-113">リソース消費の制御とパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="920db-113">Controlling Resource Consumption and Improving Performance</span></span>](../../../docs/framework/wcf/controlling-resource-consumption-and-improving-performance.md)  
 <span data-ttu-id="920db-114">過度のリソース消費を抑え、セキュリティを向上するために用意されているプロパティについて説明し、その使用方法の詳細情報を示します。</span><span class="sxs-lookup"><span data-stu-id="920db-114">Describes the properties that are designed to help prevent undue resource consumption and improve security and points to more complete information about their use.</span></span>  
  
 [<span data-ttu-id="920db-115">ClickOnce を使用して WCF アプリケーションを展開する</span><span class="sxs-lookup"><span data-stu-id="920db-115">Deploying WCF Applications with ClickOnce</span></span>](../../../docs/framework/wcf/deploying-wcf-applications-with-clickonce.md)  
 <span data-ttu-id="920db-116">ClickOnce 機能を使用する際の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="920db-116">Describes the considerations to be made when using the ClickOnce feature.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="920db-117">参照</span><span class="sxs-lookup"><span data-stu-id="920db-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="920db-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="920db-118">Related Sections</span></span>  
 [<span data-ttu-id="920db-119">概念</span><span class="sxs-lookup"><span data-stu-id="920db-119">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
  
 [<span data-ttu-id="920db-120">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="920db-120">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="920db-121">参照</span><span class="sxs-lookup"><span data-stu-id="920db-121">See Also</span></span>  
 [<span data-ttu-id="920db-122">Windows Communication Foundation とは</span><span class="sxs-lookup"><span data-stu-id="920db-122">What Is Windows Communication Foundation</span></span>](../../../docs/framework/wcf/whats-wcf.md)  
 [<span data-ttu-id="920db-123">Windows Communication Foundation サンプル</span><span class="sxs-lookup"><span data-stu-id="920db-123">Windows Communication Foundation Samples</span></span>](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
 [<span data-ttu-id="920db-124">概念</span><span class="sxs-lookup"><span data-stu-id="920db-124">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="920db-125">クライアントを構築する</span><span class="sxs-lookup"><span data-stu-id="920db-125">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)
