---
title: '&lt;customTrackingQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d4427ad1b45ceade29b8859d30eba746a70a27d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="58cd4-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="58cd4-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="58cd4-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58cd4-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="58cd4-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58cd4-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="58cd4-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="58cd4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="58cd4-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="58cd4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="58cd4-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="58cd4-107">\<tracking></span></span>  
<span data-ttu-id="58cd4-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="58cd4-108">\<trackingProfile></span></span>  
<span data-ttu-id="58cd4-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="58cd4-109">\<workflow></span></span>  
<span data-ttu-id="58cd4-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="58cd4-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="58cd4-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="58cd4-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58cd4-112">構文</span><span class="sxs-lookup"><span data-stu-id="58cd4-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58cd4-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="58cd4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="58cd4-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="58cd4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58cd4-115">属性</span><span class="sxs-lookup"><span data-stu-id="58cd4-115">Attributes</span></span>  
  
|<span data-ttu-id="58cd4-116">属性</span><span class="sxs-lookup"><span data-stu-id="58cd4-116">Attribute</span></span>|<span data-ttu-id="58cd4-117">説明</span><span class="sxs-lookup"><span data-stu-id="58cd4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58cd4-118">activityName</span><span class="sxs-lookup"><span data-stu-id="58cd4-118">activityName</span></span>|<span data-ttu-id="58cd4-119">追跡レコードを生成したアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="58cd4-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="58cd4-120">name</span><span class="sxs-lookup"><span data-stu-id="58cd4-120">name</span></span>|<span data-ttu-id="58cd4-121">生成されたカスタム追跡レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="58cd4-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58cd4-122">子要素</span><span class="sxs-lookup"><span data-stu-id="58cd4-122">Child Elements</span></span>  
 <span data-ttu-id="58cd4-123">なし。</span><span class="sxs-lookup"><span data-stu-id="58cd4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58cd4-124">親要素</span><span class="sxs-lookup"><span data-stu-id="58cd4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="58cd4-125">要素</span><span class="sxs-lookup"><span data-stu-id="58cd4-125">Element</span></span>|<span data-ttu-id="58cd4-126">説明</span><span class="sxs-lookup"><span data-stu-id="58cd4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58cd4-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="58cd4-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="58cd4-128">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="58cd4-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58cd4-129">参照</span><span class="sxs-lookup"><span data-stu-id="58cd4-129">See Also</span></span>  
 <span data-ttu-id="58cd4-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="58cd4-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="58cd4-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="58cd4-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="58cd4-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="58cd4-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="58cd4-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="58cd4-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
