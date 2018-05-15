---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: a6b4e369d2d22d2441b3896321b7c152e21d967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="79ab9-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="79ab9-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="79ab9-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="79ab9-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="79ab9-104">説明</span><span class="sxs-lookup"><span data-stu-id="79ab9-104">Description</span></span>  
 <span data-ttu-id="79ab9-105">システムは ManualFlowControlLimit スロットルに設定された制限値に達しました。</span><span class="sxs-lookup"><span data-stu-id="79ab9-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="79ab9-106">スロットル値を変更するには、ServiceHost または InstanceContext の ManualFlowControlLimit プロパティを適宜変更します。</span><span class="sxs-lookup"><span data-stu-id="79ab9-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="79ab9-107">このトレースは、マニュアル フロー制御制限が初めて 0 に減少したときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="79ab9-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="79ab9-108">それ以降は、0 に変更されてもトレースされません。</span><span class="sxs-lookup"><span data-stu-id="79ab9-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="79ab9-109">インスタンス コンテキストに対するフロー制御制限は、コンテキストごとに 1 回トレースされます。</span><span class="sxs-lookup"><span data-stu-id="79ab9-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ab9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="79ab9-110">See Also</span></span>  
 [<span data-ttu-id="79ab9-111">トレース</span><span class="sxs-lookup"><span data-stu-id="79ab9-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="79ab9-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="79ab9-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="79ab9-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="79ab9-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
