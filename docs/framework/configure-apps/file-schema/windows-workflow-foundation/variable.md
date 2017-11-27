---
title: "&lt;変数&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3db57b3332638092fc9f16de5199b65c4efafebd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltvariablegt"></a><span data-ttu-id="2c099-102">&lt;変数&gt;</span><span class="sxs-lookup"><span data-stu-id="2c099-102">&lt;variable&gt;</span></span>
<span data-ttu-id="2c099-103">このアクティビティ クエリに関連付けられている変数のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2c099-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="2c099-104">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c099-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2c099-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2c099-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2c099-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="2c099-106">\<tracking></span></span>  
<span data-ttu-id="2c099-107">\<プロファイル ></span><span class="sxs-lookup"><span data-stu-id="2c099-107">\<profiles></span></span>  
<span data-ttu-id="2c099-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2c099-108">\<trackingProfile></span></span>  
<span data-ttu-id="2c099-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="2c099-109">\<workflow></span></span>  
<span data-ttu-id="2c099-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="2c099-110">\<activityStateQueries></span></span>  
<span data-ttu-id="2c099-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="2c099-111">\<activityStateQuery></span></span>  
<span data-ttu-id="2c099-112">\<変数 ></span><span class="sxs-lookup"><span data-stu-id="2c099-112">\<variables></span></span>  
<span data-ttu-id="2c099-113">\<変数 ></span><span class="sxs-lookup"><span data-stu-id="2c099-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c099-114">構文</span><span class="sxs-lookup"><span data-stu-id="2c099-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c099-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2c099-115">Attributes and Elements</span></span>  
 <span data-ttu-id="2c099-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c099-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c099-117">属性</span><span class="sxs-lookup"><span data-stu-id="2c099-117">Attributes</span></span>  
  
|<span data-ttu-id="2c099-118">属性</span><span class="sxs-lookup"><span data-stu-id="2c099-118">Attribute</span></span>|<span data-ttu-id="2c099-119">説明</span><span class="sxs-lookup"><span data-stu-id="2c099-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c099-120">name</span><span class="sxs-lookup"><span data-stu-id="2c099-120">name</span></span>|<span data-ttu-id="2c099-121">変数の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2c099-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c099-122">子要素</span><span class="sxs-lookup"><span data-stu-id="2c099-122">Child Elements</span></span>  
 <span data-ttu-id="2c099-123">なし。</span><span class="sxs-lookup"><span data-stu-id="2c099-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c099-124">親要素</span><span class="sxs-lookup"><span data-stu-id="2c099-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2c099-125">要素</span><span class="sxs-lookup"><span data-stu-id="2c099-125">Element</span></span>|<span data-ttu-id="2c099-126">説明</span><span class="sxs-lookup"><span data-stu-id="2c099-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c099-127">\<変数 ></span><span class="sxs-lookup"><span data-stu-id="2c099-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="2c099-128">アクティビティ状態クエリに関連付けられている変数。</span><span class="sxs-lookup"><span data-stu-id="2c099-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c099-129">コメント</span><span class="sxs-lookup"><span data-stu-id="2c099-129">Remarks</span></span>  
 <span data-ttu-id="2c099-130">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="2c099-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="2c099-131">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c099-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="2c099-132">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="2c099-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="2c099-133">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="2c099-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c099-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c099-134">See Also</span></span>  
 <span data-ttu-id="2c099-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2c099-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="2c099-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="2c099-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="2c099-137">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="2c099-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2c099-138">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="2c099-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
