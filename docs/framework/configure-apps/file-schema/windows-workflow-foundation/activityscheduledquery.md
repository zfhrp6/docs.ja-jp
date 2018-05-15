---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0822d0ce7dd82ff396596a0ed2431a5f2084ad8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="779a0-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="779a0-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="779a0-103">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="779a0-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="779a0-104">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="779a0-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="779a0-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="779a0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="779a0-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="779a0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="779a0-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="779a0-107">\<tracking></span></span>  
<span data-ttu-id="779a0-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="779a0-108">\<trackingProfile></span></span>  
<span data-ttu-id="779a0-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="779a0-109">\<workflow></span></span>  
<span data-ttu-id="779a0-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="779a0-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="779a0-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="779a0-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="779a0-112">構文</span><span class="sxs-lookup"><span data-stu-id="779a0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="779a0-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="779a0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="779a0-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="779a0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="779a0-115">属性</span><span class="sxs-lookup"><span data-stu-id="779a0-115">Attributes</span></span>  
  
|<span data-ttu-id="779a0-116">属性</span><span class="sxs-lookup"><span data-stu-id="779a0-116">Attribute</span></span>|<span data-ttu-id="779a0-117">説明</span><span class="sxs-lookup"><span data-stu-id="779a0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="779a0-118">activityName</span><span class="sxs-lookup"><span data-stu-id="779a0-118">activityName</span></span>|<span data-ttu-id="779a0-119">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="779a0-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="779a0-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="779a0-120">childActivityName</span></span>|<span data-ttu-id="779a0-121">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="779a0-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="779a0-122">子要素</span><span class="sxs-lookup"><span data-stu-id="779a0-122">Child Elements</span></span>  
 <span data-ttu-id="779a0-123">なし。</span><span class="sxs-lookup"><span data-stu-id="779a0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="779a0-124">親要素</span><span class="sxs-lookup"><span data-stu-id="779a0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="779a0-125">要素</span><span class="sxs-lookup"><span data-stu-id="779a0-125">Element</span></span>|<span data-ttu-id="779a0-126">説明</span><span class="sxs-lookup"><span data-stu-id="779a0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="779a0-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="779a0-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="779a0-128">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="779a0-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="779a0-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="779a0-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="779a0-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="779a0-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="779a0-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="779a0-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
