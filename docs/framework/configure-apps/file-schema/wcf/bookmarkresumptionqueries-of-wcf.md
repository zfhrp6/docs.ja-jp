---
title: WCF の &lt;bookmarkResumptionQueries&gt;
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 8a83f521e444838b6495221c00211710dd99ab6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753041"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="54911-102">WCF の &lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="54911-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="54911-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="54911-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="54911-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="54911-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="54911-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="54911-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="54911-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="54911-106">\<system.serviceModel></span></span>  
<span data-ttu-id="54911-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="54911-107">\<tracking></span></span>  
<span data-ttu-id="54911-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="54911-108">\<trackingProfile></span></span>  
<span data-ttu-id="54911-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="54911-109">\<workflow></span></span>  
<span data-ttu-id="54911-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="54911-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="54911-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="54911-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54911-112">構文</span><span class="sxs-lookup"><span data-stu-id="54911-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54911-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="54911-113">Attributes and Elements</span></span>  
 <span data-ttu-id="54911-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="54911-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54911-115">属性</span><span class="sxs-lookup"><span data-stu-id="54911-115">Attributes</span></span>  
 <span data-ttu-id="54911-116">なし。</span><span class="sxs-lookup"><span data-stu-id="54911-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54911-117">子要素</span><span class="sxs-lookup"><span data-stu-id="54911-117">Child Elements</span></span>  
  
|<span data-ttu-id="54911-118">要素</span><span class="sxs-lookup"><span data-stu-id="54911-118">Element</span></span>|<span data-ttu-id="54911-119">説明</span><span class="sxs-lookup"><span data-stu-id="54911-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54911-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="54911-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="54911-121">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリ。</span><span class="sxs-lookup"><span data-stu-id="54911-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="54911-122">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="54911-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54911-123">親要素</span><span class="sxs-lookup"><span data-stu-id="54911-123">Parent Elements</span></span>  
  
|<span data-ttu-id="54911-124">要素</span><span class="sxs-lookup"><span data-stu-id="54911-124">Element</span></span>|<span data-ttu-id="54911-125">説明</span><span class="sxs-lookup"><span data-stu-id="54911-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54911-126">\<workflow></span><span class="sxs-lookup"><span data-stu-id="54911-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="54911-127">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="54911-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54911-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="54911-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="54911-129">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="54911-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="54911-130">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="54911-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
