---
title: "WCF の &lt;trackingProfile&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b651c2-c0d2-4850-a101-b0e009a1dc3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23b419842376383c87fee90263bbd0d6468799c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttrackingprofilegt-of-wcf"></a><span data-ttu-id="d377e-102">WCF の &lt;trackingProfile&gt;</span><span class="sxs-lookup"><span data-stu-id="d377e-102">&lt;trackingProfile&gt; of WCF</span></span>
<span data-ttu-id="d377e-103">ワークフロー追跡参加要素内のレコードを追跡するサブスクリプションを作成するための構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="d377e-103">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="d377e-104">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d377e-104">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d377e-105">追跡プロファイル セクション内で定義されたクエリでは、サブスクリプションによって返されるイベントの種類が定義されます。</span><span class="sxs-lookup"><span data-stu-id="d377e-105">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>  
  
 <span data-ttu-id="d377e-106">ワークフロー追跡とその構成の詳細については、次を参照してください。[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)と[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="d377e-106">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="d377e-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d377e-107">\<system.serviceModel></span></span>  
<span data-ttu-id="d377e-108">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="d377e-108">\<tracking></span></span>  
<span data-ttu-id="d377e-109">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d377e-109">\<trackingProfile></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d377e-110">構文</span><span class="sxs-lookup"><span data-stu-id="d377e-110">Syntax</span></span>  
  
```xml
   <system.serviceModel>  <tracking>      <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>    
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d377e-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d377e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d377e-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d377e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d377e-113">属性</span><span class="sxs-lookup"><span data-stu-id="d377e-113">Attributes</span></span>  
  
|<span data-ttu-id="d377e-114">属性</span><span class="sxs-lookup"><span data-stu-id="d377e-114">Attribute</span></span>|<span data-ttu-id="d377e-115">説明</span><span class="sxs-lookup"><span data-stu-id="d377e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d377e-116">name</span><span class="sxs-lookup"><span data-stu-id="d377e-116">name</span></span>|<span data-ttu-id="d377e-117">追跡プロファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d377e-117">A string that specifies the name of the tracking profile.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d377e-118">子要素</span><span class="sxs-lookup"><span data-stu-id="d377e-118">Child Elements</span></span>  
  
|<span data-ttu-id="d377e-119">要素</span><span class="sxs-lookup"><span data-stu-id="d377e-119">Element</span></span>|<span data-ttu-id="d377e-120">説明</span><span class="sxs-lookup"><span data-stu-id="d377e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d377e-121">\<参加者 ></span><span class="sxs-lookup"><span data-stu-id="d377e-121">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="d377e-122">`a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="d377e-122">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d377e-123">親要素</span><span class="sxs-lookup"><span data-stu-id="d377e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d377e-124">要素</span><span class="sxs-lookup"><span data-stu-id="d377e-124">Element</span></span>|<span data-ttu-id="d377e-125">説明</span><span class="sxs-lookup"><span data-stu-id="d377e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d377e-126">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="d377e-126">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="d377e-127">ワークフロー サービスの追跡設定を定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="d377e-127">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d377e-128">コメント</span><span class="sxs-lookup"><span data-stu-id="d377e-128">Remarks</span></span>  
 <span data-ttu-id="d377e-129">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d377e-129">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="d377e-130">監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、大まかなプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d377e-130">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="d377e-131">それとは反対に、結果として得られるイベントが、後で詳細な実行フローを十分に再構築できるほど豊富な、詳細なプロファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d377e-131">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="d377e-132">追跡プロファイルは、特定の追跡レコードを対象としてワークフロー ランタイムを照会できる、追跡レコード用の宣言型のサブスクリプションとして構築されます。</span><span class="sxs-lookup"><span data-stu-id="d377e-132">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="d377e-133">ハイパーリンク"http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord (VS.100).aspx"TrackingRecord オブジェクトのさまざまなクラスを定期受信できるクエリの型の多数があります。</span><span class="sxs-lookup"><span data-stu-id="d377e-133">There are a handful of query types that allow you subscribe to different classes of  HYPERLINK "http://msdn.microsoft.com/en-us/library/system.activities.tracking.trackingrecord(VS.100).aspx" TrackingRecord objects.</span></span> <span data-ttu-id="d377e-134">クエリの一覧については、次を参照してください[\<参加者 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)と[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).。</span><span class="sxs-lookup"><span data-stu-id="d377e-134">For a complete list of queries, see [\<participants>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md) and [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)..</span></span>  
  
 <span data-ttu-id="d377e-135">次の例では、追跡プロファイルを示しますをサブスクライブする追跡参加要素をできるようにする構成ファイルで、`Started`と`Completed`ワークフロー イベント。</span><span class="sxs-lookup"><span data-stu-id="d377e-135">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>    
    <trackingProfile name="Sample Tracking Profile">  
      <workflow activityDefinitionId="*">  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
            <states>  
              <state name="Started"/>  
              <state name="Completed"/>  
            </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d377e-136">参照</span><span class="sxs-lookup"><span data-stu-id="d377e-136">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="d377e-137">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="d377e-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d377e-138">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="d377e-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
