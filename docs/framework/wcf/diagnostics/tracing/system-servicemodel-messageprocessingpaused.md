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
ms.openlocfilehash: 33d05eaa94ec0efdf6d18d03d9d38bda6f0c9eb7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="d134b-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="d134b-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="d134b-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="d134b-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="d134b-104">説明</span><span class="sxs-lookup"><span data-stu-id="d134b-104">Description</span></span>  
 <span data-ttu-id="d134b-105">メッセージの処理中にスレッドが切り替わりました。</span><span class="sxs-lookup"><span data-stu-id="d134b-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="d134b-106">メッセージ処理は、次の理由によって一時停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="d134b-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="d134b-107">ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。</span><span class="sxs-lookup"><span data-stu-id="d134b-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="d134b-108">トランザクションが有効で、サービスが別のトランザクションを処理している。</span><span class="sxs-lookup"><span data-stu-id="d134b-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="d134b-109">同期コンテキストが最新ではない。</span><span class="sxs-lookup"><span data-stu-id="d134b-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d134b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d134b-110">See Also</span></span>  
 [<span data-ttu-id="d134b-111">トレース</span><span class="sxs-lookup"><span data-stu-id="d134b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d134b-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d134b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d134b-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="d134b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
