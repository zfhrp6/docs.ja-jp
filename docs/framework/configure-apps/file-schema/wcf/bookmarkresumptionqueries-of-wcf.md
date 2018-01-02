---
title: "WCF の &lt;bookmarkResumptionQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c29f4c0cd92b2c4e8263e1893e7deefc2f14624a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="301da-102">WCF の &lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="301da-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="301da-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="301da-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="301da-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="301da-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="301da-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="301da-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="301da-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="301da-106">\<system.serviceModel></span></span>  
<span data-ttu-id="301da-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="301da-107">\<tracking></span></span>  
<span data-ttu-id="301da-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="301da-108">\<trackingProfile></span></span>  
<span data-ttu-id="301da-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="301da-109">\<workflow></span></span>  
<span data-ttu-id="301da-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="301da-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="301da-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="301da-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301da-112">構文</span><span class="sxs-lookup"><span data-stu-id="301da-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="301da-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="301da-113">Attributes and Elements</span></span>  
 <span data-ttu-id="301da-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="301da-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="301da-115">属性</span><span class="sxs-lookup"><span data-stu-id="301da-115">Attributes</span></span>  
 <span data-ttu-id="301da-116">なし。</span><span class="sxs-lookup"><span data-stu-id="301da-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="301da-117">子要素</span><span class="sxs-lookup"><span data-stu-id="301da-117">Child Elements</span></span>  
  
|<span data-ttu-id="301da-118">要素</span><span class="sxs-lookup"><span data-stu-id="301da-118">Element</span></span>|<span data-ttu-id="301da-119">説明</span><span class="sxs-lookup"><span data-stu-id="301da-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="301da-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="301da-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="301da-121">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="301da-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="301da-122">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="301da-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="301da-123">親要素</span><span class="sxs-lookup"><span data-stu-id="301da-123">Parent Elements</span></span>  
  
|<span data-ttu-id="301da-124">要素</span><span class="sxs-lookup"><span data-stu-id="301da-124">Element</span></span>|<span data-ttu-id="301da-125">説明</span><span class="sxs-lookup"><span data-stu-id="301da-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="301da-126">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="301da-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="301da-127">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="301da-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="301da-128">参照</span><span class="sxs-lookup"><span data-stu-id="301da-128">See Also</span></span>  
 <span data-ttu-id="301da-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="301da-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="301da-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="301da-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="301da-131">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="301da-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="301da-132">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="301da-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
