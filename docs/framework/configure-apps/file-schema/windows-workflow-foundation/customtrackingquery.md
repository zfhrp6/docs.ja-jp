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
ms.openlocfilehash: 908c340167d50d4d16e0eeff7cc2e01290b55e7a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="10b50-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="10b50-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="10b50-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="10b50-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="10b50-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="10b50-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="10b50-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10b50-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="10b50-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="10b50-106">\<system.serviceModel></span></span>  
<span data-ttu-id="10b50-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="10b50-107">\<tracking></span></span>  
<span data-ttu-id="10b50-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="10b50-108">\<trackingProfile></span></span>  
<span data-ttu-id="10b50-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="10b50-109">\<workflow></span></span>  
<span data-ttu-id="10b50-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="10b50-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="10b50-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="10b50-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10b50-112">構文</span><span class="sxs-lookup"><span data-stu-id="10b50-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10b50-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="10b50-113">Attributes and Elements</span></span>  
 <span data-ttu-id="10b50-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="10b50-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10b50-115">属性</span><span class="sxs-lookup"><span data-stu-id="10b50-115">Attributes</span></span>  
  
|<span data-ttu-id="10b50-116">属性</span><span class="sxs-lookup"><span data-stu-id="10b50-116">Attribute</span></span>|<span data-ttu-id="10b50-117">説明</span><span class="sxs-lookup"><span data-stu-id="10b50-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10b50-118">activityName</span><span class="sxs-lookup"><span data-stu-id="10b50-118">activityName</span></span>|<span data-ttu-id="10b50-119">追跡レコードを生成したアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10b50-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="10b50-120">name</span><span class="sxs-lookup"><span data-stu-id="10b50-120">name</span></span>|<span data-ttu-id="10b50-121">生成されたカスタム追跡レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="10b50-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10b50-122">子要素</span><span class="sxs-lookup"><span data-stu-id="10b50-122">Child Elements</span></span>  
 <span data-ttu-id="10b50-123">なし。</span><span class="sxs-lookup"><span data-stu-id="10b50-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10b50-124">親要素</span><span class="sxs-lookup"><span data-stu-id="10b50-124">Parent Elements</span></span>  
  
|<span data-ttu-id="10b50-125">要素</span><span class="sxs-lookup"><span data-stu-id="10b50-125">Element</span></span>|<span data-ttu-id="10b50-126">説明</span><span class="sxs-lookup"><span data-stu-id="10b50-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10b50-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="10b50-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="10b50-128">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="10b50-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10b50-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="10b50-129">See Also</span></span>  
 <span data-ttu-id="10b50-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="10b50-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="10b50-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="10b50-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="10b50-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="10b50-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="10b50-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="10b50-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
