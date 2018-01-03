---
title: "アプリケーション ドメインのリソース監視 (ARM) ETW イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="7c63a-102">アプリケーション ドメインのリソース監視 (ARM) ETW イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="7c63a-103">これらのイベントは、アプリケーション ドメインの状態に関する詳細な診断の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="7c63a-104">これらのイベントを使用することもできますが、アプリケーション ドメインのリソース監視 (ARM) の機能を使用しても同じ情報を得られます。</span><span class="sxs-lookup"><span data-stu-id="7c63a-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="7c63a-105">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="7c63a-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="7c63a-106">ThreadCreated イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="7c63a-107">AppDomainMemAllocated イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="7c63a-108">AppDomainMemSurvived イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="7c63a-109">ThreadAppDomainEnter イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="7c63a-110">ThreadTerminated イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="7c63a-111">ThreadCreated イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="7c63a-112">このイベントは、ランダウン プロバイダーで `ThreadDC` としても発生します  ( `AppDomainResourceManagementRundownKeyword` キーワードで発生)。</span><span class="sxs-lookup"><span data-stu-id="7c63a-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="7c63a-113">これは、このカテゴリでランダウン プロバイダーで発生する唯一のイベントです。</span><span class="sxs-lookup"><span data-stu-id="7c63a-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="7c63a-114">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="7c63a-115">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="7c63a-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="7c63a-116">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7c63a-116">Keyword for raising the event</span></span>|<span data-ttu-id="7c63a-117">レベル</span><span class="sxs-lookup"><span data-stu-id="7c63a-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7c63a-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="7c63a-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="7c63a-119">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-119">Informational(4)</span></span>|  
|<span data-ttu-id="7c63a-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7c63a-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7c63a-121">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="7c63a-122">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7c63a-123">イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-123">Event</span></span>|<span data-ttu-id="7c63a-124">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7c63a-124">Event ID</span></span>|<span data-ttu-id="7c63a-125">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7c63a-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="7c63a-126">85</span><span class="sxs-lookup"><span data-stu-id="7c63a-126">85</span></span>|<span data-ttu-id="7c63a-127">アプリケーション ドメインに対してスレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="7c63a-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="7c63a-128">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7c63a-129">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7c63a-129">Field name</span></span>|<span data-ttu-id="7c63a-130">データ型</span><span class="sxs-lookup"><span data-stu-id="7c63a-130">Data type</span></span>|<span data-ttu-id="7c63a-131">説明</span><span class="sxs-lookup"><span data-stu-id="7c63a-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7c63a-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="7c63a-132">ThreadID</span></span>|<span data-ttu-id="7c63a-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-133">win:UInt64</span></span>|<span data-ttu-id="7c63a-134">作成されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="7c63a-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7c63a-135">AppDomainID</span></span>|<span data-ttu-id="7c63a-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-136">win:UInt64</span></span>|<span data-ttu-id="7c63a-137">スレッドのアクティビティの報告対象のアプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="7c63a-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="7c63a-138">フラグ</span><span class="sxs-lookup"><span data-stu-id="7c63a-138">Flags</span></span>|<span data-ttu-id="7c63a-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7c63a-139">win:UInt32</span></span>|<span data-ttu-id="7c63a-140">スレッドの作成フラグ</span><span class="sxs-lookup"><span data-stu-id="7c63a-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="7c63a-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="7c63a-141">ManagedThreadIndex</span></span>|<span data-ttu-id="7c63a-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7c63a-142">win:UInt32</span></span>|<span data-ttu-id="7c63a-143">作成されたスレッドのマネージ インデックス。</span><span class="sxs-lookup"><span data-stu-id="7c63a-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="7c63a-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="7c63a-144">OSThreadID</span></span>|<span data-ttu-id="7c63a-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="7c63a-145">win:UInt32</span></span>|<span data-ttu-id="7c63a-146">作成されたスレッドのオペレーティング システム ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="7c63a-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7c63a-147">ClrInstanceID</span></span>|<span data-ttu-id="7c63a-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7c63a-148">win:UInt16</span></span>|<span data-ttu-id="7c63a-149">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7c63a-150">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7c63a-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="7c63a-151">AppDomainMemAllocated イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="7c63a-152">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7c63a-153">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7c63a-153">Keyword for raising the event</span></span>|<span data-ttu-id="7c63a-154">レベル</span><span class="sxs-lookup"><span data-stu-id="7c63a-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7c63a-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="7c63a-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="7c63a-156">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="7c63a-157">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7c63a-158">イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-158">Event</span></span>|<span data-ttu-id="7c63a-159">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7c63a-159">Event ID</span></span>|<span data-ttu-id="7c63a-160">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7c63a-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="7c63a-161">83</span><span class="sxs-lookup"><span data-stu-id="7c63a-161">83</span></span>|<span data-ttu-id="7c63a-162">アプリケーション ドメインに 4 MB ずつのメモリ (概算) が割り当てられる。</span><span class="sxs-lookup"><span data-stu-id="7c63a-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="7c63a-163">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7c63a-164">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7c63a-164">Field name</span></span>|<span data-ttu-id="7c63a-165">データ型</span><span class="sxs-lookup"><span data-stu-id="7c63a-165">Data type</span></span>|<span data-ttu-id="7c63a-166">説明</span><span class="sxs-lookup"><span data-stu-id="7c63a-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7c63a-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7c63a-167">AppDomainID</span></span>|<span data-ttu-id="7c63a-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-168">win:UInt64</span></span>|<span data-ttu-id="7c63a-169">リソースの使用状況の報告対象のアプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="7c63a-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="7c63a-170">Allocated</span><span class="sxs-lookup"><span data-stu-id="7c63a-170">Allocated</span></span>|<span data-ttu-id="7c63a-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-171">win:UInt64</span></span>|<span data-ttu-id="7c63a-172">アプリケーション ドメインが作成されてから、このアプリケーション ドメインに割り当てられたバイトの合計数 (解放されたメモリの量は引かれない)。</span><span class="sxs-lookup"><span data-stu-id="7c63a-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="7c63a-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7c63a-173">ClrInstanceID</span></span>|<span data-ttu-id="7c63a-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7c63a-174">win:UInt16</span></span>|<span data-ttu-id="7c63a-175">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7c63a-176">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7c63a-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="7c63a-177">AppDomainMemSurvived イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="7c63a-178">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7c63a-179">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7c63a-179">Keyword for raising the event</span></span>|<span data-ttu-id="7c63a-180">レベル</span><span class="sxs-lookup"><span data-stu-id="7c63a-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7c63a-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="7c63a-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="7c63a-182">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="7c63a-183">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7c63a-184">イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-184">Event</span></span>|<span data-ttu-id="7c63a-185">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7c63a-185">Event ID</span></span>|<span data-ttu-id="7c63a-186">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7c63a-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="7c63a-187">84</span><span class="sxs-lookup"><span data-stu-id="7c63a-187">84</span></span>|<span data-ttu-id="7c63a-188">各ガベージ コレクションが終了した。</span><span class="sxs-lookup"><span data-stu-id="7c63a-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="7c63a-189">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7c63a-190">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7c63a-190">Field name</span></span>|<span data-ttu-id="7c63a-191">データ型</span><span class="sxs-lookup"><span data-stu-id="7c63a-191">Data type</span></span>|<span data-ttu-id="7c63a-192">説明</span><span class="sxs-lookup"><span data-stu-id="7c63a-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7c63a-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7c63a-193">AppDomainID</span></span>|<span data-ttu-id="7c63a-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-194">win:UInt64</span></span>|<span data-ttu-id="7c63a-195">リソースの使用状況の報告対象のドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="7c63a-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="7c63a-196">Survived</span><span class="sxs-lookup"><span data-stu-id="7c63a-196">Survived</span></span>|<span data-ttu-id="7c63a-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-197">win:UInt64</span></span>|<span data-ttu-id="7c63a-198">最後のコレクションの実行後に残され、このアプリケーション ドメインによって保持されることが判明しているバイト数。</span><span class="sxs-lookup"><span data-stu-id="7c63a-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="7c63a-199">この数は、完全なコレクションの後では正確で完全ですが、短期コレクションの後では完全ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c63a-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="7c63a-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="7c63a-200">ProcessSurvived</span></span>|<span data-ttu-id="7c63a-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-201">win:UInt64</span></span>|<span data-ttu-id="7c63a-202">最後のコレクション後に残った合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="7c63a-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="7c63a-203">完全なコレクションの後では、この数はマネージ ヒープにライブで保持されるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="7c63a-204">短期コレクションの後では、この数は短期のジェネレーションにライブで保持されるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="7c63a-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7c63a-205">ClrInstanceID</span></span>|<span data-ttu-id="7c63a-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7c63a-206">win:UInt16</span></span>|<span data-ttu-id="7c63a-207">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7c63a-208">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7c63a-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="7c63a-209">ThreadAppDomainEnter イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="7c63a-210">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7c63a-211">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7c63a-211">Keyword for raising the event</span></span>|<span data-ttu-id="7c63a-212">レベル</span><span class="sxs-lookup"><span data-stu-id="7c63a-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7c63a-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="7c63a-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="7c63a-214">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-214">Informational(4)</span></span>|  
|<span data-ttu-id="7c63a-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7c63a-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7c63a-216">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="7c63a-217">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7c63a-218">イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-218">Event</span></span>|<span data-ttu-id="7c63a-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7c63a-219">Event ID</span></span>|<span data-ttu-id="7c63a-220">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7c63a-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="7c63a-221">87</span><span class="sxs-lookup"><span data-stu-id="7c63a-221">87</span></span>|<span data-ttu-id="7c63a-222">アプリケーション ドメインにスレッドが入力される。</span><span class="sxs-lookup"><span data-stu-id="7c63a-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="7c63a-223">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="7c63a-224">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7c63a-224">Field name</span></span>|<span data-ttu-id="7c63a-225">データ型</span><span class="sxs-lookup"><span data-stu-id="7c63a-225">Data type</span></span>|<span data-ttu-id="7c63a-226">説明</span><span class="sxs-lookup"><span data-stu-id="7c63a-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7c63a-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="7c63a-227">ThreadID</span></span>|<span data-ttu-id="7c63a-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-228">win:UInt64</span></span>|<span data-ttu-id="7c63a-229">スレッド ID です</span><span class="sxs-lookup"><span data-stu-id="7c63a-229">The thread identifier.</span></span>|  
|<span data-ttu-id="7c63a-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7c63a-230">AppDomainID</span></span>|<span data-ttu-id="7c63a-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-231">win:UInt64</span></span>|<span data-ttu-id="7c63a-232">アプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="7c63a-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="7c63a-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7c63a-233">ClrInstanceID</span></span>|<span data-ttu-id="7c63a-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7c63a-234">win:UInt16</span></span>|<span data-ttu-id="7c63a-235">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="7c63a-236">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7c63a-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="7c63a-237">ThreadTerminated イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="7c63a-238">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="7c63a-239">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="7c63a-239">Keyword for raising the event</span></span>|<span data-ttu-id="7c63a-240">レベル</span><span class="sxs-lookup"><span data-stu-id="7c63a-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7c63a-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="7c63a-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="7c63a-242">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-242">Informational(4)</span></span>|  
|<span data-ttu-id="7c63a-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="7c63a-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="7c63a-244">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="7c63a-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="7c63a-245">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="7c63a-246">イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-246">Event</span></span>|<span data-ttu-id="7c63a-247">イベント ID</span><span class="sxs-lookup"><span data-stu-id="7c63a-247">Event ID</span></span>|<span data-ttu-id="7c63a-248">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="7c63a-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="7c63a-249">86</span><span class="sxs-lookup"><span data-stu-id="7c63a-249">86</span></span>|<span data-ttu-id="7c63a-250">スレッドが終了する。</span><span class="sxs-lookup"><span data-stu-id="7c63a-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="7c63a-251">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="7c63a-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="7c63a-252">フィールド名</span><span class="sxs-lookup"><span data-stu-id="7c63a-252">Field name</span></span>|<span data-ttu-id="7c63a-253">データ型</span><span class="sxs-lookup"><span data-stu-id="7c63a-253">Data type</span></span>|<span data-ttu-id="7c63a-254">説明</span><span class="sxs-lookup"><span data-stu-id="7c63a-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7c63a-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="7c63a-255">ThreadID</span></span>|<span data-ttu-id="7c63a-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-256">win:UInt64</span></span>|<span data-ttu-id="7c63a-257">スレッド ID です</span><span class="sxs-lookup"><span data-stu-id="7c63a-257">The thread identifier.</span></span>|  
|<span data-ttu-id="7c63a-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="7c63a-258">AppDomainID</span></span>|<span data-ttu-id="7c63a-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="7c63a-259">win:UInt64</span></span>|<span data-ttu-id="7c63a-260">アプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="7c63a-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="7c63a-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7c63a-261">ClrInstanceID</span></span>|<span data-ttu-id="7c63a-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="7c63a-262">win:UInt16</span></span>|<span data-ttu-id="7c63a-263">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="7c63a-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c63a-264">参照</span><span class="sxs-lookup"><span data-stu-id="7c63a-264">See Also</span></span>  
 [<span data-ttu-id="7c63a-265">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="7c63a-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
