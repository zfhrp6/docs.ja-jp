---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 2bd64263a2374c10a3514cbed75f9224542051dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478947"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="fb25c-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="fb25c-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="fb25c-103">MSMQ はメッセージを拒否しました。</span><span class="sxs-lookup"><span data-stu-id="fb25c-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fb25c-104">説明</span><span class="sxs-lookup"><span data-stu-id="fb25c-104">Description</span></span>  
 <span data-ttu-id="fb25c-105">このトレースは、MSMQ メッセージが拒否されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="fb25c-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="fb25c-106">Windows Communication Foundation (WCF) が (NetMsmqBinding または MsmqIntegrationBinding と共に使用) は、それらを処理することがない場合に、MSMQ メッセージを拒否できます。</span><span class="sxs-lookup"><span data-stu-id="fb25c-106">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="fb25c-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="fb25c-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="fb25c-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。</span><span class="sxs-lookup"><span data-stu-id="fb25c-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="fb25c-109">拒否されたメッセージは、送信者に送り返す配信[配信不能キュー](http://go.microsoft.com/fwlink/?LinkID=99544)です。</span><span class="sxs-lookup"><span data-stu-id="fb25c-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="fb25c-110">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="fb25c-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="fb25c-111">参照してください[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)拒否されたメッセージは MSMQ では意味の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="fb25c-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb25c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb25c-112">See Also</span></span>  
 [<span data-ttu-id="fb25c-113">トレース</span><span class="sxs-lookup"><span data-stu-id="fb25c-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fb25c-114">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fb25c-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fb25c-115">管理と診断</span><span class="sxs-lookup"><span data-stu-id="fb25c-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="fb25c-116">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="fb25c-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="fb25c-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="fb25c-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
