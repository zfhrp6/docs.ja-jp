---
title: '&lt;variable&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 7d41d80bfe83cfafca01509d50709e21730bcb97
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltvariablegt"></a><span data-ttu-id="2f011-102">&lt;variable&gt;</span><span class="sxs-lookup"><span data-stu-id="2f011-102">&lt;variable&gt;</span></span>
<span data-ttu-id="2f011-103">このアクティビティ クエリに関連付けられている変数のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="2f011-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="2f011-104">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f011-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="2f011-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2f011-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2f011-106">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="2f011-106">\<tracking></span></span>  
<span data-ttu-id="2f011-107">\<プロファイル ></span><span class="sxs-lookup"><span data-stu-id="2f011-107">\<profiles></span></span>  
<span data-ttu-id="2f011-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2f011-108">\<trackingProfile></span></span>  
<span data-ttu-id="2f011-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="2f011-109">\<workflow></span></span>  
<span data-ttu-id="2f011-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="2f011-110">\<activityStateQueries></span></span>  
<span data-ttu-id="2f011-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="2f011-111">\<activityStateQuery></span></span>  
<span data-ttu-id="2f011-112">\<変数 ></span><span class="sxs-lookup"><span data-stu-id="2f011-112">\<variables></span></span>  
<span data-ttu-id="2f011-113">\<変数 ></span><span class="sxs-lookup"><span data-stu-id="2f011-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f011-114">構文</span><span class="sxs-lookup"><span data-stu-id="2f011-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f011-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2f011-115">Attributes and Elements</span></span>  
 <span data-ttu-id="2f011-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f011-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f011-117">属性</span><span class="sxs-lookup"><span data-stu-id="2f011-117">Attributes</span></span>  
  
|<span data-ttu-id="2f011-118">属性</span><span class="sxs-lookup"><span data-stu-id="2f011-118">Attribute</span></span>|<span data-ttu-id="2f011-119">説明</span><span class="sxs-lookup"><span data-stu-id="2f011-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f011-120">name</span><span class="sxs-lookup"><span data-stu-id="2f011-120">name</span></span>|<span data-ttu-id="2f011-121">変数の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2f011-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f011-122">子要素</span><span class="sxs-lookup"><span data-stu-id="2f011-122">Child Elements</span></span>  
 <span data-ttu-id="2f011-123">なし。</span><span class="sxs-lookup"><span data-stu-id="2f011-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f011-124">親要素</span><span class="sxs-lookup"><span data-stu-id="2f011-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2f011-125">要素</span><span class="sxs-lookup"><span data-stu-id="2f011-125">Element</span></span>|<span data-ttu-id="2f011-126">説明</span><span class="sxs-lookup"><span data-stu-id="2f011-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f011-127">\<変数 ></span><span class="sxs-lookup"><span data-stu-id="2f011-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="2f011-128">アクティビティ状態クエリに関連付けられている変数。</span><span class="sxs-lookup"><span data-stu-id="2f011-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f011-129">コメント</span><span class="sxs-lookup"><span data-stu-id="2f011-129">Remarks</span></span>  
 <span data-ttu-id="2f011-130">ActivityStateQuery の固有の機能の 1 つは、ワークフローの実行を追跡するときにデータを抽出する機能です。</span><span class="sxs-lookup"><span data-stu-id="2f011-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="2f011-131">これにより、実行後に追跡レコードにアクセスするときにコンテキストが追加されます。</span><span class="sxs-lookup"><span data-stu-id="2f011-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="2f011-132">使用することができます、 [\<引数 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)、 [\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)と[\<状態 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)な変数や引数を抽出する要素ワークフロー内のすべての活動から次の例は、変数と引数を抽出するアクティビティ状態クエリを示しています。 ときに、アクティビティの`Closed`追跡レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="2f011-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="2f011-133">ActivityStateRecord でのみ抽出できるし、したがってサブスクライブしている追跡内で変数と引数を使用してプロファイル[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f011-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f011-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f011-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="2f011-135">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="2f011-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2f011-136">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="2f011-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
