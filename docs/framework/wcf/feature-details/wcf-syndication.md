---
title: WCF 配信
ms.date: 03/30/2017
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
ms.openlocfilehash: 627de6431c641e48367a97e3f80f3d05d185ab45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-syndication"></a><span data-ttu-id="9a791-102">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="9a791-102">WCF Syndication</span></span>
<span data-ttu-id="9a791-103">Windows Communication Foundation (WCF) では、Atom、RSS、またはその他のカスタム形式で配信フィードを簡単に操作をサポートすると、読み取り、作成し、サービス エンドポイントで公開することができますを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a791-103">Windows Communication Foundation (WCF) provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="9a791-104">このセクションのトピックでは、配信用のこのプログラミング モデルについて詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a791-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9a791-105">In This Section</span></span>  
 [<span data-ttu-id="9a791-106">WCF 配信の概要</span><span class="sxs-lookup"><span data-stu-id="9a791-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="9a791-107">WCF によって提供される配信サポートの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="9a791-107">Provides an overview of syndication support provided by WCF.</span></span>  
  
 [<span data-ttu-id="9a791-108">配信のアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="9a791-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="9a791-109">オブジェクト モデルのクラスと配信の拡張について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="9a791-110">WCF 配信オブジェクト モデルを Atom や RSS に割り当てる方法</span><span class="sxs-lookup"><span data-stu-id="9a791-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="9a791-111">WCF 配信オブジェクト モデルにおけるフィードの表現方法と RSS フィードおよび ATOM フィードへの変換方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="9a791-112">方法 : 基本的な RSS フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="9a791-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="9a791-113">基本的な RSS フィードを利用できるようにするサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="9a791-114">方法 : 基本的な ATOM フィードを作成する</span><span class="sxs-lookup"><span data-stu-id="9a791-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="9a791-115">基本的な ATOM フィードを利用できるようにするサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="9a791-116">方法 : Atom および RSS の両方としてフィードを公開する</span><span class="sxs-lookup"><span data-stu-id="9a791-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="9a791-117">ATOM と RSS で同じフィードを利用できるようにするサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="9a791-118">配信の拡張</span><span class="sxs-lookup"><span data-stu-id="9a791-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="9a791-119">カスタム要素と属性を配信フィードに追加するメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9a791-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9a791-120">参照</span><span class="sxs-lookup"><span data-stu-id="9a791-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a791-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a791-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a791-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a791-122">See Also</span></span>  
 [<span data-ttu-id="9a791-123">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="9a791-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="9a791-124">部分信頼</span><span class="sxs-lookup"><span data-stu-id="9a791-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
