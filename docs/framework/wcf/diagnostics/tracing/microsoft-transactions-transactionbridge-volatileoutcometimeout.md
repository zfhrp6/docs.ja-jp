---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1992a209bb58c0a0d6f181eb2f1ec546d50372ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="ad91e-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="ad91e-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="ad91e-103">不安定な参加要素からの結果メッセージに対する応答を受信するのを待機しているときに WS-AT プロトコル サービスがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ad91e-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="ad91e-104">受信者が応答した場合、トランザクションの結果が不明である場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad91e-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ad91e-105">説明</span><span class="sxs-lookup"><span data-stu-id="ad91e-105">Description</span></span>  
 <span data-ttu-id="ad91e-106">不安定な参加要素がコミットまたは中止を決定したが、一定時間内にコミット要求またはロールバック要求に応答していない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="ad91e-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ad91e-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ad91e-107">Troubleshooting</span></span>  
 <span data-ttu-id="ad91e-108">不安定な参加要素がすべて一定時間内に応答できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ad91e-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="ad91e-109">既定の時間は 180 秒です。</span><span class="sxs-lookup"><span data-stu-id="ad91e-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="ad91e-110">この時間が不十分な場合は、WS-AT の `VolatileOutcomeDelay` タイマー ポリシーを増やします。</span><span class="sxs-lookup"><span data-stu-id="ad91e-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad91e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad91e-111">See Also</span></span>  
 [<span data-ttu-id="ad91e-112">トレース</span><span class="sxs-lookup"><span data-stu-id="ad91e-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ad91e-113">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ad91e-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ad91e-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="ad91e-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
