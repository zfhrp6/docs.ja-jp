---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: ad05a2b8552cc09d45e950e2c3336d86be918963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479132"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="e3793-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="e3793-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="e3793-103">MSMQ はメッセージを破棄しました。</span><span class="sxs-lookup"><span data-stu-id="e3793-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3793-104">説明</span><span class="sxs-lookup"><span data-stu-id="e3793-104">Description</span></span>  
 <span data-ttu-id="e3793-105">このトレースは、MSMQ メッセージが破棄されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="e3793-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="e3793-106">Windows Communication Foundation (WCF) が (NetMsmqBinding または MsmqIntegrationBinding と共に使用) は、それらを処理することがない場合に、MSMQ メッセージを削除できます。</span><span class="sxs-lookup"><span data-stu-id="e3793-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="e3793-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e3793-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="e3793-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。</span><span class="sxs-lookup"><span data-stu-id="e3793-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="e3793-109">破棄されたメッセージはキューから削除され、元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e3793-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="e3793-110">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="e3793-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3793-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3793-111">See Also</span></span>  
 [<span data-ttu-id="e3793-112">トレース</span><span class="sxs-lookup"><span data-stu-id="e3793-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e3793-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e3793-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e3793-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e3793-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="e3793-115">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="e3793-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
