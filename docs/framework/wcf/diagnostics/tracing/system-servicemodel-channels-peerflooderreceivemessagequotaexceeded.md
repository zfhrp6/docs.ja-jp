---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 136baabc0760826aa9ba76dc19862c9c4b60e16e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="351d5-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="351d5-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="351d5-103">メッセージの受信速度が速すぎます。</span><span class="sxs-lookup"><span data-stu-id="351d5-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="351d5-104">説明</span><span class="sxs-lookup"><span data-stu-id="351d5-104">Description</span></span>  
 <span data-ttu-id="351d5-105">このトレースは、受信メッセージの処理を試みたときに行われます。</span><span class="sxs-lookup"><span data-stu-id="351d5-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="351d5-106">特定の近隣ノードでクォータ セットが超過しているため、メッセージをその近隣ノードに転送できません。</span><span class="sxs-lookup"><span data-stu-id="351d5-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="351d5-107">応答しない近隣ノードが、メッセージ保留のバックログをクリアできなかった場合にこの状態が発生します。</span><span class="sxs-lookup"><span data-stu-id="351d5-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="351d5-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="351d5-108">Troubleshooting</span></span>  
 <span data-ttu-id="351d5-109">メッシュ内でメッセージが送信される速度を遅くしてください。</span><span class="sxs-lookup"><span data-stu-id="351d5-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="351d5-110">参照</span><span class="sxs-lookup"><span data-stu-id="351d5-110">See Also</span></span>  
 [<span data-ttu-id="351d5-111">トレース</span><span class="sxs-lookup"><span data-stu-id="351d5-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="351d5-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="351d5-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="351d5-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="351d5-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
