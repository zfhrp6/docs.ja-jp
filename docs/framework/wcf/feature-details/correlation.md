---
title: "相関関係"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc1608cc4e746af56e7d89237f0c1f5e6cc3bc7e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="correlation"></a><span data-ttu-id="880bc-102">相関関係</span><span class="sxs-lookup"><span data-stu-id="880bc-102">Correlation</span></span>
<span data-ttu-id="880bc-103">ワークフロー サービス アプリケーションが他のサービスと通信するときには、やり取りされるメッセージが、適切なワークフロー インスタンスにディスパッチされることが重要です。</span><span class="sxs-lookup"><span data-stu-id="880bc-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="880bc-104">相関関係によって、これを実現する機構が提供されます。</span><span class="sxs-lookup"><span data-stu-id="880bc-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="880bc-105">このセクションの各トピックでは、相関関係の概要を示し、さまざまなワークフロー サービス シナリオで相関関係を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="880bc-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="880bc-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="880bc-106">In This Section</span></span>  
 [<span data-ttu-id="880bc-107">相関関係の概要</span><span class="sxs-lookup"><span data-stu-id="880bc-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="880bc-108">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] で使用可能な相関関係の種類の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="880bc-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="880bc-109">コンテキスト交換</span><span class="sxs-lookup"><span data-stu-id="880bc-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="880bc-110">コンテキスト交換の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="880bc-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="880bc-111">永続的な二重</span><span class="sxs-lookup"><span data-stu-id="880bc-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="880bc-112">永続的な二重の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="880bc-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="880bc-113">コンテンツ ベース</span><span class="sxs-lookup"><span data-stu-id="880bc-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="880bc-114">コンテンツ ベースの相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="880bc-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="880bc-115">要求/応答</span><span class="sxs-lookup"><span data-stu-id="880bc-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="880bc-116">要求/応答の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="880bc-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="880bc-117">相関関係のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="880bc-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="880bc-118">相関関係のトラブルシューティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="880bc-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880bc-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="880bc-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="880bc-120">コンテンツ ベースの相関関係</span><span class="sxs-lookup"><span data-stu-id="880bc-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="880bc-121">相関電卓</span><span class="sxs-lookup"><span data-stu-id="880bc-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
