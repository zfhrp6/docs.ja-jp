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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f767165486ac2dc6ce4ee5b3e0825eceef0c249
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="97108-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="97108-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="97108-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="97108-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="97108-104">説明</span><span class="sxs-lookup"><span data-stu-id="97108-104">Description</span></span>  
 <span data-ttu-id="97108-105">メッセージの処理中にスレッドが切り替わりました。</span><span class="sxs-lookup"><span data-stu-id="97108-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="97108-106">メッセージ処理は、次の理由によって一時停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="97108-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="97108-107">ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。</span><span class="sxs-lookup"><span data-stu-id="97108-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="97108-108">トランザクションが有効で、サービスが別のトランザクションを処理している。</span><span class="sxs-lookup"><span data-stu-id="97108-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="97108-109">同期コンテキストが最新ではない。</span><span class="sxs-lookup"><span data-stu-id="97108-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97108-110">参照</span><span class="sxs-lookup"><span data-stu-id="97108-110">See Also</span></span>  
 [<span data-ttu-id="97108-111">トレース</span><span class="sxs-lookup"><span data-stu-id="97108-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="97108-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="97108-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="97108-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="97108-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
