---
title: "分析トレースの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3492821d56f7089c2aa53bba566690ded02f8a5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-overview"></a><span data-ttu-id="ba50a-102">分析トレースの概要</span><span class="sxs-lookup"><span data-stu-id="ba50a-102">Analytic Tracing Overview</span></span>
<span data-ttu-id="ba50a-103">[!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] の分析トレースは、Event Tracing for Windows (ETW) を基盤とするトレース機能のセットです。詳細度は低いのですが、パフォーマンスに優れています。</span><span class="sxs-lookup"><span data-stu-id="ba50a-103">Analytic tracing in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] is a high performance and low verbosity tracing feature set on top of Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="ba50a-104">ETW は、カーネル レベルで実行され、トレース操作のオーバーヘッドを大幅に削減します。</span><span class="sxs-lookup"><span data-stu-id="ba50a-104">ETW runs at the kernel-level to greatly reduce the overhead of tracing operations.</span></span> <span data-ttu-id="ba50a-105">ユーザー モードおよびカーネル モードのイベントを効率よくバッファーし、サービスの再起動を必要とすることなく、動的にログを有効化できます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-105">It efficiently buffers user- and kernel-mode events, and allows dynamic enabling of logging without requiring service restarts.</span></span> <span data-ttu-id="ba50a-106">トレース データは、生成および受信されると、イベント ログから確認できます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-106">The tracing data is available in the event logs after it has been emitted and received.</span></span>  
  
 <span data-ttu-id="ba50a-107">ETW の[!INCLUDE[crabout](../../../../../includes/crabout-md.md)] については、「 [ETW によりデバッグおよびパフォーマンス調整を改善する](http://go.microsoft.com/fwlink/?LinkId=164781)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba50a-107">[!INCLUDE[crabout](../../../../../includes/crabout-md.md)] ETW, see [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkId=164781).</span></span>  
  
 <span data-ttu-id="ba50a-108">Windows のシステム、セキュリティ、およびアプリケーション イベント ログによるアプリケーションの分析のほかに、 [!INCLUDE[wv](../../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] では、最上位ノードの [アプリケーションとサービス ログ] の下にログが追加されています。</span><span class="sxs-lookup"><span data-stu-id="ba50a-108">In addition to using the Windows System, Security, and Application event logs to analyze application, [!INCLUDE[wv](../../../../../includes/wv-md.md)] and [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] introduced additional logs under the Applications and Services Logs top-level node.</span></span> <span data-ttu-id="ba50a-109">これらの新しいログは、システム全体に影響するグローバルなイベント (セキュリティ イベント ログで記録されるようなイベントなど) ではなく、特定のアプリケーションやコンポーネントのイベントを格納することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ba50a-109">The purpose of these new logs is to store events for a particular application or specific component instead of global events that have a system-wide impact (such as the type of events that the Security event log might record).</span></span> [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="ba50a-110"> では、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース イベント、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] メッセージ ログ、および [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] 追跡レコードのログを [アプリケーションとサービス ログ] にまとめ、相互に関連付けています。</span><span class="sxs-lookup"><span data-stu-id="ba50a-110"> unifies and correlates the logging of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Trace Events, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Message Logs, and [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] Tracking records to the Applications and Services Logs.</span></span>  
  
## <a name="concepts-and-capabilities"></a><span data-ttu-id="ba50a-111">概念と機能</span><span class="sxs-lookup"><span data-stu-id="ba50a-111">Concepts and Capabilities</span></span>  
 <span data-ttu-id="ba50a-112">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 分析トレースには、次の概念と機能があります。</span><span class="sxs-lookup"><span data-stu-id="ba50a-112">The following concepts and capabilities apply to [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Analytic Tracing.</span></span>  
  
### <a name="enabling-wcf-diagnostics-settings"></a><span data-ttu-id="ba50a-113">WCF 診断設定の有効化</span><span class="sxs-lookup"><span data-stu-id="ba50a-113">Enabling WCF Diagnostics Settings</span></span>  
 <span data-ttu-id="ba50a-114">内で WCF の診断が有効になっている、 \<system.serviceModel >\<診断 > 構成セクション。</span><span class="sxs-lookup"><span data-stu-id="ba50a-114">WCF diagnostics are enabled within the \<system.serviceModel>\<diagnostics> configuration section.</span></span>  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 <span data-ttu-id="ba50a-115">Web でホストされる IIS 仮想アプリケーションの WCF 診断の設定は、アプリケーションの Web.config ファイルで有効にします。</span><span class="sxs-lookup"><span data-stu-id="ba50a-115">WCF diagnostic settings for a Web-hosted IIS virtual application are enabled in its’ Web.config file.</span></span> <span data-ttu-id="ba50a-116">または、アプリケーション内のサブディレクトリに Web.config を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-116">Another option is to create a Web.config in a sub-directory within the application.</span></span>  <span data-ttu-id="ba50a-117">この方法では、設定がサブディレクトリ内のすべてのサービスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-117">This choice applies the settings to all of the services within a sub-directory.</span></span>  <span data-ttu-id="ba50a-118">診断設定が、アプリケーション内のすべてのサービスに対して一貫して初期化されるようにするには、これらの設定を、アプリケーション内の個別のサブディレクトリの 1 つではなく、アプリケーション ディレクトリ内の Web.config に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba50a-118">To ensure that the diagnostics settings are initialized consistently for all services within the application, the settings should be within the Web.config in the application directory and not in one of the individual sub-directories within the application.</span></span>  
  
### <a name="channels"></a><span data-ttu-id="ba50a-119">チャネル</span><span class="sxs-lookup"><span data-stu-id="ba50a-119">Channels</span></span>  
 <span data-ttu-id="ba50a-120">ETW の場合、ソフトウェア コンポーネントは、チャネルを使用することで、トレース イベントをユーザーの種類に応じて振り分けることができます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-120">ETW allows software components to direct tracing events to a particular audience by use of channels.</span></span> <span data-ttu-id="ba50a-121">たとえば、システム管理者向けのイベントを 1 つのチャネルに送信し、アプリケーション開発者にとって重要なイベントを別のチャネルに送信できます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-121">For example, you can send events for system administrators to one channel, and events that application developers care about to another channel.</span></span> <span data-ttu-id="ba50a-122">チャネルには名前が付けられ、Windows に登録されるので、ユーザーは、特定のチャネルのイベントをイベント ビューアーを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-122">Channels are named and registered with Windows so that consumers can view a channel’s events using the Event Viewer.</span></span>  
  
 <span data-ttu-id="ba50a-123">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] の [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] の分析トレース機能は、Microsoft-Windows-Application-Server-Applications チャネルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-123">The analytic tracing feature for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] writes to the Microsoft-Windows-Application-Server-Applications channel.</span></span> <span data-ttu-id="ba50a-124">このチャネルは、特に、運用中の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスの状態を監視する必要があるユーザー向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="ba50a-124">This channel is specifically designed for users who want to monitor the health of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in production.</span></span> <span data-ttu-id="ba50a-125">このチャネルでは、さまざまな状態監視およびトラブルシューティング シナリオで使用できるイベントがいくつか定義されています。</span><span class="sxs-lookup"><span data-stu-id="ba50a-125">It defines a small, set of events that can be used in many health monitoring and troubleshooting scenarios.</span></span>  
  
 <span data-ttu-id="ba50a-126">メッセージがイベント ログで正常にデコードされるように Event Tracing for Windows マニファストを有効にするために、次のようにコマンド ラインで ServiceModelReg ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba50a-126">To enable the Event Tracing for Windows manifest so that messages are decoded properly in the event log, use the ServiceModelReg tool on the command line as follows:</span></span>  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="ba50a-127">動的構成</span><span class="sxs-lookup"><span data-stu-id="ba50a-127">Dynamic Configuration</span></span>  
 <span data-ttu-id="ba50a-128">ETW のインフラストラクチャでは、標準の Windows ツールを使用して動的にトレースを有効化および構成できます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-128">The ETW infrastructure allows tracing to be enabled and configured dynamically using standard Windows tools.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="ba50a-129">[分析トレースを動的に有効にする](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba50a-129"> [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).</span></span>  
  
### <a name="message-flow-tracing"></a><span data-ttu-id="ba50a-130">メッセージ フローのトレース</span><span class="sxs-lookup"><span data-stu-id="ba50a-130">Message Flow Tracing</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="ba50a-131"> については、「 [Configuring Message Flow Tracing](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba50a-131"> how to enable message flow tracing, see [Configuring Message Flow Tracing](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).</span></span>  
  
### <a name="keywords"></a><span data-ttu-id="ba50a-132">キーワード</span><span class="sxs-lookup"><span data-stu-id="ba50a-132">Keywords</span></span>  
 <span data-ttu-id="ba50a-133">キーワードは、トレース メッセージをフィルター処理するため、およびイベントを生成した [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] コンポーネントを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ba50a-133">Keywords are used to filter trace messages and define which component of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitted the event.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="ba50a-134">[分析トレースを動的に有効にする](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba50a-134"> [Dynamically Enabling Analytic Tracing](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).</span></span>
