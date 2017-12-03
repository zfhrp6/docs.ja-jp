---
title: '&lt;customTrackingQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 241684a3a2344d6eb7f3b34c81c581b0ec5130f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="24892-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="24892-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="24892-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="24892-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="24892-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="24892-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="24892-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="24892-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="24892-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="24892-106">\<system.serviceModel></span></span>  
<span data-ttu-id="24892-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="24892-107">\<tracking></span></span>  
<span data-ttu-id="24892-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="24892-108">\<trackingProfile></span></span>  
<span data-ttu-id="24892-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="24892-109">\<workflow></span></span>  
<span data-ttu-id="24892-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="24892-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24892-111">構文</span><span class="sxs-lookup"><span data-stu-id="24892-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24892-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="24892-112">Attributes and Elements</span></span>  
 <span data-ttu-id="24892-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="24892-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24892-114">属性</span><span class="sxs-lookup"><span data-stu-id="24892-114">Attributes</span></span>  
 <span data-ttu-id="24892-115">なし。</span><span class="sxs-lookup"><span data-stu-id="24892-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24892-116">子要素</span><span class="sxs-lookup"><span data-stu-id="24892-116">Child Elements</span></span>  
  
|<span data-ttu-id="24892-117">要素</span><span class="sxs-lookup"><span data-stu-id="24892-117">Element</span></span>|<span data-ttu-id="24892-118">説明</span><span class="sxs-lookup"><span data-stu-id="24892-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24892-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="24892-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="24892-120">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="24892-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24892-121">親要素</span><span class="sxs-lookup"><span data-stu-id="24892-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24892-122">要素</span><span class="sxs-lookup"><span data-stu-id="24892-122">Element</span></span>|<span data-ttu-id="24892-123">説明</span><span class="sxs-lookup"><span data-stu-id="24892-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24892-124">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="24892-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="24892-125">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="24892-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="24892-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="24892-126">See Also</span></span>  
 <span data-ttu-id="24892-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="24892-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="24892-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="24892-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="24892-129">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="24892-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="24892-130">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="24892-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
