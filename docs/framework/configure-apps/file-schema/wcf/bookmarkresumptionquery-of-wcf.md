---
title: "WCF の &lt;bookmarkResumptionQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b3cccb31b3b9433f6eab09aa380af92b210649b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="8eff9-102">WCF の &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="8eff9-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="8eff9-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="8eff9-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="8eff9-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="8eff9-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="8eff9-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8eff9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8eff9-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8eff9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8eff9-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="8eff9-107">\<tracking></span></span>  
<span data-ttu-id="8eff9-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8eff9-108">\<trackingProfile></span></span>  
<span data-ttu-id="8eff9-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="8eff9-109">\<workflow></span></span>  
<span data-ttu-id="8eff9-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="8eff9-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="8eff9-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="8eff9-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eff9-112">構文</span><span class="sxs-lookup"><span data-stu-id="8eff9-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8eff9-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8eff9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8eff9-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8eff9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eff9-115">属性</span><span class="sxs-lookup"><span data-stu-id="8eff9-115">Attributes</span></span>  
  
|<span data-ttu-id="8eff9-116">属性</span><span class="sxs-lookup"><span data-stu-id="8eff9-116">Attribute</span></span>|<span data-ttu-id="8eff9-117">説明</span><span class="sxs-lookup"><span data-stu-id="8eff9-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8eff9-118">name</span><span class="sxs-lookup"><span data-stu-id="8eff9-118">name</span></span>|<span data-ttu-id="8eff9-119">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="8eff9-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8eff9-120">子要素</span><span class="sxs-lookup"><span data-stu-id="8eff9-120">Child Elements</span></span>  
 <span data-ttu-id="8eff9-121">なし。</span><span class="sxs-lookup"><span data-stu-id="8eff9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8eff9-122">親要素</span><span class="sxs-lookup"><span data-stu-id="8eff9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8eff9-123">要素</span><span class="sxs-lookup"><span data-stu-id="8eff9-123">Element</span></span>|<span data-ttu-id="8eff9-124">説明</span><span class="sxs-lookup"><span data-stu-id="8eff9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eff9-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="8eff9-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="8eff9-126">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="8eff9-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8eff9-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8eff9-127">See Also</span></span>  
 <span data-ttu-id="8eff9-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8eff9-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8eff9-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8eff9-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8eff9-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="8eff9-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8eff9-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="8eff9-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
