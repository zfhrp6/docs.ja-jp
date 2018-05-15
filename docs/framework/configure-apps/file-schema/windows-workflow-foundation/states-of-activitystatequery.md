---
title: '&lt;activityStateQuery&gt; の &lt;states&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: d26687e9d0f2bee672f6b0c6c38b87fadf6e7888
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltstatesgt-of-ltactivitystatequerygt"></a><span data-ttu-id="5f789-102">&lt;activityStateQuery&gt; の &lt;states&gt;</span><span class="sxs-lookup"><span data-stu-id="5f789-102">&lt;states&gt; of &lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="5f789-103">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="5f789-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="5f789-104">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f789-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5f789-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5f789-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5f789-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="5f789-106">\<tracking></span></span>  
<span data-ttu-id="5f789-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5f789-107">\<trackingProfile></span></span>  
<span data-ttu-id="5f789-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="5f789-108">\<workflow></span></span>  
<span data-ttu-id="5f789-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="5f789-109">\<activityStateQueries></span></span>  
<span data-ttu-id="5f789-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="5f789-110">\<activityStateQuery></span></span>  
<span data-ttu-id="5f789-111">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="5f789-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f789-112">構文</span><span class="sxs-lookup"><span data-stu-id="5f789-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f789-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5f789-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5f789-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f789-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f789-115">属性</span><span class="sxs-lookup"><span data-stu-id="5f789-115">Attributes</span></span>  
 <span data-ttu-id="5f789-116">なし。</span><span class="sxs-lookup"><span data-stu-id="5f789-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f789-117">子要素</span><span class="sxs-lookup"><span data-stu-id="5f789-117">Child Elements</span></span>  
  
|<span data-ttu-id="5f789-118">要素</span><span class="sxs-lookup"><span data-stu-id="5f789-118">Element</span></span>|<span data-ttu-id="5f789-119">説明</span><span class="sxs-lookup"><span data-stu-id="5f789-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f789-120">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="5f789-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="5f789-121">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素。</span><span class="sxs-lookup"><span data-stu-id="5f789-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f789-122">親要素</span><span class="sxs-lookup"><span data-stu-id="5f789-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5f789-123">要素</span><span class="sxs-lookup"><span data-stu-id="5f789-123">Element</span></span>|<span data-ttu-id="5f789-124">説明</span><span class="sxs-lookup"><span data-stu-id="5f789-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f789-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="5f789-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="5f789-126">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="5f789-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="5f789-127">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="5f789-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f789-128">コメント</span><span class="sxs-lookup"><span data-stu-id="5f789-128">Remarks</span></span>  
 <span data-ttu-id="5f789-129">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="5f789-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5f789-130">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="5f789-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5f789-131">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5f789-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5f789-132">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f789-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f789-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f789-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>      
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="5f789-134">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="5f789-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5f789-135">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="5f789-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
