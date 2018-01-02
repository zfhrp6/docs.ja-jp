---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="083a6-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="083a6-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="083a6-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="083a6-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="083a6-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="083a6-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="083a6-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="083a6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="083a6-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="083a6-106">\<system.serviceModel></span></span>  
<span data-ttu-id="083a6-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="083a6-107">\<tracking></span></span>  
<span data-ttu-id="083a6-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="083a6-108">\<trackingProfile></span></span>  
<span data-ttu-id="083a6-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="083a6-109">\<workflow></span></span>  
<span data-ttu-id="083a6-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="083a6-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="083a6-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="083a6-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083a6-112">構文</span><span class="sxs-lookup"><span data-stu-id="083a6-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="083a6-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="083a6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="083a6-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="083a6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="083a6-115">属性</span><span class="sxs-lookup"><span data-stu-id="083a6-115">Attributes</span></span>  
 <span data-ttu-id="083a6-116">なし。</span><span class="sxs-lookup"><span data-stu-id="083a6-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="083a6-117">子要素</span><span class="sxs-lookup"><span data-stu-id="083a6-117">Child Elements</span></span>  
  
|<span data-ttu-id="083a6-118">要素</span><span class="sxs-lookup"><span data-stu-id="083a6-118">Element</span></span>|<span data-ttu-id="083a6-119">説明</span><span class="sxs-lookup"><span data-stu-id="083a6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="083a6-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="083a6-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="083a6-121">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="083a6-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="083a6-122">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="083a6-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="083a6-123">親要素</span><span class="sxs-lookup"><span data-stu-id="083a6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="083a6-124">要素</span><span class="sxs-lookup"><span data-stu-id="083a6-124">Element</span></span>|<span data-ttu-id="083a6-125">説明</span><span class="sxs-lookup"><span data-stu-id="083a6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="083a6-126">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="083a6-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="083a6-127">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="083a6-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="083a6-128">参照</span><span class="sxs-lookup"><span data-stu-id="083a6-128">See Also</span></span>  
 <span data-ttu-id="083a6-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="083a6-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="083a6-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="083a6-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="083a6-131">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="083a6-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="083a6-132">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="083a6-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
