---
title: "&lt;引数&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61e93aa956aee16469fa0d276e749d08049e1cd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltargumentgt"></a><span data-ttu-id="13c9b-102">&lt;引数&gt;</span><span class="sxs-lookup"><span data-stu-id="13c9b-102">&lt;argument&gt;</span></span>
<span data-ttu-id="13c9b-103">アクティビティ状態クエリに関連付けられている引数を表す構成要素。</span><span class="sxs-lookup"><span data-stu-id="13c9b-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="13c9b-104">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="13c9b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="13c9b-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="13c9b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="13c9b-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="13c9b-106">\<tracking></span></span>  
<span data-ttu-id="13c9b-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="13c9b-107">\<trackingProfile></span></span>  
<span data-ttu-id="13c9b-108">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="13c9b-108">\<workflow></span></span>  
<span data-ttu-id="13c9b-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="13c9b-109">\<activityStateQueries></span></span>  
<span data-ttu-id="13c9b-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="13c9b-110">\<activityStateQuery></span></span>  
<span data-ttu-id="13c9b-111">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="13c9b-111">\<arguments></span></span>  
<span data-ttu-id="13c9b-112">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="13c9b-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c9b-113">構文</span><span class="sxs-lookup"><span data-stu-id="13c9b-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13c9b-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="13c9b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="13c9b-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="13c9b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13c9b-116">属性</span><span class="sxs-lookup"><span data-stu-id="13c9b-116">Attributes</span></span>  
  
|<span data-ttu-id="13c9b-117">属性</span><span class="sxs-lookup"><span data-stu-id="13c9b-117">Attribute</span></span>|<span data-ttu-id="13c9b-118">説明</span><span class="sxs-lookup"><span data-stu-id="13c9b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13c9b-119">name</span><span class="sxs-lookup"><span data-stu-id="13c9b-119">name</span></span>|<span data-ttu-id="13c9b-120">この引数の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="13c9b-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13c9b-121">子要素</span><span class="sxs-lookup"><span data-stu-id="13c9b-121">Child Elements</span></span>  
 <span data-ttu-id="13c9b-122">なし。</span><span class="sxs-lookup"><span data-stu-id="13c9b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13c9b-123">親要素</span><span class="sxs-lookup"><span data-stu-id="13c9b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="13c9b-124">要素</span><span class="sxs-lookup"><span data-stu-id="13c9b-124">Element</span></span>|<span data-ttu-id="13c9b-125">説明</span><span class="sxs-lookup"><span data-stu-id="13c9b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13c9b-126">\<引数 ></span><span class="sxs-lookup"><span data-stu-id="13c9b-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="13c9b-127">このアクティビティ クエリに関連付けられている引数のコレクション。</span><span class="sxs-lookup"><span data-stu-id="13c9b-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13c9b-128">コメント</span><span class="sxs-lookup"><span data-stu-id="13c9b-128">Remarks</span></span>  
 <span data-ttu-id="13c9b-129">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="13c9b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="13c9b-130">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="13c9b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="13c9b-131">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="13c9b-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="13c9b-132">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="13c9b-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13c9b-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="13c9b-133">See Also</span></span>  
 <span data-ttu-id="13c9b-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="13c9b-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="13c9b-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="13c9b-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="13c9b-136">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="13c9b-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="13c9b-137">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="13c9b-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
