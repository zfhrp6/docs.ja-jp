---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 8f9f30cf16e18eec6f076a41474a1935feeb3460
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="51f7a-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="51f7a-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="51f7a-103">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="51f7a-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="51f7a-104">たとえば、「電子メール送信」アクティビティがワークフロー インスタンス内で完了を毎回の追跡することがあります。</span><span class="sxs-lookup"><span data-stu-id="51f7a-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="51f7a-105">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="51f7a-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="51f7a-106">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="51f7a-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="51f7a-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="51f7a-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="51f7a-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="51f7a-108">\<system.serviceModel></span></span>  
<span data-ttu-id="51f7a-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="51f7a-109">\<tracking></span></span>  
<span data-ttu-id="51f7a-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="51f7a-110">\<trackingProfile></span></span>  
<span data-ttu-id="51f7a-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="51f7a-111">\<workflow></span></span>  
<span data-ttu-id="51f7a-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="51f7a-112">\<activityStateQueries></span></span>  
<span data-ttu-id="51f7a-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="51f7a-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51f7a-114">構文</span><span class="sxs-lookup"><span data-stu-id="51f7a-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51f7a-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="51f7a-115">Attributes and Elements</span></span>  
 <span data-ttu-id="51f7a-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="51f7a-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51f7a-117">属性</span><span class="sxs-lookup"><span data-stu-id="51f7a-117">Attributes</span></span>  
  
|<span data-ttu-id="51f7a-118">属性</span><span class="sxs-lookup"><span data-stu-id="51f7a-118">Attribute</span></span>|<span data-ttu-id="51f7a-119">説明</span><span class="sxs-lookup"><span data-stu-id="51f7a-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51f7a-120">activityName</span><span class="sxs-lookup"><span data-stu-id="51f7a-120">activityName</span></span>|<span data-ttu-id="51f7a-121"><xref:System.Activities.Tracking.ActivityStateRecord> インスタンスをフィルターするために、アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="51f7a-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51f7a-122">子要素</span><span class="sxs-lookup"><span data-stu-id="51f7a-122">Child Elements</span></span>  
  
|<span data-ttu-id="51f7a-123">要素</span><span class="sxs-lookup"><span data-stu-id="51f7a-123">Element</span></span>|<span data-ttu-id="51f7a-124">説明</span><span class="sxs-lookup"><span data-stu-id="51f7a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51f7a-125">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="51f7a-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="51f7a-126">このアクティビティ クエリに関連付けられている引数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="51f7a-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="51f7a-127">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="51f7a-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="51f7a-128">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="51f7a-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="51f7a-129">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="51f7a-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="51f7a-130">このアクティビティ クエリに関連付けられている変数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="51f7a-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="51f7a-131">親要素</span><span class="sxs-lookup"><span data-stu-id="51f7a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="51f7a-132">要素</span><span class="sxs-lookup"><span data-stu-id="51f7a-132">Element</span></span>|<span data-ttu-id="51f7a-133">説明</span><span class="sxs-lookup"><span data-stu-id="51f7a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51f7a-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="51f7a-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="51f7a-135">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="51f7a-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="51f7a-136">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="51f7a-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51f7a-137">コメント</span><span class="sxs-lookup"><span data-stu-id="51f7a-137">Remarks</span></span>  
 <span data-ttu-id="51f7a-138">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="51f7a-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="51f7a-139">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="51f7a-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="51f7a-140">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="51f7a-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="51f7a-141">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="51f7a-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51f7a-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="51f7a-142">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="51f7a-143">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="51f7a-143">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="51f7a-144">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="51f7a-144">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
