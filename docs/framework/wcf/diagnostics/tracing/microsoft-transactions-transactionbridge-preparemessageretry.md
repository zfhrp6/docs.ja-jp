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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d3483165fe7a4895c6540f2c8023c09d6c00d2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="27a08-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="27a08-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="27a08-103">応答しない参加要素に、準備メッセージの再試行が送信されました。</span><span class="sxs-lookup"><span data-stu-id="27a08-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="27a08-104">説明</span><span class="sxs-lookup"><span data-stu-id="27a08-104">Description</span></span>  
 <span data-ttu-id="27a08-105">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、下位の参加要素に準備メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="27a08-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="27a08-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="27a08-106">Troubleshooting</span></span>  
 <span data-ttu-id="27a08-107">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="27a08-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="27a08-108">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="27a08-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="27a08-109">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="27a08-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a08-110">参照</span><span class="sxs-lookup"><span data-stu-id="27a08-110">See Also</span></span>  
 [<span data-ttu-id="27a08-111">トレース</span><span class="sxs-lookup"><span data-stu-id="27a08-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="27a08-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="27a08-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="27a08-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="27a08-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
