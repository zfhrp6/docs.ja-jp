---
title: '&lt;workflowInstanceQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: a165d6f55afbbf1489a7355d4207a74ac1f003ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755592"
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="c291b-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c291b-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="c291b-103">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="c291b-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="c291b-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c291b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c291b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c291b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c291b-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="c291b-106">\<tracking></span></span>  
<span data-ttu-id="c291b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c291b-107">\<trackingProfile></span></span>  
<span data-ttu-id="c291b-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="c291b-108">\<workflow></span></span>  
<span data-ttu-id="c291b-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="c291b-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c291b-110">構文</span><span class="sxs-lookup"><span data-stu-id="c291b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c291b-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c291b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c291b-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c291b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c291b-113">属性</span><span class="sxs-lookup"><span data-stu-id="c291b-113">Attributes</span></span>  
 <span data-ttu-id="c291b-114">なし。</span><span class="sxs-lookup"><span data-stu-id="c291b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c291b-115">子要素</span><span class="sxs-lookup"><span data-stu-id="c291b-115">Child Elements</span></span>  
  
|<span data-ttu-id="c291b-116">要素</span><span class="sxs-lookup"><span data-stu-id="c291b-116">Element</span></span>|<span data-ttu-id="c291b-117">説明</span><span class="sxs-lookup"><span data-stu-id="c291b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c291b-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="c291b-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="c291b-119">ワークフロー インスタンスのライフサイクルの変化を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="c291b-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c291b-120">親要素</span><span class="sxs-lookup"><span data-stu-id="c291b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c291b-121">要素</span><span class="sxs-lookup"><span data-stu-id="c291b-121">Element</span></span>|<span data-ttu-id="c291b-122">説明</span><span class="sxs-lookup"><span data-stu-id="c291b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c291b-123">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c291b-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c291b-124">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c291b-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c291b-125">コメント</span><span class="sxs-lookup"><span data-stu-id="c291b-125">Remarks</span></span>  
 <span data-ttu-id="c291b-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c291b-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="c291b-127">例</span><span class="sxs-lookup"><span data-stu-id="c291b-127">Example</span></span>  
 <span data-ttu-id="c291b-128">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="c291b-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c291b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c291b-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="c291b-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="c291b-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c291b-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="c291b-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
