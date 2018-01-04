---
title: "エンドツーエンドのトレース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a2127c8dda26c376d7d722a24d72d2330174027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="6dc10-102">エンドツーエンドのトレース</span><span class="sxs-lookup"><span data-stu-id="6dc10-102">End-to-End Tracing</span></span>
<span data-ttu-id="6dc10-103">エンド ツー エンド (E2E) のトレースを使用すると、開発者は [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] インフラストラクチャ内のコードの実行状況を追跡し、コード パスが失敗した原因を調査したり、キャパシティ プランニングやパフォーマンス分析に使用できる詳細なトレース情報を出力したりできます。</span><span class="sxs-lookup"><span data-stu-id="6dc10-103">End to End (e2e) Tracing allows developers to follow the execution of code in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="6dc10-104"> には、エラーの原因の診断に役立つアクティビティ、伝達、および転送の 3 つの相関機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="6dc10-104"> provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="6dc10-105">参照してください[エンド ツー エンドのトレース シナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)エンド ツー エンドのトレース シナリオと、それぞれのアクティビティとデザインのトレースの一覧についてはします。</span><span class="sxs-lookup"><span data-stu-id="6dc10-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6dc10-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6dc10-106">In This Section</span></span>  
 <span data-ttu-id="6dc10-107">[アクティビティ](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): でのアクティビティ トレースについて説明します、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]トレース モデル。</span><span class="sxs-lookup"><span data-stu-id="6dc10-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
 <span data-ttu-id="6dc10-108">[転送](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): での転送について説明します、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]モデルでは、トレースとエンドポイント内のアクティビティを関連付けるために転送を使用します。</span><span class="sxs-lookup"><span data-stu-id="6dc10-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="6dc10-109">[伝達](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): でのアクティビティ伝達について説明します、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]モデルのトレースと伝達を使用してエンドポイント間でアクティビティを関連付けるためにします。</span><span class="sxs-lookup"><span data-stu-id="6dc10-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="6dc10-110">トレースの種類の概要</span><span class="sxs-lookup"><span data-stu-id="6dc10-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="6dc10-111">すべてのアクティビティ トレースの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="6dc10-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc10-112">参照</span><span class="sxs-lookup"><span data-stu-id="6dc10-112">See Also</span></span>  
 [<span data-ttu-id="6dc10-113">トレースの構成</span><span class="sxs-lookup"><span data-stu-id="6dc10-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="6dc10-114">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6dc10-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="6dc10-115">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="6dc10-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="6dc10-116">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="6dc10-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
