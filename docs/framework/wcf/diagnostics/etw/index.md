---
title: "ETW を使用した分析トレース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42683acdfe2e63d59a13496b210f83fb97c02de7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="87023-102">ETW を使用した分析トレース</span><span class="sxs-lookup"><span data-stu-id="87023-102">Analytic Tracing with ETW</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="87023-103"> の分析トレースでは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの実行中に診断情報をキャプチャする手段が提供されます。</span><span class="sxs-lookup"><span data-stu-id="87023-103"> analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="87023-104"> スタック内のキー ポイントで [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレース イベントが生成され、運用環境での [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスのトラブルシューティングが可能になります。</span><span class="sxs-lookup"><span data-stu-id="87023-104"> analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="87023-105">分析トレースは[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サービスには影響を最小限製品のサーバーのパフォーマンスにホストする[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services のようにこれらのイベントはイベント トレース for Windows (ETW) セッションに非常に効率よく生成されます。</span><span class="sxs-lookup"><span data-stu-id="87023-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87023-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="87023-106">In This Section</span></span>  
 [<span data-ttu-id="87023-107">分析トレースの概要</span><span class="sxs-lookup"><span data-stu-id="87023-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="87023-108">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の分析トレースが [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] でどのように機能するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="87023-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="87023-109">分析トレースを動的に有効にします。</span><span class="sxs-lookup"><span data-stu-id="87023-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="87023-110">ETW を使用してトレースを動的に有効化または無効化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="87023-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="87023-111">メッセージ フローのトレースを構成します。</span><span class="sxs-lookup"><span data-stu-id="87023-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="87023-112">メッセージ フローのトレースを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="87023-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="87023-113">分析トレース イベント リファレンス</span><span class="sxs-lookup"><span data-stu-id="87023-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="87023-114">イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。</span><span class="sxs-lookup"><span data-stu-id="87023-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87023-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="87023-115">See Also</span></span>  
 [<span data-ttu-id="87023-116">WCF サービスと Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="87023-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="87023-117">Windows のイベント トレースへの追跡イベント</span><span class="sxs-lookup"><span data-stu-id="87023-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
