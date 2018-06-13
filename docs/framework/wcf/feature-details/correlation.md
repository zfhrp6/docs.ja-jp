---
title: 相関関係
ms.date: 03/30/2017
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
ms.openlocfilehash: 9dbebf6d497a5cc109400d04206d39ad76321ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491284"
---
# <a name="correlation"></a><span data-ttu-id="d5ccd-102">相関関係</span><span class="sxs-lookup"><span data-stu-id="d5ccd-102">Correlation</span></span>
<span data-ttu-id="d5ccd-103">ワークフロー サービス アプリケーションが他のサービスと通信するときには、やり取りされるメッセージが、適切なワークフロー インスタンスにディスパッチされることが重要です。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="d5ccd-104">相関関係によって、これを実現する機構が提供されます。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="d5ccd-105">このセクションの各トピックでは、相関関係の概要を示し、さまざまなワークフロー サービス シナリオで相関関係を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5ccd-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d5ccd-106">In This Section</span></span>  
 [<span data-ttu-id="d5ccd-107">相関関係の概要</span><span class="sxs-lookup"><span data-stu-id="d5ccd-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="d5ccd-108">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] で使用可能な相関関係の種類の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="d5ccd-109">コンテキスト交換</span><span class="sxs-lookup"><span data-stu-id="d5ccd-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="d5ccd-110">コンテキスト交換の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="d5ccd-111">永続的な二重</span><span class="sxs-lookup"><span data-stu-id="d5ccd-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="d5ccd-112">永続的な二重の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="d5ccd-113">コンテンツ ベース</span><span class="sxs-lookup"><span data-stu-id="d5ccd-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="d5ccd-114">コンテンツ ベースの相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="d5ccd-115">要求/応答</span><span class="sxs-lookup"><span data-stu-id="d5ccd-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="d5ccd-116">要求/応答の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="d5ccd-117">相関関係のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d5ccd-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="d5ccd-118">相関関係のトラブルシューティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d5ccd-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ccd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5ccd-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="d5ccd-120">コンテンツ ベースの相関関係</span><span class="sxs-lookup"><span data-stu-id="d5ccd-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="d5ccd-121">相関電卓</span><span class="sxs-lookup"><span data-stu-id="d5ccd-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
