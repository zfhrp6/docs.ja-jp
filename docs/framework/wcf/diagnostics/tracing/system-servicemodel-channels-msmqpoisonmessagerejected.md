---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28924f04dc83387f49c2369c2598c028f9b8d4bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="945cb-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="945cb-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="945cb-103">有害メッセージは拒否されました。</span><span class="sxs-lookup"><span data-stu-id="945cb-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="945cb-104">説明</span><span class="sxs-lookup"><span data-stu-id="945cb-104">Description</span></span>  
 <span data-ttu-id="945cb-105">このトレースは、有害メッセージが検出され、続いて拒否されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="945cb-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="945cb-106">これは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると発生します。</span><span class="sxs-lookup"><span data-stu-id="945cb-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="945cb-107">拒否されたメッセージは、送信者に送り返す配信[配信不能キュー](http://go.microsoft.com/fwlink/?LinkId=99544)です。</span><span class="sxs-lookup"><span data-stu-id="945cb-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="945cb-108">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkId=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="945cb-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="945cb-109">参照してください[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)拒否されたメッセージは MSMQ では意味の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="945cb-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945cb-110">参照</span><span class="sxs-lookup"><span data-stu-id="945cb-110">See Also</span></span>  
 [<span data-ttu-id="945cb-111">トレース</span><span class="sxs-lookup"><span data-stu-id="945cb-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="945cb-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="945cb-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="945cb-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="945cb-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="945cb-114">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="945cb-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="945cb-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="945cb-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
