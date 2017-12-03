---
title: '&lt;state&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f1ed21f359e9f0e2b07154bc37d3352dd52db12
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltstategt"></a><span data-ttu-id="f12e5-102">&lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="f12e5-102">&lt;state&gt;</span></span>
<span data-ttu-id="f12e5-103">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="f12e5-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="f12e5-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f12e5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f12e5-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f12e5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f12e5-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="f12e5-106">\<tracking></span></span>  
<span data-ttu-id="f12e5-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f12e5-107">\<trackingProfile></span></span>  
<span data-ttu-id="f12e5-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="f12e5-108">\<workflow></span></span>  
<span data-ttu-id="f12e5-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="f12e5-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="f12e5-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f12e5-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="f12e5-111">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="f12e5-111">\<states></span></span>  
<span data-ttu-id="f12e5-112">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="f12e5-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12e5-113">構文</span><span class="sxs-lookup"><span data-stu-id="f12e5-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f12e5-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f12e5-114">Attributes and Elements</span></span>  
 <span data-ttu-id="f12e5-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f12e5-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f12e5-116">属性</span><span class="sxs-lookup"><span data-stu-id="f12e5-116">Attributes</span></span>  
  
|<span data-ttu-id="f12e5-117">属性</span><span class="sxs-lookup"><span data-stu-id="f12e5-117">Attribute</span></span>|<span data-ttu-id="f12e5-118">説明</span><span class="sxs-lookup"><span data-stu-id="f12e5-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f12e5-119">name</span><span class="sxs-lookup"><span data-stu-id="f12e5-119">name</span></span>|<span data-ttu-id="f12e5-120">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="f12e5-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f12e5-121">子要素</span><span class="sxs-lookup"><span data-stu-id="f12e5-121">Child Elements</span></span>  
 <span data-ttu-id="f12e5-122">なし。</span><span class="sxs-lookup"><span data-stu-id="f12e5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f12e5-123">親要素</span><span class="sxs-lookup"><span data-stu-id="f12e5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f12e5-124">要素</span><span class="sxs-lookup"><span data-stu-id="f12e5-124">Element</span></span>|<span data-ttu-id="f12e5-125">説明</span><span class="sxs-lookup"><span data-stu-id="f12e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f12e5-126">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="f12e5-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="f12e5-127">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクション。</span><span class="sxs-lookup"><span data-stu-id="f12e5-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f12e5-128">コメント</span><span class="sxs-lookup"><span data-stu-id="f12e5-128">Remarks</span></span>  
 <span data-ttu-id="f12e5-129">返されたレコードは、このコレクションの状態でフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="f12e5-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="f12e5-130">次の表に、有効な状態の値を示します。</span><span class="sxs-lookup"><span data-stu-id="f12e5-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="f12e5-131">状態</span><span class="sxs-lookup"><span data-stu-id="f12e5-131">State</span></span>|<span data-ttu-id="f12e5-132">説明</span><span class="sxs-lookup"><span data-stu-id="f12e5-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f12e5-133">Aborted</span><span class="sxs-lookup"><span data-stu-id="f12e5-133">Aborted</span></span>|<span data-ttu-id="f12e5-134">ワークフロー インスタンスは中止されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f12e5-135">Completed</span><span class="sxs-lookup"><span data-stu-id="f12e5-135">Completed</span></span>|<span data-ttu-id="f12e5-136">ワークフロー インスタンスは完了しました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f12e5-137">Deleted</span><span class="sxs-lookup"><span data-stu-id="f12e5-137">Deleted</span></span>|<span data-ttu-id="f12e5-138">ワークフロー インスタンスは削除されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f12e5-139">Idle</span><span class="sxs-lookup"><span data-stu-id="f12e5-139">Idle</span></span>|<span data-ttu-id="f12e5-140">ワークフロー インスタンスはアイドル状態です。</span><span class="sxs-lookup"><span data-stu-id="f12e5-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f12e5-141">Persisted</span><span class="sxs-lookup"><span data-stu-id="f12e5-141">Persisted</span></span>|<span data-ttu-id="f12e5-142">ワークフロー インスタンスは永続化されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f12e5-143">Resumed</span><span class="sxs-lookup"><span data-stu-id="f12e5-143">Resumed</span></span>|<span data-ttu-id="f12e5-144">ワークフロー インスタンスが再開されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f12e5-145">Started</span><span class="sxs-lookup"><span data-stu-id="f12e5-145">Started</span></span>|<span data-ttu-id="f12e5-146">ワークフロー インスタンスが開始されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f12e5-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="f12e5-147">UnhandledException</span></span>|<span data-ttu-id="f12e5-148">ワークフロー インスタンスで未処理の例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f12e5-149">アンロード</span><span class="sxs-lookup"><span data-stu-id="f12e5-149">Unloaded</span></span>|<span data-ttu-id="f12e5-150">ワークフロー インスタンスはアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f12e5-151">Canceled</span><span class="sxs-lookup"><span data-stu-id="f12e5-151">Canceled</span></span>|<span data-ttu-id="f12e5-152">ワークフロー インスタンスは取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f12e5-153">Suspended</span><span class="sxs-lookup"><span data-stu-id="f12e5-153">Suspended</span></span>|<span data-ttu-id="f12e5-154">ワークフロー インスタンスが中断されています。</span><span class="sxs-lookup"><span data-stu-id="f12e5-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f12e5-155">Terminated</span><span class="sxs-lookup"><span data-stu-id="f12e5-155">Terminated</span></span>|<span data-ttu-id="f12e5-156">ワークフロー インスタンスは終了しました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f12e5-157">Unsuspended</span><span class="sxs-lookup"><span data-stu-id="f12e5-157">Unsuspended</span></span>|<span data-ttu-id="f12e5-158">ワークフロー インスタンスの中断が解除されました。</span><span class="sxs-lookup"><span data-stu-id="f12e5-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f12e5-159">例</span><span class="sxs-lookup"><span data-stu-id="f12e5-159">Example</span></span>  
 <span data-ttu-id="f12e5-160">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="f12e5-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f12e5-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="f12e5-161">See Also</span></span>  
 <span data-ttu-id="f12e5-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f12e5-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f12e5-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f12e5-163"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f12e5-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f12e5-164"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>      
 [<span data-ttu-id="f12e5-165">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="f12e5-165">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f12e5-166">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="f12e5-166">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
