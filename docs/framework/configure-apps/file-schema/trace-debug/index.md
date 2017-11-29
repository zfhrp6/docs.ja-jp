---
title: "トレースおよびデバッグ設定のスキーマ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 97c96fbb1abf969d902159709ca0e738f475fab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="4ef93-102">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="4ef93-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="4ef93-103">トレースおよびデバッグの設定により、メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="4ef93-104">次の表に、トレース設定とデバッグ設定の各要素の機能を示します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="4ef93-105">要素</span><span class="sxs-lookup"><span data-stu-id="4ef93-105">Element</span></span>|<span data-ttu-id="4ef93-106">説明</span><span class="sxs-lookup"><span data-stu-id="4ef93-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ef93-107">\<add></span><span class="sxs-lookup"><span data-stu-id="4ef93-107">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="4ef93-108">トレース ソースの `Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="4ef93-109">\<add></span><span class="sxs-lookup"><span data-stu-id="4ef93-109">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="4ef93-110">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-110">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="4ef93-111">\<add></span><span class="sxs-lookup"><span data-stu-id="4ef93-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|<span data-ttu-id="4ef93-112">`sharedListeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-112">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="4ef93-113">\<add></span><span class="sxs-lookup"><span data-stu-id="4ef93-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="4ef93-114">トレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-114">Specifies the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="4ef93-115">\<assert></span><span class="sxs-lookup"><span data-stu-id="4ef93-115">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="4ef93-116"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-116">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="4ef93-117">\<clear></span><span class="sxs-lookup"><span data-stu-id="4ef93-117">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="4ef93-118">トレース ソースの `Listeners` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-118">Clears the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="4ef93-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="4ef93-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="4ef93-120">トレースの `Listeners` コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="4ef93-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="4ef93-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="4ef93-122">トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-122">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="4ef93-123">\<filter></span><span class="sxs-lookup"><span data-stu-id="4ef93-123">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="4ef93-124">トレースの `Listeners` コレクションのリスナーにフィルターに追加します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-124">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="4ef93-125">\<filter></span><span class="sxs-lookup"><span data-stu-id="4ef93-125">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="4ef93-126">`sharedListeners` コレクションのリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-126">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="4ef93-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="4ef93-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="4ef93-128">トレース ソースの `Listeners` コレクションにリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-128">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="4ef93-129">\<listeners></span><span class="sxs-lookup"><span data-stu-id="4ef93-129">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="4ef93-130">トレースの `Listeners` コレクションにリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-130">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="4ef93-131">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="4ef93-131">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="4ef93-132">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-132">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="4ef93-133">\<remove></span><span class="sxs-lookup"><span data-stu-id="4ef93-133">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="4ef93-134">トレースの `Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-134">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="4ef93-135">\<remove></span><span class="sxs-lookup"><span data-stu-id="4ef93-135">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="4ef93-136">トレース ソースの `Listeners` コレクションからリスナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-136">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="4ef93-137">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="4ef93-137">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="4ef93-138">任意の source 要素または trace 要素が参照できるリスナーを含みます。</span><span class="sxs-lookup"><span data-stu-id="4ef93-138">Contains listeners that any source or trace element can reference.</span></span>|  
|[<span data-ttu-id="4ef93-139">\<sources></span><span class="sxs-lookup"><span data-stu-id="4ef93-139">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="4ef93-140">トレース メッセージを開始するトレース ソースを保持します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-140">Contains trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="4ef93-141">\<source></span><span class="sxs-lookup"><span data-stu-id="4ef93-141">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="4ef93-142">トレース メッセージを開始するトレース ソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-142">Specifies a trace source that initiates tracing messages.</span></span>|  
|[<span data-ttu-id="4ef93-143">\<switches></span><span class="sxs-lookup"><span data-stu-id="4ef93-143">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="4ef93-144">トレース スイッチと、トレース スイッチを設定するレベルを保持します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-144">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[<span data-ttu-id="4ef93-145">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="4ef93-145">\<system.diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|<span data-ttu-id="4ef93-146">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-146">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="4ef93-147">\<trace></span><span class="sxs-lookup"><span data-stu-id="4ef93-147">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="4ef93-148">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="4ef93-148">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ef93-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ef93-149">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="4ef93-150">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="4ef93-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
