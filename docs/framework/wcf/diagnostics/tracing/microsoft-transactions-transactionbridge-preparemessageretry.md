---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8199398e4e0bfe8ad42f6c8ba8adb11e883236e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="fd6ca-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="fd6ca-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="fd6ca-103">応答しない参加要素に、準備メッセージの再試行が送信されました。</span><span class="sxs-lookup"><span data-stu-id="fd6ca-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd6ca-104">説明</span><span class="sxs-lookup"><span data-stu-id="fd6ca-104">Description</span></span>  
 <span data-ttu-id="fd6ca-105">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、下位の参加要素に準備メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="fd6ca-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fd6ca-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fd6ca-106">Troubleshooting</span></span>  
 <span data-ttu-id="fd6ca-107">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="fd6ca-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="fd6ca-108">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fd6ca-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="fd6ca-109">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fd6ca-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6ca-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd6ca-110">See Also</span></span>  
 [<span data-ttu-id="fd6ca-111">トレース</span><span class="sxs-lookup"><span data-stu-id="fd6ca-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fd6ca-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fd6ca-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fd6ca-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="fd6ca-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
