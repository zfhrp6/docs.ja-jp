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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="1c816-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="1c816-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="1c816-103">MSMQ はメッセージを破棄しました。</span><span class="sxs-lookup"><span data-stu-id="1c816-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1c816-104">説明</span><span class="sxs-lookup"><span data-stu-id="1c816-104">Description</span></span>  
 <span data-ttu-id="1c816-105">このトレースは、MSMQ メッセージが破棄されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="1c816-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="1c816-106">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] を NetMsmqBinding または MsmqIntegrationBinding と共に使用したときに、MSMQ メッセージを処理できない場合は、これらのメッセージが破棄されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1c816-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="1c816-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1c816-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="1c816-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。</span><span class="sxs-lookup"><span data-stu-id="1c816-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="1c816-109">破棄されたメッセージはキューから削除され、元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="1c816-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="1c816-110">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="1c816-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c816-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c816-111">See Also</span></span>  
 [<span data-ttu-id="1c816-112">トレース</span><span class="sxs-lookup"><span data-stu-id="1c816-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1c816-113">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1c816-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1c816-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="1c816-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="1c816-115">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="1c816-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
