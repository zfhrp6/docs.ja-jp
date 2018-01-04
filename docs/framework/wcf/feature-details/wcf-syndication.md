---
title: "WCF 配信"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f7f5fd65fc298107a66e2049c059f3cc58b3d44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-syndication"></a><span data-ttu-id="8cb85-102">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="8cb85-102">WCF Syndication</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="8cb85-103"> には、Atom、RSS、またはその他の独自の形式の配信フィードを簡単に扱うためのサポートが用意されています。これを利用して、配信フィードの読み取りや作成を行ったり、サービス エンドポイントで配信フィードを公開したりできます。</span><span class="sxs-lookup"><span data-stu-id="8cb85-103"> provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="8cb85-104">このセクションのトピックでは、配信用のこのプログラミング モデルについて詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cb85-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8cb85-105">In This Section</span></span>  
 [<span data-ttu-id="8cb85-106">WCF 配信の概要</span><span class="sxs-lookup"><span data-stu-id="8cb85-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="8cb85-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で提供される配信サポートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-107">Provides an overview of syndication support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="8cb85-108">配信のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="8cb85-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="8cb85-109">オブジェクト モデルのクラスと配信の拡張について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="8cb85-110">WCF 配信オブジェクト モデルを Atom や RSS に割り当てる方法</span><span class="sxs-lookup"><span data-stu-id="8cb85-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="8cb85-111">WCF 配信オブジェクト モデルにおけるフィードの表現方法と RSS フィードおよび ATOM フィードへの変換方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="8cb85-112">方法 : 基本的な RSS フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="8cb85-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="8cb85-113">基本的な RSS フィードを利用できるようにするサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="8cb85-114">方法 : 基本的な ATOM フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="8cb85-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="8cb85-115">基本的な ATOM フィードを利用できるようにするサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="8cb85-116">方法 : Atom および RSS の両方としてフィードを公開する</span><span class="sxs-lookup"><span data-stu-id="8cb85-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="8cb85-117">ATOM と RSS で同じフィードを利用できるようにするサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="8cb85-118">配信の拡張</span><span class="sxs-lookup"><span data-stu-id="8cb85-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="8cb85-119">カスタム要素と属性を配信フィードに追加するメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8cb85-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8cb85-120">参照</span><span class="sxs-lookup"><span data-stu-id="8cb85-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8cb85-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cb85-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb85-122">参照</span><span class="sxs-lookup"><span data-stu-id="8cb85-122">See Also</span></span>  
 [<span data-ttu-id="8cb85-123">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="8cb85-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="8cb85-124">部分信頼</span><span class="sxs-lookup"><span data-stu-id="8cb85-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
