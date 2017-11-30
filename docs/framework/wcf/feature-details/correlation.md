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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d15609db250e4743ae2a7a1b6c3c355600704f02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="correlation"></a><span data-ttu-id="57356-102">相関関係</span><span class="sxs-lookup"><span data-stu-id="57356-102">Correlation</span></span>
<span data-ttu-id="57356-103">ワークフロー サービス アプリケーションが他のサービスと通信するときには、やり取りされるメッセージが、適切なワークフロー インスタンスにディスパッチされることが重要です。</span><span class="sxs-lookup"><span data-stu-id="57356-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="57356-104">相関関係によって、これを実現する機構が提供されます。</span><span class="sxs-lookup"><span data-stu-id="57356-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="57356-105">このセクションの各トピックでは、相関関係の概要を示し、さまざまなワークフロー サービス シナリオで相関関係を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57356-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57356-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="57356-106">In This Section</span></span>  
 [<span data-ttu-id="57356-107">相関関係の概要</span><span class="sxs-lookup"><span data-stu-id="57356-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="57356-108">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] で使用可能な相関関係の種類の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="57356-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="57356-109">コンテキスト交換</span><span class="sxs-lookup"><span data-stu-id="57356-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="57356-110">コンテキスト交換の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="57356-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="57356-111">永続的な二重</span><span class="sxs-lookup"><span data-stu-id="57356-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="57356-112">永続的な二重の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="57356-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="57356-113">コンテンツ ベース</span><span class="sxs-lookup"><span data-stu-id="57356-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="57356-114">コンテンツ ベースの相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="57356-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="57356-115">要求/応答</span><span class="sxs-lookup"><span data-stu-id="57356-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="57356-116">要求/応答の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="57356-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="57356-117">相関関係のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="57356-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="57356-118">相関関係のトラブルシューティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="57356-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57356-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="57356-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="57356-120">コンテンツ ベースの相関関係</span><span class="sxs-lookup"><span data-stu-id="57356-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="57356-121">相関電卓</span><span class="sxs-lookup"><span data-stu-id="57356-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
