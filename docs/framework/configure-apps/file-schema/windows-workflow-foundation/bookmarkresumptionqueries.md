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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bf209525bcc9748e9a5f5b71a0407a4eca1a897
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="57b7d-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="57b7d-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="57b7d-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="57b7d-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="57b7d-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="57b7d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="57b7d-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="57b7d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="57b7d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="57b7d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="57b7d-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="57b7d-107">\<tracking></span></span>  
<span data-ttu-id="57b7d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="57b7d-108">\<trackingProfile></span></span>  
<span data-ttu-id="57b7d-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="57b7d-109">\<workflow></span></span>  
<span data-ttu-id="57b7d-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="57b7d-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="57b7d-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="57b7d-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b7d-112">構文</span><span class="sxs-lookup"><span data-stu-id="57b7d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57b7d-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="57b7d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="57b7d-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="57b7d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57b7d-115">属性</span><span class="sxs-lookup"><span data-stu-id="57b7d-115">Attributes</span></span>  
 <span data-ttu-id="57b7d-116">なし。</span><span class="sxs-lookup"><span data-stu-id="57b7d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57b7d-117">子要素</span><span class="sxs-lookup"><span data-stu-id="57b7d-117">Child Elements</span></span>  
  
|<span data-ttu-id="57b7d-118">要素</span><span class="sxs-lookup"><span data-stu-id="57b7d-118">Element</span></span>|<span data-ttu-id="57b7d-119">説明</span><span class="sxs-lookup"><span data-stu-id="57b7d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57b7d-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="57b7d-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="57b7d-121">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="57b7d-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="57b7d-122">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="57b7d-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57b7d-123">親要素</span><span class="sxs-lookup"><span data-stu-id="57b7d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="57b7d-124">要素</span><span class="sxs-lookup"><span data-stu-id="57b7d-124">Element</span></span>|<span data-ttu-id="57b7d-125">説明</span><span class="sxs-lookup"><span data-stu-id="57b7d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57b7d-126">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="57b7d-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="57b7d-127">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="57b7d-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57b7d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="57b7d-128">See Also</span></span>  
 <span data-ttu-id="57b7d-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="57b7d-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="57b7d-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="57b7d-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="57b7d-131">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="57b7d-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="57b7d-132">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="57b7d-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
