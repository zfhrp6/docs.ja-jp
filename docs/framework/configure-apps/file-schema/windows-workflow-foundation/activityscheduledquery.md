---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51db0762c10459d67929867a0fe44908dc7ec750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="e01b5-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e01b5-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="e01b5-103">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="e01b5-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e01b5-104">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="e01b5-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e01b5-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e01b5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e01b5-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e01b5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e01b5-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="e01b5-107">\<tracking></span></span>  
<span data-ttu-id="e01b5-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e01b5-108">\<trackingProfile></span></span>  
<span data-ttu-id="e01b5-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="e01b5-109">\<workflow></span></span>  
<span data-ttu-id="e01b5-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="e01b5-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="e01b5-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="e01b5-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e01b5-112">構文</span><span class="sxs-lookup"><span data-stu-id="e01b5-112">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e01b5-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e01b5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e01b5-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e01b5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e01b5-115">属性</span><span class="sxs-lookup"><span data-stu-id="e01b5-115">Attributes</span></span>  
  
|<span data-ttu-id="e01b5-116">属性</span><span class="sxs-lookup"><span data-stu-id="e01b5-116">Attribute</span></span>|<span data-ttu-id="e01b5-117">説明</span><span class="sxs-lookup"><span data-stu-id="e01b5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e01b5-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e01b5-118">activityName</span></span>|<span data-ttu-id="e01b5-119">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e01b5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e01b5-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e01b5-120">childActivityName</span></span>|<span data-ttu-id="e01b5-121">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e01b5-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e01b5-122">子要素</span><span class="sxs-lookup"><span data-stu-id="e01b5-122">Child Elements</span></span>  
 <span data-ttu-id="e01b5-123">なし。</span><span class="sxs-lookup"><span data-stu-id="e01b5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e01b5-124">親要素</span><span class="sxs-lookup"><span data-stu-id="e01b5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e01b5-125">要素</span><span class="sxs-lookup"><span data-stu-id="e01b5-125">Element</span></span>|<span data-ttu-id="e01b5-126">説明</span><span class="sxs-lookup"><span data-stu-id="e01b5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e01b5-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="e01b5-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="e01b5-128">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="e01b5-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e01b5-129">参照</span><span class="sxs-lookup"><span data-stu-id="e01b5-129">See Also</span></span>  
 <span data-ttu-id="e01b5-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e01b5-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e01b5-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e01b5-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e01b5-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="e01b5-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e01b5-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="e01b5-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
