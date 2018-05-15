---
title: '&lt;argument&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: bfcb98085e0b2292d46acfd0a57096219afff606
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltargumentgt"></a><span data-ttu-id="479bf-102">&lt;argument&gt;</span><span class="sxs-lookup"><span data-stu-id="479bf-102">&lt;argument&gt;</span></span>
<span data-ttu-id="479bf-103">アクティビティ状態クエリに関連付けられている引数を表す構成要素。</span><span class="sxs-lookup"><span data-stu-id="479bf-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="479bf-104">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="479bf-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="479bf-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="479bf-105">\<system.serviceModel></span></span>  
<span data-ttu-id="479bf-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="479bf-106">\<tracking></span></span>  
<span data-ttu-id="479bf-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="479bf-107">\<trackingProfile></span></span>  
<span data-ttu-id="479bf-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="479bf-108">\<workflow></span></span>  
<span data-ttu-id="479bf-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="479bf-109">\<activityStateQueries></span></span>  
<span data-ttu-id="479bf-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="479bf-110">\<activityStateQuery></span></span>  
<span data-ttu-id="479bf-111">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="479bf-111">\<arguments></span></span>  
<span data-ttu-id="479bf-112">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="479bf-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="479bf-113">構文</span><span class="sxs-lookup"><span data-stu-id="479bf-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="479bf-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="479bf-114">Attributes and Elements</span></span>  
 <span data-ttu-id="479bf-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="479bf-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="479bf-116">属性</span><span class="sxs-lookup"><span data-stu-id="479bf-116">Attributes</span></span>  
  
|<span data-ttu-id="479bf-117">属性</span><span class="sxs-lookup"><span data-stu-id="479bf-117">Attribute</span></span>|<span data-ttu-id="479bf-118">説明</span><span class="sxs-lookup"><span data-stu-id="479bf-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="479bf-119">name</span><span class="sxs-lookup"><span data-stu-id="479bf-119">name</span></span>|<span data-ttu-id="479bf-120">この引数の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="479bf-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="479bf-121">子要素</span><span class="sxs-lookup"><span data-stu-id="479bf-121">Child Elements</span></span>  
 <span data-ttu-id="479bf-122">なし。</span><span class="sxs-lookup"><span data-stu-id="479bf-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="479bf-123">親要素</span><span class="sxs-lookup"><span data-stu-id="479bf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="479bf-124">要素</span><span class="sxs-lookup"><span data-stu-id="479bf-124">Element</span></span>|<span data-ttu-id="479bf-125">説明</span><span class="sxs-lookup"><span data-stu-id="479bf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="479bf-126">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="479bf-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="479bf-127">このアクティビティ クエリに関連付けられている引数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="479bf-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="479bf-128">コメント</span><span class="sxs-lookup"><span data-stu-id="479bf-128">Remarks</span></span>  
 <span data-ttu-id="479bf-129">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="479bf-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="479bf-130">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="479bf-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="479bf-131">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="479bf-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="479bf-132">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="479bf-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="479bf-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="479bf-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="479bf-134">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="479bf-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="479bf-135">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="479bf-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
