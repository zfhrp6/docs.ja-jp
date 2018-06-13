---
title: アプリケーション ドメインのリソース監視 (ARM) ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47ab6e52278c77156e828869dd23575561879bff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398184"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="f00f6-102">アプリケーション ドメインのリソース監視 (ARM) ETW イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f00f6-103">これらのイベントは、アプリケーション ドメインの状態に関する詳細な診断の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="f00f6-104">これらのイベントを使用することもできますが、アプリケーション ドメインのリソース監視 (ARM) の機能を使用しても同じ情報を得られます。</span><span class="sxs-lookup"><span data-stu-id="f00f6-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="f00f6-105">このカテゴリは、次のイベントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f00f6-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="f00f6-106">ThreadCreated イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="f00f6-107">AppDomainMemAllocated イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="f00f6-108">AppDomainMemSurvived イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="f00f6-109">ThreadAppDomainEnter イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="f00f6-110">ThreadTerminated イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="f00f6-111">ThreadCreated イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="f00f6-112">このイベントは、ランダウン プロバイダーで `ThreadDC` としても発生します  ( `AppDomainResourceManagementRundownKeyword` キーワードで発生)。</span><span class="sxs-lookup"><span data-stu-id="f00f6-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="f00f6-113">これは、このカテゴリでランダウン プロバイダーで発生する唯一のイベントです。</span><span class="sxs-lookup"><span data-stu-id="f00f6-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="f00f6-114">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="f00f6-115">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f00f6-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f00f6-116">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="f00f6-116">Keyword for raising the event</span></span>|<span data-ttu-id="f00f6-117">レベル</span><span class="sxs-lookup"><span data-stu-id="f00f6-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f00f6-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f00f6-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f00f6-119">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-119">Informational(4)</span></span>|  
|<span data-ttu-id="f00f6-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f00f6-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f00f6-121">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="f00f6-122">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f00f6-123">イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-123">Event</span></span>|<span data-ttu-id="f00f6-124">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f00f6-124">Event ID</span></span>|<span data-ttu-id="f00f6-125">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="f00f6-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="f00f6-126">85</span><span class="sxs-lookup"><span data-stu-id="f00f6-126">85</span></span>|<span data-ttu-id="f00f6-127">アプリケーション ドメインに対してスレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="f00f6-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="f00f6-128">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f00f6-129">フィールド名</span><span class="sxs-lookup"><span data-stu-id="f00f6-129">Field name</span></span>|<span data-ttu-id="f00f6-130">データ型</span><span class="sxs-lookup"><span data-stu-id="f00f6-130">Data type</span></span>|<span data-ttu-id="f00f6-131">説明</span><span class="sxs-lookup"><span data-stu-id="f00f6-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f00f6-132">ThreadID</span><span class="sxs-lookup"><span data-stu-id="f00f6-132">ThreadID</span></span>|<span data-ttu-id="f00f6-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-133">win:UInt64</span></span>|<span data-ttu-id="f00f6-134">作成されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="f00f6-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f00f6-135">AppDomainID</span></span>|<span data-ttu-id="f00f6-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-136">win:UInt64</span></span>|<span data-ttu-id="f00f6-137">スレッドのアクティビティの報告対象のアプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="f00f6-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="f00f6-138">フラグ</span><span class="sxs-lookup"><span data-stu-id="f00f6-138">Flags</span></span>|<span data-ttu-id="f00f6-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f00f6-139">win:UInt32</span></span>|<span data-ttu-id="f00f6-140">スレッドの作成フラグ</span><span class="sxs-lookup"><span data-stu-id="f00f6-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="f00f6-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="f00f6-141">ManagedThreadIndex</span></span>|<span data-ttu-id="f00f6-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f00f6-142">win:UInt32</span></span>|<span data-ttu-id="f00f6-143">作成されたスレッドのマネージ インデックス。</span><span class="sxs-lookup"><span data-stu-id="f00f6-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="f00f6-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="f00f6-144">OSThreadID</span></span>|<span data-ttu-id="f00f6-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f00f6-145">win:UInt32</span></span>|<span data-ttu-id="f00f6-146">作成されたスレッドのオペレーティング システム ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="f00f6-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f00f6-147">ClrInstanceID</span></span>|<span data-ttu-id="f00f6-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f00f6-148">win:UInt16</span></span>|<span data-ttu-id="f00f6-149">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f00f6-150">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="f00f6-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="f00f6-151">AppDomainMemAllocated イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="f00f6-152">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f00f6-153">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="f00f6-153">Keyword for raising the event</span></span>|<span data-ttu-id="f00f6-154">レベル</span><span class="sxs-lookup"><span data-stu-id="f00f6-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f00f6-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f00f6-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f00f6-156">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="f00f6-157">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f00f6-158">イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-158">Event</span></span>|<span data-ttu-id="f00f6-159">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f00f6-159">Event ID</span></span>|<span data-ttu-id="f00f6-160">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="f00f6-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="f00f6-161">83</span><span class="sxs-lookup"><span data-stu-id="f00f6-161">83</span></span>|<span data-ttu-id="f00f6-162">アプリケーション ドメインに 4 MB ずつのメモリ (概算) が割り当てられる。</span><span class="sxs-lookup"><span data-stu-id="f00f6-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="f00f6-163">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f00f6-164">フィールド名</span><span class="sxs-lookup"><span data-stu-id="f00f6-164">Field name</span></span>|<span data-ttu-id="f00f6-165">データ型</span><span class="sxs-lookup"><span data-stu-id="f00f6-165">Data type</span></span>|<span data-ttu-id="f00f6-166">説明</span><span class="sxs-lookup"><span data-stu-id="f00f6-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f00f6-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f00f6-167">AppDomainID</span></span>|<span data-ttu-id="f00f6-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-168">win:UInt64</span></span>|<span data-ttu-id="f00f6-169">リソースの使用状況の報告対象のアプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="f00f6-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="f00f6-170">Allocated</span><span class="sxs-lookup"><span data-stu-id="f00f6-170">Allocated</span></span>|<span data-ttu-id="f00f6-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-171">win:UInt64</span></span>|<span data-ttu-id="f00f6-172">アプリケーション ドメインが作成されてから、このアプリケーション ドメインに割り当てられたバイトの合計数 (解放されたメモリの量は引かれない)。</span><span class="sxs-lookup"><span data-stu-id="f00f6-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="f00f6-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f00f6-173">ClrInstanceID</span></span>|<span data-ttu-id="f00f6-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f00f6-174">win:UInt16</span></span>|<span data-ttu-id="f00f6-175">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f00f6-176">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="f00f6-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="f00f6-177">AppDomainMemSurvived イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="f00f6-178">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f00f6-179">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="f00f6-179">Keyword for raising the event</span></span>|<span data-ttu-id="f00f6-180">レベル</span><span class="sxs-lookup"><span data-stu-id="f00f6-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f00f6-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f00f6-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f00f6-182">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="f00f6-183">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f00f6-184">イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-184">Event</span></span>|<span data-ttu-id="f00f6-185">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f00f6-185">Event ID</span></span>|<span data-ttu-id="f00f6-186">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="f00f6-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="f00f6-187">84</span><span class="sxs-lookup"><span data-stu-id="f00f6-187">84</span></span>|<span data-ttu-id="f00f6-188">各ガベージ コレクションが終了した。</span><span class="sxs-lookup"><span data-stu-id="f00f6-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="f00f6-189">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f00f6-190">フィールド名</span><span class="sxs-lookup"><span data-stu-id="f00f6-190">Field name</span></span>|<span data-ttu-id="f00f6-191">データ型</span><span class="sxs-lookup"><span data-stu-id="f00f6-191">Data type</span></span>|<span data-ttu-id="f00f6-192">説明</span><span class="sxs-lookup"><span data-stu-id="f00f6-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f00f6-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f00f6-193">AppDomainID</span></span>|<span data-ttu-id="f00f6-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-194">win:UInt64</span></span>|<span data-ttu-id="f00f6-195">リソースの使用状況の報告対象のドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="f00f6-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="f00f6-196">Survived</span><span class="sxs-lookup"><span data-stu-id="f00f6-196">Survived</span></span>|<span data-ttu-id="f00f6-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-197">win:UInt64</span></span>|<span data-ttu-id="f00f6-198">最後のコレクションの実行後に残され、このアプリケーション ドメインによって保持されることが判明しているバイト数。</span><span class="sxs-lookup"><span data-stu-id="f00f6-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="f00f6-199">この数は、完全なコレクションの後では正確で完全ですが、短期コレクションの後では完全ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f00f6-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="f00f6-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="f00f6-200">ProcessSurvived</span></span>|<span data-ttu-id="f00f6-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-201">win:UInt64</span></span>|<span data-ttu-id="f00f6-202">最後のコレクション後に残った合計バイト数。</span><span class="sxs-lookup"><span data-stu-id="f00f6-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="f00f6-203">完全なコレクションの後では、この数はマネージ ヒープにライブで保持されるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="f00f6-204">短期コレクションの後では、この数は短期のジェネレーションにライブで保持されるバイト数を表します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="f00f6-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f00f6-205">ClrInstanceID</span></span>|<span data-ttu-id="f00f6-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f00f6-206">win:UInt16</span></span>|<span data-ttu-id="f00f6-207">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f00f6-208">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="f00f6-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="f00f6-209">ThreadAppDomainEnter イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="f00f6-210">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f00f6-211">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="f00f6-211">Keyword for raising the event</span></span>|<span data-ttu-id="f00f6-212">レベル</span><span class="sxs-lookup"><span data-stu-id="f00f6-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f00f6-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f00f6-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f00f6-214">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-214">Informational(4)</span></span>|  
|<span data-ttu-id="f00f6-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f00f6-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f00f6-216">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="f00f6-217">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f00f6-218">イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-218">Event</span></span>|<span data-ttu-id="f00f6-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f00f6-219">Event ID</span></span>|<span data-ttu-id="f00f6-220">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="f00f6-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="f00f6-221">87</span><span class="sxs-lookup"><span data-stu-id="f00f6-221">87</span></span>|<span data-ttu-id="f00f6-222">アプリケーション ドメインにスレッドが入力される。</span><span class="sxs-lookup"><span data-stu-id="f00f6-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="f00f6-223">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f00f6-224">フィールド名</span><span class="sxs-lookup"><span data-stu-id="f00f6-224">Field name</span></span>|<span data-ttu-id="f00f6-225">データ型</span><span class="sxs-lookup"><span data-stu-id="f00f6-225">Data type</span></span>|<span data-ttu-id="f00f6-226">説明</span><span class="sxs-lookup"><span data-stu-id="f00f6-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f00f6-227">ThreadID</span><span class="sxs-lookup"><span data-stu-id="f00f6-227">ThreadID</span></span>|<span data-ttu-id="f00f6-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-228">win:UInt64</span></span>|<span data-ttu-id="f00f6-229">スレッド ID です</span><span class="sxs-lookup"><span data-stu-id="f00f6-229">The thread identifier.</span></span>|  
|<span data-ttu-id="f00f6-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f00f6-230">AppDomainID</span></span>|<span data-ttu-id="f00f6-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-231">win:UInt64</span></span>|<span data-ttu-id="f00f6-232">アプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="f00f6-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="f00f6-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f00f6-233">ClrInstanceID</span></span>|<span data-ttu-id="f00f6-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f00f6-234">win:UInt16</span></span>|<span data-ttu-id="f00f6-235">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f00f6-236">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="f00f6-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="f00f6-237">ThreadTerminated イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="f00f6-238">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f00f6-239">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="f00f6-239">Keyword for raising the event</span></span>|<span data-ttu-id="f00f6-240">レベル</span><span class="sxs-lookup"><span data-stu-id="f00f6-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f00f6-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="f00f6-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="f00f6-242">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-242">Informational(4)</span></span>|  
|<span data-ttu-id="f00f6-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f00f6-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f00f6-244">情報通知 (4)</span><span class="sxs-lookup"><span data-stu-id="f00f6-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="f00f6-245">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f00f6-246">イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-246">Event</span></span>|<span data-ttu-id="f00f6-247">イベント ID</span><span class="sxs-lookup"><span data-stu-id="f00f6-247">Event ID</span></span>|<span data-ttu-id="f00f6-248">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="f00f6-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="f00f6-249">86</span><span class="sxs-lookup"><span data-stu-id="f00f6-249">86</span></span>|<span data-ttu-id="f00f6-250">スレッドが終了する。</span><span class="sxs-lookup"><span data-stu-id="f00f6-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="f00f6-251">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="f00f6-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="f00f6-252">フィールド名</span><span class="sxs-lookup"><span data-stu-id="f00f6-252">Field name</span></span>|<span data-ttu-id="f00f6-253">データ型</span><span class="sxs-lookup"><span data-stu-id="f00f6-253">Data type</span></span>|<span data-ttu-id="f00f6-254">説明</span><span class="sxs-lookup"><span data-stu-id="f00f6-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f00f6-255">ThreadID</span><span class="sxs-lookup"><span data-stu-id="f00f6-255">ThreadID</span></span>|<span data-ttu-id="f00f6-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-256">win:UInt64</span></span>|<span data-ttu-id="f00f6-257">スレッド ID です</span><span class="sxs-lookup"><span data-stu-id="f00f6-257">The thread identifier.</span></span>|  
|<span data-ttu-id="f00f6-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f00f6-258">AppDomainID</span></span>|<span data-ttu-id="f00f6-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f00f6-259">win:UInt64</span></span>|<span data-ttu-id="f00f6-260">アプリケーション ドメインの識別子。</span><span class="sxs-lookup"><span data-stu-id="f00f6-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="f00f6-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f00f6-261">ClrInstanceID</span></span>|<span data-ttu-id="f00f6-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f00f6-262">win:UInt16</span></span>|<span data-ttu-id="f00f6-263">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="f00f6-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f00f6-264">関連項目</span><span class="sxs-lookup"><span data-stu-id="f00f6-264">See Also</span></span>  
 [<span data-ttu-id="f00f6-265">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="f00f6-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
