---
title: "WCF の &lt;activityStateQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de042732e7957fa6ea8c22d03ff6892ee1e912f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="d36d8-102">WCF の &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="d36d8-102">&lt;activityStateQuery&gt; of WCF</span></span>
<span data-ttu-id="d36d8-103">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="d36d8-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d36d8-104">たとえば、「電子メール送信」アクティビティがワークフロー インスタンス内で完了を毎回の追跡することがあります。</span><span class="sxs-lookup"><span data-stu-id="d36d8-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d36d8-105">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="d36d8-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="d36d8-106">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="d36d8-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="d36d8-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="d36d8-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="d36d8-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d36d8-108">\<system.serviceModel></span></span>  
<span data-ttu-id="d36d8-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="d36d8-109">\<tracking></span></span>  
<span data-ttu-id="d36d8-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d36d8-110">\<trackingProfile></span></span>  
<span data-ttu-id="d36d8-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="d36d8-111">\<workflow></span></span>  
<span data-ttu-id="d36d8-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="d36d8-112">\<activityStateQueries></span></span>  
<span data-ttu-id="d36d8-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d36d8-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d36d8-114">構文</span><span class="sxs-lookup"><span data-stu-id="d36d8-114">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d36d8-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d36d8-115">Attributes and Elements</span></span>  
 <span data-ttu-id="d36d8-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d36d8-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d36d8-117">属性</span><span class="sxs-lookup"><span data-stu-id="d36d8-117">Attributes</span></span>  
  
|<span data-ttu-id="d36d8-118">属性</span><span class="sxs-lookup"><span data-stu-id="d36d8-118">Attribute</span></span>|<span data-ttu-id="d36d8-119">説明</span><span class="sxs-lookup"><span data-stu-id="d36d8-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d36d8-120">activityName</span><span class="sxs-lookup"><span data-stu-id="d36d8-120">activityName</span></span>|<span data-ttu-id="d36d8-121"><xref:System.Activities.Tracking.ActivityStateRecord> インスタンスをフィルターするために、アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d36d8-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d36d8-122">子要素</span><span class="sxs-lookup"><span data-stu-id="d36d8-122">Child Elements</span></span>  
  
|<span data-ttu-id="d36d8-123">要素</span><span class="sxs-lookup"><span data-stu-id="d36d8-123">Element</span></span>|<span data-ttu-id="d36d8-124">説明</span><span class="sxs-lookup"><span data-stu-id="d36d8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d36d8-125">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="d36d8-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="d36d8-126">このアクティビティ クエリに関連付けられている引数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d36d8-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="d36d8-127">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="d36d8-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="d36d8-128">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d36d8-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="d36d8-129">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="d36d8-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="d36d8-130">このアクティビティ クエリに関連付けられている変数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d36d8-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d36d8-131">親要素</span><span class="sxs-lookup"><span data-stu-id="d36d8-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d36d8-132">要素</span><span class="sxs-lookup"><span data-stu-id="d36d8-132">Element</span></span>|<span data-ttu-id="d36d8-133">説明</span><span class="sxs-lookup"><span data-stu-id="d36d8-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d36d8-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="d36d8-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="d36d8-135">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="d36d8-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="d36d8-136">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="d36d8-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d36d8-137">コメント</span><span class="sxs-lookup"><span data-stu-id="d36d8-137">Remarks</span></span>  
 <span data-ttu-id="d36d8-138">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="d36d8-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d36d8-139">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="d36d8-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d36d8-140">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="d36d8-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d36d8-141">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="d36d8-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d36d8-142">参照</span><span class="sxs-lookup"><span data-stu-id="d36d8-142">See Also</span></span>  
 <span data-ttu-id="d36d8-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span><span class="sxs-lookup"><span data-stu-id="d36d8-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span></span>    
 <span data-ttu-id="d36d8-144"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="d36d8-144"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>     
 [<span data-ttu-id="d36d8-145">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="d36d8-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d36d8-146">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="d36d8-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
