---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88ee90abb10e9f5e09deecb3d3d66c54dc289592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="d89eb-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="d89eb-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="d89eb-103">準備メッセージの再試行は、応答しないコーディネーターに送信されました。</span><span class="sxs-lookup"><span data-stu-id="d89eb-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d89eb-104">説明</span><span class="sxs-lookup"><span data-stu-id="d89eb-104">Description</span></span>  
 <span data-ttu-id="d89eb-105">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、上位のコーディネーターに準備メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="d89eb-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d89eb-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d89eb-106">Troubleshooting</span></span>  
 <span data-ttu-id="d89eb-107">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="d89eb-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="d89eb-108">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="d89eb-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="d89eb-109">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="d89eb-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89eb-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d89eb-110">See Also</span></span>  
 [<span data-ttu-id="d89eb-111">トレース</span><span class="sxs-lookup"><span data-stu-id="d89eb-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d89eb-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d89eb-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d89eb-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="d89eb-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
