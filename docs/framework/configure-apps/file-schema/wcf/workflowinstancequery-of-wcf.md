---
title: "WCF の &lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64b404fec3f3cd46912deede61bf08f8e962f1d7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="907d0-102">WCF の &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="907d0-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="907d0-103">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="907d0-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="907d0-104">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="907d0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="907d0-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="907d0-105">\<system.serviceModel></span></span>  
<span data-ttu-id="907d0-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="907d0-106">\<tracking></span></span>  
<span data-ttu-id="907d0-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="907d0-107">\<trackingProfile></span></span>  
<span data-ttu-id="907d0-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="907d0-108">\<workflow></span></span>  
<span data-ttu-id="907d0-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="907d0-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="907d0-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="907d0-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="907d0-111">構文</span><span class="sxs-lookup"><span data-stu-id="907d0-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="907d0-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="907d0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="907d0-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="907d0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="907d0-114">属性</span><span class="sxs-lookup"><span data-stu-id="907d0-114">Attributes</span></span>  
 <span data-ttu-id="907d0-115">なし。</span><span class="sxs-lookup"><span data-stu-id="907d0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="907d0-116">子要素</span><span class="sxs-lookup"><span data-stu-id="907d0-116">Child Elements</span></span>  
  
|<span data-ttu-id="907d0-117">要素</span><span class="sxs-lookup"><span data-stu-id="907d0-117">Element</span></span>|<span data-ttu-id="907d0-118">説明</span><span class="sxs-lookup"><span data-stu-id="907d0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="907d0-119">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="907d0-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="907d0-120">追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクション。</span><span class="sxs-lookup"><span data-stu-id="907d0-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="907d0-121">親要素</span><span class="sxs-lookup"><span data-stu-id="907d0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="907d0-122">要素</span><span class="sxs-lookup"><span data-stu-id="907d0-122">Element</span></span>|<span data-ttu-id="907d0-123">説明</span><span class="sxs-lookup"><span data-stu-id="907d0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="907d0-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="907d0-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="907d0-125">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="907d0-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="907d0-126">コメント</span><span class="sxs-lookup"><span data-stu-id="907d0-126">Remarks</span></span>  
 <span data-ttu-id="907d0-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> は、次の <xref:System.Activities.Tracking.TrackingRecord> オブジェクトの定期受信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="907d0-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="907d0-128">例</span><span class="sxs-lookup"><span data-stu-id="907d0-128">Example</span></span>  
 <span data-ttu-id="907d0-129">次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="907d0-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="907d0-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="907d0-130">See Also</span></span>  
 <span data-ttu-id="907d0-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="907d0-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="907d0-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="907d0-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="907d0-133">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="907d0-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="907d0-134">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="907d0-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
