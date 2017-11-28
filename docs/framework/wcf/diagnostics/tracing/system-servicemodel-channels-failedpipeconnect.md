---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a64f5885fd32d2486c90ebe4f8e0c739a025d0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="cf858-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="cf858-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="cf858-103">名前付きパイプ エンドポイントに接続しようとして失敗しました。</span><span class="sxs-lookup"><span data-stu-id="cf858-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="cf858-104">指定されたタイムアウト期間内に再試行します。</span><span class="sxs-lookup"><span data-stu-id="cf858-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cf858-105">説明</span><span class="sxs-lookup"><span data-stu-id="cf858-105">Description</span></span>  
 <span data-ttu-id="cf858-106">この情報トレースは、名前付きパイプ エンドポイントへの接続に失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cf858-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="cf858-107">これは、名前付きパイプ エンドポイントが見つからなかったか、ビジーであった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="cf858-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="cf858-108">接続に成功するか、OpenTimeout の有効期間が切れるまで、短い間隔を置いて再試行が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="cf858-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf858-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf858-109">See Also</span></span>  
 [<span data-ttu-id="cf858-110">トレース</span><span class="sxs-lookup"><span data-stu-id="cf858-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cf858-111">トレースを使用して、アプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="cf858-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cf858-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="cf858-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
