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
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="2e05e-102">アプリケーション ドメインのリソース監視 (ARM) ETW イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<span data-ttu-id="2e05e-103"><a name="top"></a> これらのイベントは、アプリケーション ドメインの状態に関する詳細な診断の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-103"><a name="top"></a> These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="2e05e-104">これらのイベントを使用することもできますが、アプリケーション ドメインのリソース監視 (ARM) の機能を使用しても同じ情報を得られます。</span><span class="sxs-lookup"><span data-stu-id="2e05e-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="2e05e-105">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2e05e-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="2e05e-106">ThreadCreated イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="2e05e-107">AppDomainMemAllocated イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="2e05e-108">AppDomainMemSurvived イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="2e05e-109">ThreadAppDomainEnter イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="2e05e-110">ThreadTerminated イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="2e05e-111">ThreadCreated イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="2e05e-112">このイベントは、ランダウン プロバイダーで `ThreadDC` としても発生します  ( `AppDomainResourceManagementRundownKeyword` キーワードで発生)。</span><span class="sxs-lookup"><span data-stu-id="2e05e-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="2e05e-113">これは、このカテゴリでランダウン プロバイダーで発生する唯一のイベントです。</span><span class="sxs-lookup"><span data-stu-id="2e05e-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="2e05e-114">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="2e05e-115">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2e05e-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2e05e-116">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2e05e-116">Keyword for raising the event</span></span>|<span data-ttu-id="2e05e-117">レベル</span><span class="sxs-lookup"><span data-stu-id="2e05e-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2e05e-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2e05e-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2e05e-119">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-119">Informational(4)</span></span>|  
|<span data-ttu-id="2e05e-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2e05e-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2e05e-121">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="2e05e-122">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2e05e-123">イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-123">Event</span></span>|<span data-ttu-id="2e05e-124">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2e05e-124">Event ID</span></span>|<span data-ttu-id="2e05e-125">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2e05e-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="2e05e-126">85</span><span class="sxs-lookup"><span data-stu-id="2e05e-126">85</span></span>|<span data-ttu-id="2e05e-127">アプリケーション ドメインに対してスレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="2e05e-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="2e05e-128">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2e05e-129">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2e05e-129">Field name</span></span>|<span data-ttu-id="2e05e-130">データ型</span><span class="sxs-lookup"><span data-stu-id="2e05e-130">Data type</span></span>|<span data-ttu-id="2e05e-131">説明</span><span class="sxs-lookup"><span data-stu-id="2e05e-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2e05e-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="2e05e-132">ThreadID</span></span>|<span data-ttu-id="2e05e-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-133">win:UInt64</span></span>|<span data-ttu-id="2e05e-134">作成されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="2e05e-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2e05e-135">AppDomainID</span></span>|<span data-ttu-id="2e05e-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-136">win:UInt64</span></span>|<span data-ttu-id="2e05e-137">スレッドのアクティビティの報告対象のアプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="2e05e-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="2e05e-138">フラグ</span><span class="sxs-lookup"><span data-stu-id="2e05e-138">Flags</span></span>|<span data-ttu-id="2e05e-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2e05e-139">win:UInt32</span></span>|<span data-ttu-id="2e05e-140">スレッドの作成フラグ</span><span class="sxs-lookup"><span data-stu-id="2e05e-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="2e05e-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="2e05e-141">ManagedThreadIndex</span></span>|<span data-ttu-id="2e05e-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2e05e-142">win:UInt32</span></span>|<span data-ttu-id="2e05e-143">作成されたスレッドのマネージ インデックス。</span><span class="sxs-lookup"><span data-stu-id="2e05e-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="2e05e-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="2e05e-144">OSThreadID</span></span>|<span data-ttu-id="2e05e-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="2e05e-145">win:UInt32</span></span>|<span data-ttu-id="2e05e-146">作成されたスレッドのオペレーティング システム ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="2e05e-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2e05e-147">ClrInstanceID</span></span>|<span data-ttu-id="2e05e-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2e05e-148">win:UInt16</span></span>|<span data-ttu-id="2e05e-149">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2e05e-150">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2e05e-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="2e05e-151">AppDomainMemAllocated イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="2e05e-152">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2e05e-153">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2e05e-153">Keyword for raising the event</span></span>|<span data-ttu-id="2e05e-154">レベル</span><span class="sxs-lookup"><span data-stu-id="2e05e-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2e05e-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2e05e-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2e05e-156">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="2e05e-157">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2e05e-158">イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-158">Event</span></span>|<span data-ttu-id="2e05e-159">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2e05e-159">Event ID</span></span>|<span data-ttu-id="2e05e-160">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2e05e-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="2e05e-161">83</span><span class="sxs-lookup"><span data-stu-id="2e05e-161">83</span></span>|<span data-ttu-id="2e05e-162">アプリケーション ドメインに 4 MB ずつのメモリ (概算) が割り当てられる。</span><span class="sxs-lookup"><span data-stu-id="2e05e-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="2e05e-163">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2e05e-164">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2e05e-164">Field name</span></span>|<span data-ttu-id="2e05e-165">データ型</span><span class="sxs-lookup"><span data-stu-id="2e05e-165">Data type</span></span>|<span data-ttu-id="2e05e-166">説明</span><span class="sxs-lookup"><span data-stu-id="2e05e-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2e05e-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2e05e-167">AppDomainID</span></span>|<span data-ttu-id="2e05e-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-168">win:UInt64</span></span>|<span data-ttu-id="2e05e-169">リソースの使用状況の報告対象のアプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="2e05e-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="2e05e-170">Allocated</span><span class="sxs-lookup"><span data-stu-id="2e05e-170">Allocated</span></span>|<span data-ttu-id="2e05e-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-171">win:UInt64</span></span>|<span data-ttu-id="2e05e-172">アプリケーション ドメインが作成されてから、このアプリケーション ドメインに割り当てられたバイトの合計数 (解放されたメモリの量は引かれない)。</span><span class="sxs-lookup"><span data-stu-id="2e05e-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="2e05e-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2e05e-173">ClrInstanceID</span></span>|<span data-ttu-id="2e05e-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2e05e-174">win:UInt16</span></span>|<span data-ttu-id="2e05e-175">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2e05e-176">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2e05e-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="2e05e-177">AppDomainMemSurvived イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="2e05e-178">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2e05e-179">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2e05e-179">Keyword for raising the event</span></span>|<span data-ttu-id="2e05e-180">レベル</span><span class="sxs-lookup"><span data-stu-id="2e05e-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2e05e-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2e05e-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2e05e-182">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="2e05e-183">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2e05e-184">イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-184">Event</span></span>|<span data-ttu-id="2e05e-185">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2e05e-185">Event ID</span></span>|<span data-ttu-id="2e05e-186">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2e05e-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="2e05e-187">84</span><span class="sxs-lookup"><span data-stu-id="2e05e-187">84</span></span>|<span data-ttu-id="2e05e-188">各ガベージ コレクションが終了した。</span><span class="sxs-lookup"><span data-stu-id="2e05e-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="2e05e-189">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2e05e-190">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2e05e-190">Field name</span></span>|<span data-ttu-id="2e05e-191">データ型</span><span class="sxs-lookup"><span data-stu-id="2e05e-191">Data type</span></span>|<span data-ttu-id="2e05e-192">説明</span><span class="sxs-lookup"><span data-stu-id="2e05e-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2e05e-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2e05e-193">AppDomainID</span></span>|<span data-ttu-id="2e05e-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-194">win:UInt64</span></span>|<span data-ttu-id="2e05e-195">リソースの使用状況の報告対象のドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="2e05e-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="2e05e-196">Survived</span><span class="sxs-lookup"><span data-stu-id="2e05e-196">Survived</span></span>|<span data-ttu-id="2e05e-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-197">win:UInt64</span></span>|<span data-ttu-id="2e05e-198">最後のコレクションの実行後に残され、このアプリケーション ドメインによって保持されることが判明しているバイト数。</span><span class="sxs-lookup"><span data-stu-id="2e05e-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="2e05e-199">この数は、完全なコレクションの後では正確で完全ですが、短期コレクションの後では完全ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e05e-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="2e05e-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="2e05e-200">ProcessSurvived</span></span>|<span data-ttu-id="2e05e-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-201">win:UInt64</span></span>|<span data-ttu-id="2e05e-202">最後のコレクション後に残った合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="2e05e-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="2e05e-203">完全なコレクションの後では、この数はマネージ ヒープにライブで保持されるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="2e05e-204">短期コレクションの後では、この数は短期のジェネレーションにライブで保持されるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="2e05e-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2e05e-205">ClrInstanceID</span></span>|<span data-ttu-id="2e05e-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2e05e-206">win:UInt16</span></span>|<span data-ttu-id="2e05e-207">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2e05e-208">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2e05e-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="2e05e-209">ThreadAppDomainEnter イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="2e05e-210">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2e05e-211">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2e05e-211">Keyword for raising the event</span></span>|<span data-ttu-id="2e05e-212">レベル</span><span class="sxs-lookup"><span data-stu-id="2e05e-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2e05e-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2e05e-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2e05e-214">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-214">Informational(4)</span></span>|  
|<span data-ttu-id="2e05e-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2e05e-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2e05e-216">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="2e05e-217">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2e05e-218">イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-218">Event</span></span>|<span data-ttu-id="2e05e-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2e05e-219">Event ID</span></span>|<span data-ttu-id="2e05e-220">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2e05e-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="2e05e-221">87</span><span class="sxs-lookup"><span data-stu-id="2e05e-221">87</span></span>|<span data-ttu-id="2e05e-222">アプリケーション ドメインにスレッドが入力される。</span><span class="sxs-lookup"><span data-stu-id="2e05e-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="2e05e-223">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2e05e-224">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2e05e-224">Field name</span></span>|<span data-ttu-id="2e05e-225">データ型</span><span class="sxs-lookup"><span data-stu-id="2e05e-225">Data type</span></span>|<span data-ttu-id="2e05e-226">説明</span><span class="sxs-lookup"><span data-stu-id="2e05e-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2e05e-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="2e05e-227">ThreadID</span></span>|<span data-ttu-id="2e05e-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-228">win:UInt64</span></span>|<span data-ttu-id="2e05e-229">スレッド ID です</span><span class="sxs-lookup"><span data-stu-id="2e05e-229">The thread identifier.</span></span>|  
|<span data-ttu-id="2e05e-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2e05e-230">AppDomainID</span></span>|<span data-ttu-id="2e05e-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-231">win:UInt64</span></span>|<span data-ttu-id="2e05e-232">アプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="2e05e-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="2e05e-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2e05e-233">ClrInstanceID</span></span>|<span data-ttu-id="2e05e-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2e05e-234">win:UInt16</span></span>|<span data-ttu-id="2e05e-235">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="2e05e-236">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="2e05e-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="2e05e-237">ThreadTerminated イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="2e05e-238">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="2e05e-239">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2e05e-239">Keyword for raising the event</span></span>|<span data-ttu-id="2e05e-240">レベル</span><span class="sxs-lookup"><span data-stu-id="2e05e-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2e05e-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="2e05e-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="2e05e-242">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-242">Informational(4)</span></span>|  
|<span data-ttu-id="2e05e-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="2e05e-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="2e05e-244">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="2e05e-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="2e05e-245">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2e05e-246">イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-246">Event</span></span>|<span data-ttu-id="2e05e-247">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2e05e-247">Event ID</span></span>|<span data-ttu-id="2e05e-248">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2e05e-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="2e05e-249">86</span><span class="sxs-lookup"><span data-stu-id="2e05e-249">86</span></span>|<span data-ttu-id="2e05e-250">スレッドが終了する。</span><span class="sxs-lookup"><span data-stu-id="2e05e-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="2e05e-251">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="2e05e-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="2e05e-252">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2e05e-252">Field name</span></span>|<span data-ttu-id="2e05e-253">データ型</span><span class="sxs-lookup"><span data-stu-id="2e05e-253">Data type</span></span>|<span data-ttu-id="2e05e-254">説明</span><span class="sxs-lookup"><span data-stu-id="2e05e-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2e05e-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="2e05e-255">ThreadID</span></span>|<span data-ttu-id="2e05e-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-256">win:UInt64</span></span>|<span data-ttu-id="2e05e-257">スレッド ID です</span><span class="sxs-lookup"><span data-stu-id="2e05e-257">The thread identifier.</span></span>|  
|<span data-ttu-id="2e05e-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="2e05e-258">AppDomainID</span></span>|<span data-ttu-id="2e05e-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="2e05e-259">win:UInt64</span></span>|<span data-ttu-id="2e05e-260">アプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="2e05e-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="2e05e-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2e05e-261">ClrInstanceID</span></span>|<span data-ttu-id="2e05e-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="2e05e-262">win:UInt16</span></span>|<span data-ttu-id="2e05e-263">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2e05e-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e05e-264">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e05e-264">See Also</span></span>  
 [<span data-ttu-id="2e05e-265">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="2e05e-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
