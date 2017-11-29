---
title: '&lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e7ed855dc49c4e6639734dcc6a9bc1db7ae53d01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="60216-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="60216-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="60216-103">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="60216-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="60216-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="60216-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="60216-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="60216-105">\<system.serviceModel></span></span>  
<span data-ttu-id="60216-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="60216-106">\<tracking></span></span>  
<span data-ttu-id="60216-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="60216-107">\<trackingProfile></span></span>  
<span data-ttu-id="60216-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="60216-108">\<workflow></span></span>  
<span data-ttu-id="60216-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="60216-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="60216-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="60216-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60216-111">構文</span><span class="sxs-lookup"><span data-stu-id="60216-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60216-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="60216-112">Attributes and Elements</span></span>  
 <span data-ttu-id="60216-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="60216-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60216-114">属性</span><span class="sxs-lookup"><span data-stu-id="60216-114">Attributes</span></span>  
 <span data-ttu-id="60216-115">なし。</span><span class="sxs-lookup"><span data-stu-id="60216-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60216-116">子要素</span><span class="sxs-lookup"><span data-stu-id="60216-116">Child Elements</span></span>  
  
|<span data-ttu-id="60216-117">要素</span><span class="sxs-lookup"><span data-stu-id="60216-117">Element</span></span>|<span data-ttu-id="60216-118">説明</span><span class="sxs-lookup"><span data-stu-id="60216-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60216-119">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="60216-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="60216-120">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクション。</span><span class="sxs-lookup"><span data-stu-id="60216-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60216-121">親要素</span><span class="sxs-lookup"><span data-stu-id="60216-121">Parent Elements</span></span>  
  
|<span data-ttu-id="60216-122">要素</span><span class="sxs-lookup"><span data-stu-id="60216-122">Element</span></span>|<span data-ttu-id="60216-123">説明</span><span class="sxs-lookup"><span data-stu-id="60216-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60216-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="60216-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="60216-125">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="60216-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60216-126">コメント</span><span class="sxs-lookup"><span data-stu-id="60216-126">Remarks</span></span>  
 <span data-ttu-id="60216-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="60216-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="60216-128">例</span><span class="sxs-lookup"><span data-stu-id="60216-128">Example</span></span>  
 <span data-ttu-id="60216-129">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="60216-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="60216-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="60216-130">See Also</span></span>  
 <span data-ttu-id="60216-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="60216-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="60216-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="60216-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="60216-133">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="60216-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="60216-134">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="60216-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
