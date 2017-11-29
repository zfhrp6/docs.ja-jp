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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779ac3995d4d5fb1b63de6ae6b9db7103691d6f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="6893d-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="6893d-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="6893d-103">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="6893d-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="6893d-104">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="6893d-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="6893d-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6893d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6893d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6893d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6893d-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="6893d-107">\<tracking></span></span>  
<span data-ttu-id="6893d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6893d-108">\<trackingProfile></span></span>  
<span data-ttu-id="6893d-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="6893d-109">\<workflow></span></span>  
<span data-ttu-id="6893d-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="6893d-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="6893d-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="6893d-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6893d-112">構文</span><span class="sxs-lookup"><span data-stu-id="6893d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6893d-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6893d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6893d-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6893d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6893d-115">属性</span><span class="sxs-lookup"><span data-stu-id="6893d-115">Attributes</span></span>  
  
|<span data-ttu-id="6893d-116">属性</span><span class="sxs-lookup"><span data-stu-id="6893d-116">Attribute</span></span>|<span data-ttu-id="6893d-117">説明</span><span class="sxs-lookup"><span data-stu-id="6893d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6893d-118">activityName</span><span class="sxs-lookup"><span data-stu-id="6893d-118">activityName</span></span>|<span data-ttu-id="6893d-119">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="6893d-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="6893d-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="6893d-120">childActivityName</span></span>|<span data-ttu-id="6893d-121">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="6893d-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6893d-122">子要素</span><span class="sxs-lookup"><span data-stu-id="6893d-122">Child Elements</span></span>  
 <span data-ttu-id="6893d-123">なし。</span><span class="sxs-lookup"><span data-stu-id="6893d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6893d-124">親要素</span><span class="sxs-lookup"><span data-stu-id="6893d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6893d-125">要素</span><span class="sxs-lookup"><span data-stu-id="6893d-125">Element</span></span>|<span data-ttu-id="6893d-126">説明</span><span class="sxs-lookup"><span data-stu-id="6893d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6893d-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="6893d-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="6893d-128">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="6893d-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6893d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="6893d-129">See Also</span></span>  
 <span data-ttu-id="6893d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6893d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="6893d-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6893d-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="6893d-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="6893d-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6893d-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="6893d-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
