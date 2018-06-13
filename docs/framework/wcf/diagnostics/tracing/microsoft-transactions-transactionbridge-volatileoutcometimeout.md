---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475632"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="b5fdb-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="b5fdb-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="b5fdb-103">不安定な参加要素からの結果メッセージに対する応答を受信するのを待機しているときに WS-AT プロトコル サービスがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b5fdb-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="b5fdb-104">受信者が応答した場合、トランザクションの結果が不明である場合があります。</span><span class="sxs-lookup"><span data-stu-id="b5fdb-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b5fdb-105">説明</span><span class="sxs-lookup"><span data-stu-id="b5fdb-105">Description</span></span>  
 <span data-ttu-id="b5fdb-106">不安定な参加要素がコミットまたは中止を決定したが、一定時間内にコミット要求またはロールバック要求に応答していない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="b5fdb-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b5fdb-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b5fdb-107">Troubleshooting</span></span>  
 <span data-ttu-id="b5fdb-108">不安定な参加要素がすべて一定時間内に応答できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b5fdb-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="b5fdb-109">既定の時間は 180 秒です。</span><span class="sxs-lookup"><span data-stu-id="b5fdb-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="b5fdb-110">この時間が不十分な場合は、WS-AT の `VolatileOutcomeDelay` タイマー ポリシーを増やします。</span><span class="sxs-lookup"><span data-stu-id="b5fdb-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fdb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5fdb-111">See Also</span></span>  
 [<span data-ttu-id="b5fdb-112">トレース</span><span class="sxs-lookup"><span data-stu-id="b5fdb-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b5fdb-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b5fdb-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b5fdb-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="b5fdb-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
