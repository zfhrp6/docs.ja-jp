---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 474895e7fbcf1b9ed7ad7da6d28313ae4894f720
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="dc10f-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="dc10f-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="dc10f-103">メッセージを移動または削除できません。</span><span class="sxs-lookup"><span data-stu-id="dc10f-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dc10f-104">説明</span><span class="sxs-lookup"><span data-stu-id="dc10f-104">Description</span></span>  
 <span data-ttu-id="dc10f-105">このトレースは、MSMQ メッセージの移動、削除、または拒否の試行中にエラーが発生したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="dc10f-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="dc10f-106">MSMQ メッセージは (NetMsmqBinding または MsmqIntegrationBinding のどちらかを使用する場合に) [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] で使用されます。このトレースは NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティで選択された値と関係しています。</span><span class="sxs-lookup"><span data-stu-id="dc10f-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="dc10f-107">このトレースはシステム全体についてのエラーを示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="dc10f-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="dc10f-108">ただし、選択した有害メッセージの処置に失敗したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="dc10f-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="dc10f-109">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="dc10f-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc10f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc10f-110">See Also</span></span>  
 [<span data-ttu-id="dc10f-111">トレース</span><span class="sxs-lookup"><span data-stu-id="dc10f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="dc10f-112">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="dc10f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="dc10f-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="dc10f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
