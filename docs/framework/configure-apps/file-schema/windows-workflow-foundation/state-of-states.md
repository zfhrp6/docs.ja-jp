---
title: "&lt;states&gt; の &lt;state&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13ae0e8cc59adec0b4e4bd9f2cf4c7ea31811602
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="766db-102">&lt;states&gt; の &lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="766db-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="766db-103">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素。</span><span class="sxs-lookup"><span data-stu-id="766db-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="766db-104">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="766db-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="766db-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="766db-105">\<system.serviceModel></span></span>  
<span data-ttu-id="766db-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="766db-106">\<tracking></span></span>  
<span data-ttu-id="766db-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="766db-107">\<trackingProfile></span></span>  
<span data-ttu-id="766db-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="766db-108">\<workflow></span></span>  
<span data-ttu-id="766db-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="766db-109">\<activityStateQueries></span></span>  
<span data-ttu-id="766db-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="766db-110">\<activityStateQuery></span></span>  
<span data-ttu-id="766db-111">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="766db-111">\<states></span></span>  
<span data-ttu-id="766db-112">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="766db-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="766db-113">構文</span><span class="sxs-lookup"><span data-stu-id="766db-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="766db-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="766db-114">Attributes and Elements</span></span>  
 <span data-ttu-id="766db-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="766db-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="766db-116">属性</span><span class="sxs-lookup"><span data-stu-id="766db-116">Attributes</span></span>  
  
|<span data-ttu-id="766db-117">属性</span><span class="sxs-lookup"><span data-stu-id="766db-117">Attribute</span></span>|<span data-ttu-id="766db-118">説明</span><span class="sxs-lookup"><span data-stu-id="766db-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="766db-119">name</span><span class="sxs-lookup"><span data-stu-id="766db-119">name</span></span>|<span data-ttu-id="766db-120">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="766db-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="766db-121">子要素</span><span class="sxs-lookup"><span data-stu-id="766db-121">Child Elements</span></span>  
 <span data-ttu-id="766db-122">なし。</span><span class="sxs-lookup"><span data-stu-id="766db-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="766db-123">親要素</span><span class="sxs-lookup"><span data-stu-id="766db-123">Parent Elements</span></span>  
  
|<span data-ttu-id="766db-124">要素</span><span class="sxs-lookup"><span data-stu-id="766db-124">Element</span></span>|<span data-ttu-id="766db-125">説明</span><span class="sxs-lookup"><span data-stu-id="766db-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="766db-126">\<状態 ></span><span class="sxs-lookup"><span data-stu-id="766db-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="766db-127">追跡レコードを生成する必要がある定期受信済みアクティビティの状態を含む構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="766db-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="766db-128">コメント</span><span class="sxs-lookup"><span data-stu-id="766db-128">Remarks</span></span>  
 <span data-ttu-id="766db-129">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="766db-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="766db-130">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="766db-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="766db-131">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="766db-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="766db-132">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="766db-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="766db-133">参照</span><span class="sxs-lookup"><span data-stu-id="766db-133">See Also</span></span>  
 <span data-ttu-id="766db-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="766db-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="766db-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="766db-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="766db-136">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="766db-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="766db-137">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="766db-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
