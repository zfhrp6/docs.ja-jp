---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: e30b0dd8e18dcba4a4c15aab6cf5f321492eb1a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33476926"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="86c3d-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="86c3d-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>
<span data-ttu-id="86c3d-103">名前付きパイプ エンドポイントに接続しようとして失敗しました。</span><span class="sxs-lookup"><span data-stu-id="86c3d-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="86c3d-104">指定されたタイムアウト期間内に再試行します。</span><span class="sxs-lookup"><span data-stu-id="86c3d-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="86c3d-105">説明</span><span class="sxs-lookup"><span data-stu-id="86c3d-105">Description</span></span>  
 <span data-ttu-id="86c3d-106">この情報トレースは、名前付きパイプ エンドポイントへの接続に失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="86c3d-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="86c3d-107">これは、名前付きパイプ エンドポイントが見つからなかったか、ビジーであった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="86c3d-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="86c3d-108">接続に成功するか、OpenTimeout の有効期間が切れるまで、短い間隔を置いて再試行が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="86c3d-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c3d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="86c3d-109">See Also</span></span>  
 [<span data-ttu-id="86c3d-110">トレース</span><span class="sxs-lookup"><span data-stu-id="86c3d-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="86c3d-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="86c3d-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="86c3d-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="86c3d-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
