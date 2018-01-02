---
title: "WCF の &lt;workflowInstanceQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecccb2f3b062afd631ef9ba36bc8ac8521db7646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="cbc52-102">WCF の &lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="cbc52-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="cbc52-103">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="cbc52-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="cbc52-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cbc52-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="cbc52-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cbc52-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cbc52-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="cbc52-106">\<tracking></span></span>  
<span data-ttu-id="cbc52-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="cbc52-107">\<trackingProfile></span></span>  
<span data-ttu-id="cbc52-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="cbc52-108">\<workflow></span></span>  
<span data-ttu-id="cbc52-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="cbc52-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc52-110">構文</span><span class="sxs-lookup"><span data-stu-id="cbc52-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbc52-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cbc52-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cbc52-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cbc52-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbc52-113">属性</span><span class="sxs-lookup"><span data-stu-id="cbc52-113">Attributes</span></span>  
 <span data-ttu-id="cbc52-114">なし。</span><span class="sxs-lookup"><span data-stu-id="cbc52-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbc52-115">子要素</span><span class="sxs-lookup"><span data-stu-id="cbc52-115">Child Elements</span></span>  
  
|<span data-ttu-id="cbc52-116">要素</span><span class="sxs-lookup"><span data-stu-id="cbc52-116">Element</span></span>|<span data-ttu-id="cbc52-117">説明</span><span class="sxs-lookup"><span data-stu-id="cbc52-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbc52-118">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="cbc52-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="cbc52-119">ワークフロー インスタンスのライフサイクルの変化を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="cbc52-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbc52-120">親要素</span><span class="sxs-lookup"><span data-stu-id="cbc52-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cbc52-121">要素</span><span class="sxs-lookup"><span data-stu-id="cbc52-121">Element</span></span>|<span data-ttu-id="cbc52-122">説明</span><span class="sxs-lookup"><span data-stu-id="cbc52-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbc52-123">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="cbc52-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="cbc52-124">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx)プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cbc52-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc52-125">コメント</span><span class="sxs-lookup"><span data-stu-id="cbc52-125">Remarks</span></span>  
 <span data-ttu-id="cbc52-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="cbc52-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="cbc52-127">例</span><span class="sxs-lookup"><span data-stu-id="cbc52-127">Example</span></span>  
 <span data-ttu-id="cbc52-128">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="cbc52-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbc52-129">参照</span><span class="sxs-lookup"><span data-stu-id="cbc52-129">See Also</span></span>  
 <span data-ttu-id="cbc52-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cbc52-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="cbc52-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cbc52-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="cbc52-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="cbc52-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="cbc52-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="cbc52-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
