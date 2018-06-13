---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 7dc1e4120caae7c4a592067f5e77ed4f56e82e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478167"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="5e522-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="5e522-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="5e522-103">有害メッセージは拒否されました。</span><span class="sxs-lookup"><span data-stu-id="5e522-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5e522-104">説明</span><span class="sxs-lookup"><span data-stu-id="5e522-104">Description</span></span>  
 <span data-ttu-id="5e522-105">このトレースは、有害メッセージが検出され、続いて拒否されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="5e522-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="5e522-106">これは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると発生します。</span><span class="sxs-lookup"><span data-stu-id="5e522-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="5e522-107">拒否されたメッセージは、送信者に送り返す配信[配信不能キュー](http://go.microsoft.com/fwlink/?LinkId=99544)です。</span><span class="sxs-lookup"><span data-stu-id="5e522-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="5e522-108">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkId=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="5e522-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="5e522-109">参照してください[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)拒否されたメッセージは MSMQ では意味の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="5e522-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e522-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e522-110">See Also</span></span>  
 [<span data-ttu-id="5e522-111">トレース</span><span class="sxs-lookup"><span data-stu-id="5e522-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5e522-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5e522-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5e522-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="5e522-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="5e522-114">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="5e522-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="5e522-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="5e522-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
