---
title: "トレースを使用したアプリケーションのトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7676b9bb-cbd1-41fd-9a93-cc615af6e2d0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddb199ff1d83bef64735dd1425ec955dda83140d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="using-tracing-to-troubleshoot-your-application"></a><span data-ttu-id="fcf13-102">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fcf13-102">Using Tracing to Troubleshoot Your Application</span></span>
<span data-ttu-id="fcf13-103">このセクションには、トレースを使用してアプリケーションをトラブルシューティングする方法について説明したさまざまなトピックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fcf13-103">This section contains various topics that describe how you can use tracing to troubleshoot your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fcf13-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fcf13-104">In This Section</span></span>  
 [<span data-ttu-id="fcf13-105">トレースとメッセージ ログの推奨設定</span><span class="sxs-lookup"><span data-stu-id="fcf13-105">Recommended Settings for Tracing and Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)  
 <span data-ttu-id="fcf13-106">運用環境とデバッグ環境の推奨設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="fcf13-106">Describes suggested settings for production and debugging environments.</span></span>  
  
 [<span data-ttu-id="fcf13-107">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fcf13-107">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 <span data-ttu-id="fcf13-108">ここでは、サービス トレース ビューアー ツールを使用して、トレース データの表示、関連付け、および分析を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fcf13-108">Describes how you can use the Service Trace Viewer tool to view, correlate and analyze trace data.</span></span>  
  
 [<span data-ttu-id="fcf13-109">重要なトレース</span><span class="sxs-lookup"><span data-stu-id="fcf13-109">Significant Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/significant-traces.md)  
 <span data-ttu-id="fcf13-110">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] によって出力される主要なトレースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="fcf13-110">A list of major traces emitted by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="fcf13-111">クライアントでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="fcf13-111">Debugging on the Client</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/debugging-on-the-client.md)  
 <span data-ttu-id="fcf13-112">クライアントでアプリケーションをデバッグできるようにします。</span><span class="sxs-lookup"><span data-stu-id="fcf13-112">Enables clients to debug your application.</span></span>  
  
 [<span data-ttu-id="fcf13-113">エンド ツー エンドのトレース シナリオ</span><span class="sxs-lookup"><span data-stu-id="fcf13-113">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="fcf13-114">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のエンドツーエンドのシナリオ (たとえば、wsHttp による同期要求/応答や TCP による非同期の一方向要求) で使用されるトレースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fcf13-114">Describes traces used for E2E [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] scenarios, for example, synchronous wsHttp request-replies, and asynchronous TCP one-way requests.</span></span>  
  
 [<span data-ttu-id="fcf13-115">ユーザー コード トレースの出力</span><span class="sxs-lookup"><span data-stu-id="fcf13-115">Emitting User-Code Traces</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)  
 <span data-ttu-id="fcf13-116">プログラムを使用してユーザー コードでトレースを出力する方法について説明します。これによってインストルメンテーション データを事前に作成し、後の診断 (および WCF トレースとの関連付け) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcf13-116">Describes how to emit traces programmatically in user code, so that you can proactively create instrumentation data to be used later for diagnostic purpose, and in correlation with WCF traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf13-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcf13-117">See Also</span></span>  
 [<span data-ttu-id="fcf13-118">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="fcf13-118">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="fcf13-119">トレース</span><span class="sxs-lookup"><span data-stu-id="fcf13-119">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fcf13-120">エンド ツー エンドのトレース</span><span class="sxs-lookup"><span data-stu-id="fcf13-120">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
