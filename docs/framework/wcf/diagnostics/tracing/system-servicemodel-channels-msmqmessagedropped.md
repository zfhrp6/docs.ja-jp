---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2f905c345db89e909920334a7dbb524095bc46b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="4b297-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="4b297-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="4b297-103">MSMQ はメッセージを破棄しました。</span><span class="sxs-lookup"><span data-stu-id="4b297-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b297-104">説明</span><span class="sxs-lookup"><span data-stu-id="4b297-104">Description</span></span>  
 <span data-ttu-id="4b297-105">このトレースは、MSMQ メッセージが破棄されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="4b297-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="4b297-106">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] を NetMsmqBinding または MsmqIntegrationBinding と共に使用したときに、MSMQ メッセージを処理できない場合は、これらのメッセージが破棄されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4b297-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="4b297-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4b297-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="4b297-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。</span><span class="sxs-lookup"><span data-stu-id="4b297-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="4b297-109">破棄されたメッセージはキューから削除され、元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="4b297-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="4b297-110">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="4b297-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b297-111">参照</span><span class="sxs-lookup"><span data-stu-id="4b297-111">See Also</span></span>  
 [<span data-ttu-id="4b297-112">トレース</span><span class="sxs-lookup"><span data-stu-id="4b297-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4b297-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4b297-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4b297-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="4b297-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="4b297-115">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="4b297-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
