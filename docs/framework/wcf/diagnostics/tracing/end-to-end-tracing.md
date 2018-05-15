---
title: エンドツーエンドのトレース
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: 733ea0724fdbaea9c7d28ed2a94aba25f67ef87c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="357dc-102">エンドツーエンドのトレース</span><span class="sxs-lookup"><span data-stu-id="357dc-102">End-to-End Tracing</span></span>
<span data-ttu-id="357dc-103">エンド ツー エンド (e2e) のトレースでは、開発者は、コード パスが失敗した原因を調査するために、またはキャパシティ プランニングやパフォーマンス分析の詳細なトレースを提供する、Windows Communication Foundation (WCF) インフラストラクチャでのコードの実行ができます。</span><span class="sxs-lookup"><span data-stu-id="357dc-103">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="357dc-104">Windows Communication Foundation (WCF) には、エラーの原因を診断に役立つ 3 つの相関機構が用意されています。 アクティビティ、転送、および伝達します。</span><span class="sxs-lookup"><span data-stu-id="357dc-104">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="357dc-105">参照してください[エンド ツー エンドのトレース シナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)エンド ツー エンドのトレース シナリオと、それぞれのアクティビティとデザインのトレースの一覧についてはします。</span><span class="sxs-lookup"><span data-stu-id="357dc-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="357dc-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="357dc-106">In This Section</span></span>  
 <span data-ttu-id="357dc-107">[アクティビティ](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): Windows Communication Foundation (WCF) のトレース モデルでのアクティビティ トレースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="357dc-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="357dc-108">[転送](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): Windows Communication Foundation (WCF) トレース モデルでの転送をについて説明し、エンドポイント内のアクティビティを関連付けるために転送を使用します。</span><span class="sxs-lookup"><span data-stu-id="357dc-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="357dc-109">[伝達](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): アクティビティの伝達で、Windows Communication Foundation (WCF)、モデルのトレースと伝達を使用してエンドポイント間でアクティビティを関連付けるためにについて説明します。</span><span class="sxs-lookup"><span data-stu-id="357dc-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="357dc-110">トレースの種類の概要</span><span class="sxs-lookup"><span data-stu-id="357dc-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="357dc-111">すべてのアクティビティ トレースの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="357dc-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="357dc-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="357dc-112">See Also</span></span>  
 [<span data-ttu-id="357dc-113">トレースの構成</span><span class="sxs-lookup"><span data-stu-id="357dc-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="357dc-114">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="357dc-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="357dc-115">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="357dc-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="357dc-116">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="357dc-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
