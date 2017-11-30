---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1176af676673e19eb2d8cd54cc4d2d254c7ba324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="e087c-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="e087c-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="e087c-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="e087c-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="e087c-104">説明</span><span class="sxs-lookup"><span data-stu-id="e087c-104">Description</span></span>  
 <span data-ttu-id="e087c-105">メッセージの処理中にスレッドが切り替わりました。</span><span class="sxs-lookup"><span data-stu-id="e087c-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="e087c-106">メッセージ処理は、次の理由によって一時停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="e087c-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="e087c-107">ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。</span><span class="sxs-lookup"><span data-stu-id="e087c-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="e087c-108">トランザクションが有効で、サービスが別のトランザクションを処理している。</span><span class="sxs-lookup"><span data-stu-id="e087c-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="e087c-109">同期コンテキストが最新ではない。</span><span class="sxs-lookup"><span data-stu-id="e087c-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e087c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e087c-110">See Also</span></span>  
 [<span data-ttu-id="e087c-111">トレース</span><span class="sxs-lookup"><span data-stu-id="e087c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e087c-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e087c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e087c-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e087c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
