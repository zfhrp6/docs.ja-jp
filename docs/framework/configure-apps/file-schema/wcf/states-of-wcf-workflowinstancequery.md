---
title: "WCF の &lt;states&gt;、&lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5995ebfc2cee0f636d2acd8b1cadead0bc7b67e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="e19a2-102">WCF の &lt;states&gt;、&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e19a2-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="e19a2-103">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="e19a2-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e19a2-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e19a2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e19a2-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e19a2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e19a2-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="e19a2-106">\<tracking></span></span>  
<span data-ttu-id="e19a2-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e19a2-107">\<trackingProfile></span></span>  
<span data-ttu-id="e19a2-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="e19a2-108">\<workflow></span></span>  
<span data-ttu-id="e19a2-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="e19a2-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e19a2-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e19a2-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e19a2-111">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="e19a2-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e19a2-112">構文</span><span class="sxs-lookup"><span data-stu-id="e19a2-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e19a2-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e19a2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e19a2-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e19a2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e19a2-115">属性</span><span class="sxs-lookup"><span data-stu-id="e19a2-115">Attributes</span></span>  
 <span data-ttu-id="e19a2-116">なし。</span><span class="sxs-lookup"><span data-stu-id="e19a2-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e19a2-117">子要素</span><span class="sxs-lookup"><span data-stu-id="e19a2-117">Child Elements</span></span>  
  
|<span data-ttu-id="e19a2-118">要素</span><span class="sxs-lookup"><span data-stu-id="e19a2-118">Element</span></span>|<span data-ttu-id="e19a2-119">説明</span><span class="sxs-lookup"><span data-stu-id="e19a2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e19a2-120">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="e19a2-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="e19a2-121">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態。</span><span class="sxs-lookup"><span data-stu-id="e19a2-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e19a2-122">親要素</span><span class="sxs-lookup"><span data-stu-id="e19a2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e19a2-123">要素</span><span class="sxs-lookup"><span data-stu-id="e19a2-123">Element</span></span>|<span data-ttu-id="e19a2-124">説明</span><span class="sxs-lookup"><span data-stu-id="e19a2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e19a2-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e19a2-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="e19a2-126">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリ。</span><span class="sxs-lookup"><span data-stu-id="e19a2-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e19a2-127">コメント</span><span class="sxs-lookup"><span data-stu-id="e19a2-127">Remarks</span></span>  
 <span data-ttu-id="e19a2-128">返されたレコードは、このコレクションの状態でフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="e19a2-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="e19a2-129">次の表に、有効な状態の値を示します。</span><span class="sxs-lookup"><span data-stu-id="e19a2-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="e19a2-130">状態</span><span class="sxs-lookup"><span data-stu-id="e19a2-130">State</span></span>|<span data-ttu-id="e19a2-131">説明</span><span class="sxs-lookup"><span data-stu-id="e19a2-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e19a2-132">Aborted</span><span class="sxs-lookup"><span data-stu-id="e19a2-132">Aborted</span></span>|<span data-ttu-id="e19a2-133">ワークフロー インスタンスは中止されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e19a2-134">Completed</span><span class="sxs-lookup"><span data-stu-id="e19a2-134">Completed</span></span>|<span data-ttu-id="e19a2-135">ワークフロー インスタンスは完了しました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e19a2-136">Deleted</span><span class="sxs-lookup"><span data-stu-id="e19a2-136">Deleted</span></span>|<span data-ttu-id="e19a2-137">ワークフロー インスタンスは削除されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e19a2-138">Idle</span><span class="sxs-lookup"><span data-stu-id="e19a2-138">Idle</span></span>|<span data-ttu-id="e19a2-139">ワークフロー インスタンスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="e19a2-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e19a2-140">Persisted</span><span class="sxs-lookup"><span data-stu-id="e19a2-140">Persisted</span></span>|<span data-ttu-id="e19a2-141">ワークフロー インスタンスは永続化されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e19a2-142">Resumed</span><span class="sxs-lookup"><span data-stu-id="e19a2-142">Resumed</span></span>|<span data-ttu-id="e19a2-143">ワークフロー インスタンスが再開されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e19a2-144">Started</span><span class="sxs-lookup"><span data-stu-id="e19a2-144">Started</span></span>|<span data-ttu-id="e19a2-145">ワークフロー インスタンスが開始されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e19a2-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="e19a2-146">UnhandledException</span></span>|<span data-ttu-id="e19a2-147">ワークフロー インスタンスで未処理の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e19a2-148">アンロード</span><span class="sxs-lookup"><span data-stu-id="e19a2-148">Unloaded</span></span>|<span data-ttu-id="e19a2-149">ワークフロー インスタンスはアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e19a2-150">Canceled</span><span class="sxs-lookup"><span data-stu-id="e19a2-150">Canceled</span></span>|<span data-ttu-id="e19a2-151">ワークフロー インスタンスは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e19a2-152">Suspended</span><span class="sxs-lookup"><span data-stu-id="e19a2-152">Suspended</span></span>|<span data-ttu-id="e19a2-153">ワークフロー インスタンスが中断されています。</span><span class="sxs-lookup"><span data-stu-id="e19a2-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e19a2-154">Terminated</span><span class="sxs-lookup"><span data-stu-id="e19a2-154">Terminated</span></span>|<span data-ttu-id="e19a2-155">ワークフロー インスタンスは終了しました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e19a2-156">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="e19a2-156">Unsuspended</span></span>|<span data-ttu-id="e19a2-157">ワークフロー インスタンスの中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="e19a2-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e19a2-158">例</span><span class="sxs-lookup"><span data-stu-id="e19a2-158">Example</span></span>  
 <span data-ttu-id="e19a2-159">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="e19a2-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e19a2-160">参照</span><span class="sxs-lookup"><span data-stu-id="e19a2-160">See Also</span></span>  
 <span data-ttu-id="e19a2-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e19a2-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e19a2-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e19a2-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e19a2-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e19a2-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e19a2-164">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="e19a2-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e19a2-165">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="e19a2-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
