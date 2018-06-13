---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 6fb1463b811d985f54b9a99e59d1280eaa040256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482815"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="6c6dc-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="6c6dc-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="6c6dc-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="6c6dc-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="6c6dc-104">説明</span><span class="sxs-lookup"><span data-stu-id="6c6dc-104">Description</span></span>  
 <span data-ttu-id="6c6dc-105">メッセージの処理中にスレッドが切り替わりました。</span><span class="sxs-lookup"><span data-stu-id="6c6dc-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="6c6dc-106">メッセージ処理は、次の理由によって一時停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="6c6dc-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="6c6dc-107">ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。</span><span class="sxs-lookup"><span data-stu-id="6c6dc-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="6c6dc-108">トランザクションが有効で、サービスが別のトランザクションを処理している。</span><span class="sxs-lookup"><span data-stu-id="6c6dc-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="6c6dc-109">同期コンテキストが最新ではない。</span><span class="sxs-lookup"><span data-stu-id="6c6dc-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c6dc-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c6dc-110">See Also</span></span>  
 [<span data-ttu-id="6c6dc-111">トレース</span><span class="sxs-lookup"><span data-stu-id="6c6dc-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="6c6dc-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6c6dc-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="6c6dc-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="6c6dc-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
