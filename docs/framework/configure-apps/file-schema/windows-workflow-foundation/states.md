---
title: "&lt;状態&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73848bd1b8b23d6135572dc7fbb7b5e15b169554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltstatesgt"></a><span data-ttu-id="f4e02-102">&lt;状態&gt;</span><span class="sxs-lookup"><span data-stu-id="f4e02-102">&lt;states&gt;</span></span>
<span data-ttu-id="f4e02-103">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f4e02-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="f4e02-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f4e02-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f4e02-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f4e02-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f4e02-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="f4e02-106">\<tracking></span></span>  
<span data-ttu-id="f4e02-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f4e02-107">\<trackingProfile></span></span>  
<span data-ttu-id="f4e02-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="f4e02-108">\<workflow></span></span>  
<span data-ttu-id="f4e02-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f4e02-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="f4e02-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f4e02-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="f4e02-111">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="f4e02-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e02-112">構文</span><span class="sxs-lookup"><span data-stu-id="f4e02-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4e02-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f4e02-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f4e02-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4e02-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4e02-115">属性</span><span class="sxs-lookup"><span data-stu-id="f4e02-115">Attributes</span></span>  
 <span data-ttu-id="f4e02-116">なし。</span><span class="sxs-lookup"><span data-stu-id="f4e02-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4e02-117">子要素</span><span class="sxs-lookup"><span data-stu-id="f4e02-117">Child Elements</span></span>  
  
|<span data-ttu-id="f4e02-118">要素</span><span class="sxs-lookup"><span data-stu-id="f4e02-118">Element</span></span>|<span data-ttu-id="f4e02-119">説明</span><span class="sxs-lookup"><span data-stu-id="f4e02-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4e02-120">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="f4e02-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="f4e02-121">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態。</span><span class="sxs-lookup"><span data-stu-id="f4e02-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4e02-122">親要素</span><span class="sxs-lookup"><span data-stu-id="f4e02-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f4e02-123">要素</span><span class="sxs-lookup"><span data-stu-id="f4e02-123">Element</span></span>|<span data-ttu-id="f4e02-124">説明</span><span class="sxs-lookup"><span data-stu-id="f4e02-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4e02-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f4e02-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="f4e02-126">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリ。</span><span class="sxs-lookup"><span data-stu-id="f4e02-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e02-127">コメント</span><span class="sxs-lookup"><span data-stu-id="f4e02-127">Remarks</span></span>  
 <span data-ttu-id="f4e02-128">返されたレコードは、このコレクションの状態でフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="f4e02-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="f4e02-129">次の表に、有効な状態の値を示します。</span><span class="sxs-lookup"><span data-stu-id="f4e02-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="f4e02-130">状態</span><span class="sxs-lookup"><span data-stu-id="f4e02-130">State</span></span>|<span data-ttu-id="f4e02-131">説明</span><span class="sxs-lookup"><span data-stu-id="f4e02-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f4e02-132">Aborted</span><span class="sxs-lookup"><span data-stu-id="f4e02-132">Aborted</span></span>|<span data-ttu-id="f4e02-133">ワークフロー インスタンスは中止されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f4e02-134">Completed</span><span class="sxs-lookup"><span data-stu-id="f4e02-134">Completed</span></span>|<span data-ttu-id="f4e02-135">ワークフロー インスタンスは完了しました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f4e02-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="f4e02-136">Deleted</span></span>|<span data-ttu-id="f4e02-137">ワークフロー インスタンスは削除されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f4e02-138">Idle</span><span class="sxs-lookup"><span data-stu-id="f4e02-138">Idle</span></span>|<span data-ttu-id="f4e02-139">ワークフロー インスタンスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="f4e02-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f4e02-140">Persisted</span><span class="sxs-lookup"><span data-stu-id="f4e02-140">Persisted</span></span>|<span data-ttu-id="f4e02-141">ワークフロー インスタンスは永続化されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f4e02-142">Resumed</span><span class="sxs-lookup"><span data-stu-id="f4e02-142">Resumed</span></span>|<span data-ttu-id="f4e02-143">ワークフロー インスタンスが再開されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f4e02-144">Started</span><span class="sxs-lookup"><span data-stu-id="f4e02-144">Started</span></span>|<span data-ttu-id="f4e02-145">ワークフロー インスタンスが開始されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f4e02-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="f4e02-146">UnhandledException</span></span>|<span data-ttu-id="f4e02-147">ワークフロー インスタンスで未処理の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f4e02-148">アンロード</span><span class="sxs-lookup"><span data-stu-id="f4e02-148">Unloaded</span></span>|<span data-ttu-id="f4e02-149">ワークフロー インスタンスはアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f4e02-150">Canceled</span><span class="sxs-lookup"><span data-stu-id="f4e02-150">Canceled</span></span>|<span data-ttu-id="f4e02-151">ワークフロー インスタンスは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f4e02-152">Suspended</span><span class="sxs-lookup"><span data-stu-id="f4e02-152">Suspended</span></span>|<span data-ttu-id="f4e02-153">ワークフロー インスタンスが中断されています。</span><span class="sxs-lookup"><span data-stu-id="f4e02-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f4e02-154">Terminated</span><span class="sxs-lookup"><span data-stu-id="f4e02-154">Terminated</span></span>|<span data-ttu-id="f4e02-155">ワークフロー インスタンスは終了しました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f4e02-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="f4e02-156">Unsuspended</span></span>|<span data-ttu-id="f4e02-157">ワークフロー インスタンスの中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="f4e02-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f4e02-158">例</span><span class="sxs-lookup"><span data-stu-id="f4e02-158">Example</span></span>  
 <span data-ttu-id="f4e02-159">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="f4e02-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4e02-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4e02-160">See Also</span></span>  
 <span data-ttu-id="f4e02-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f4e02-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f4e02-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f4e02-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f4e02-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f4e02-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f4e02-164">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="f4e02-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f4e02-165">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="f4e02-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
