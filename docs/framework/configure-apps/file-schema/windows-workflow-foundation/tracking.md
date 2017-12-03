---
title: "&lt;追跡&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fd9b50ed-98a1-4518-836d-e4e02c670822
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8147f9d9366d323b551ce2bb8874f6e80fb50b5f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttrackinggt"></a><span data-ttu-id="5237e-102">&lt;追跡&gt;</span><span class="sxs-lookup"><span data-stu-id="5237e-102">&lt;tracking&gt;</span></span>
<span data-ttu-id="5237e-103">ワークフロー サービスの追跡設定を定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="5237e-103">Represents a configuration section for defining tracking settings for a workflow service.</span></span>  
  
 <span data-ttu-id="5237e-104">ワークフロー追跡とその構成の詳細については、次を参照してください。[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)と[ワークフローの追跡を構成する](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)です。</span><span class="sxs-lookup"><span data-stu-id="5237e-104">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
<span data-ttu-id="5237e-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="5237e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5237e-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="5237e-106">\<tracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5237e-107">構文</span><span class="sxs-lookup"><span data-stu-id="5237e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String" 
             profileName="String" 
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String" 
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String" 
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String" 
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String" 
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5237e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5237e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5237e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5237e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5237e-110">属性</span><span class="sxs-lookup"><span data-stu-id="5237e-110">Attributes</span></span>  
 <span data-ttu-id="5237e-111">なし。</span><span class="sxs-lookup"><span data-stu-id="5237e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5237e-112">子要素</span><span class="sxs-lookup"><span data-stu-id="5237e-112">Child Elements</span></span>  
  
|<span data-ttu-id="5237e-113">要素</span><span class="sxs-lookup"><span data-stu-id="5237e-113">Element</span></span>|<span data-ttu-id="5237e-114">説明</span><span class="sxs-lookup"><span data-stu-id="5237e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5237e-115">\<参加者 ></span><span class="sxs-lookup"><span data-stu-id="5237e-115">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="5237e-116">追跡レコードを定期受信の参加要素を定義する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="5237e-116">A collection of configuration elements defining participants that subscribe to tracking records.</span></span> <span data-ttu-id="5237e-117">追跡参加要素には、追跡レコードからペイロードを処理するロジックが含まれています (たとえば、ファイルへの書き込みを選択できるなど)。</span><span class="sxs-lookup"><span data-stu-id="5237e-117">The tracking participants contain the logic to process the payload from the tracking records (for example, they could choose to write to a file).</span></span>|  
|[<span data-ttu-id="5237e-118">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="5237e-118">\<trackingProfile></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|<span data-ttu-id="5237e-119">ワークフロー インスタンスで発生した追跡レコードをフィルター処理するための追跡プロファイル。</span><span class="sxs-lookup"><span data-stu-id="5237e-119">A tracking profile to filter tracking records emitted from a workflow instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5237e-120">親要素</span><span class="sxs-lookup"><span data-stu-id="5237e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5237e-121">要素</span><span class="sxs-lookup"><span data-stu-id="5237e-121">Element</span></span>|<span data-ttu-id="5237e-122">説明</span><span class="sxs-lookup"><span data-stu-id="5237e-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5237e-123">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5237e-123">system.ServiceModel</span></span>|<span data-ttu-id="5237e-124">すべてのワークフロー構成要素のルート要素。</span><span class="sxs-lookup"><span data-stu-id="5237e-124">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5237e-125">コメント</span><span class="sxs-lookup"><span data-stu-id="5237e-125">Remarks</span></span>  
 <span data-ttu-id="5237e-126">追跡には、ワークフローの実行を検証する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="5237e-126">Tracking provides you with the ability to examine the execution of a workflow.</span></span> <span data-ttu-id="5237e-127">ワークフロー追跡インフラストラクチャはワークフローをインストルメント化し、実行中の主要イベントを反映してレコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="5237e-127">The workflow tracking infrastructure instruments a workflow to emit records reflecting key events during the execution.</span></span> <span data-ttu-id="5237e-128">たとえば、ワークフロー インスタンスが開始または完了すると、追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5237e-128">For example, when a workflow instance starts or completes tracking records are emitted.</span></span> <span data-ttu-id="5237e-129">また、追跡によって、ワークフロー変数に関連付けられたビジネス関連データを抽出することもできます。</span><span class="sxs-lookup"><span data-stu-id="5237e-129">Tracking can also extract business relevant data associated with the workflow variables.</span></span> <span data-ttu-id="5237e-130">たとえば、ワークフローが注文処理システムを表している場合は、注文 ID と共に追跡レコードを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="5237e-130">For example, if the workflow represents an order processing system the order id can be extracted along with the tracking record.</span></span> <span data-ttu-id="5237e-131">一般的に、WF 追跡機能を有効にすると、ワークフロー実行の診断またはビジネス分析が容易になります。</span><span class="sxs-lookup"><span data-stu-id="5237e-131">In general, enabling WF tracking facilitates diagnostics or business analytics over a workflow execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5237e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="5237e-132">See Also</span></span>  
 <span data-ttu-id="5237e-133"><xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5237e-133"><xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="5237e-134">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="5237e-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
