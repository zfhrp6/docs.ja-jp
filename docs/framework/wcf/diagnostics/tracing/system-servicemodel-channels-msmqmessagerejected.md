---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b433e5e3c0a961098f82ad601d127290b1d6bd73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="3120c-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="3120c-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="3120c-103">MSMQ はメッセージを拒否しました。</span><span class="sxs-lookup"><span data-stu-id="3120c-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3120c-104">説明</span><span class="sxs-lookup"><span data-stu-id="3120c-104">Description</span></span>  
 <span data-ttu-id="3120c-105">このトレースは、MSMQ メッセージが拒否されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="3120c-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="3120c-106">MSMQ メッセージは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] が (NetMsmqBinding または MsmqIntegrationBinding のいずれかを使用して) メッセージを処理できない場合に拒否されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3120c-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="3120c-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="3120c-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="3120c-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。</span><span class="sxs-lookup"><span data-stu-id="3120c-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="3120c-109">拒否されたメッセージは、送信者に送り返す配信[配信不能キュー](http://go.microsoft.com/fwlink/?LinkID=99544)です。</span><span class="sxs-lookup"><span data-stu-id="3120c-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="3120c-110">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="3120c-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="3120c-111">参照してください[MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)拒否されたメッセージは MSMQ では意味の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="3120c-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3120c-112">参照</span><span class="sxs-lookup"><span data-stu-id="3120c-112">See Also</span></span>  
 [<span data-ttu-id="3120c-113">トレース</span><span class="sxs-lookup"><span data-stu-id="3120c-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3120c-114">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3120c-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3120c-115">管理と診断</span><span class="sxs-lookup"><span data-stu-id="3120c-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="3120c-116">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="3120c-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="3120c-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="3120c-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
