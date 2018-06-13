---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487907"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="c4f4e-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="c4f4e-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="c4f4e-103">メッセージを移動または削除できません。</span><span class="sxs-lookup"><span data-stu-id="c4f4e-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c4f4e-104">説明</span><span class="sxs-lookup"><span data-stu-id="c4f4e-104">Description</span></span>  
 <span data-ttu-id="c4f4e-105">このトレースは、MSMQ メッセージの移動、削除、または拒否の試行中にエラーが発生したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c4f4e-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="c4f4e-106">MSMQ メッセージで Windows Communication Foundation (WCF) (併用すると、NetMsmqBinding または MsmqIntegrationBinding のいずれか) を使用します。このトレースは、選択した値に関連する、 `ReceiveErrorHandling` NetMsmqBinding または MsmqIntegrationBinding のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c4f4e-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="c4f4e-107">このトレースはシステム全体についてのエラーを示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="c4f4e-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="c4f4e-108">ただし、選択した有害メッセージの処置に失敗したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c4f4e-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="c4f4e-109">参照してください[有害メッセージの処理](http://go.microsoft.com/fwlink/?LinkID=99546)ときにメッセージが有害となる適切に処理するサービスを構成する方法の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="c4f4e-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f4e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4f4e-110">See Also</span></span>  
 [<span data-ttu-id="c4f4e-111">トレース</span><span class="sxs-lookup"><span data-stu-id="c4f4e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c4f4e-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c4f4e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c4f4e-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="c4f4e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
