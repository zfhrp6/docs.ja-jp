---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 88f9639e4ecc3105a0e58d92e443d9582f261970
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756187"
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="ffc98-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ffc98-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="ffc98-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="ffc98-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ffc98-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="ffc98-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="ffc98-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ffc98-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ffc98-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ffc98-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ffc98-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="ffc98-107">\<tracking></span></span>  
<span data-ttu-id="ffc98-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ffc98-108">\<trackingProfile></span></span>  
<span data-ttu-id="ffc98-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="ffc98-109">\<workflow></span></span>  
<span data-ttu-id="ffc98-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ffc98-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="ffc98-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="ffc98-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc98-112">構文</span><span class="sxs-lookup"><span data-stu-id="ffc98-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffc98-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ffc98-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ffc98-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffc98-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffc98-115">属性</span><span class="sxs-lookup"><span data-stu-id="ffc98-115">Attributes</span></span>  
  
|<span data-ttu-id="ffc98-116">属性</span><span class="sxs-lookup"><span data-stu-id="ffc98-116">Attribute</span></span>|<span data-ttu-id="ffc98-117">説明</span><span class="sxs-lookup"><span data-stu-id="ffc98-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ffc98-118">name</span><span class="sxs-lookup"><span data-stu-id="ffc98-118">name</span></span>|<span data-ttu-id="ffc98-119">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="ffc98-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffc98-120">子要素</span><span class="sxs-lookup"><span data-stu-id="ffc98-120">Child Elements</span></span>  
 <span data-ttu-id="ffc98-121">なし。</span><span class="sxs-lookup"><span data-stu-id="ffc98-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffc98-122">親要素</span><span class="sxs-lookup"><span data-stu-id="ffc98-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ffc98-123">要素</span><span class="sxs-lookup"><span data-stu-id="ffc98-123">Element</span></span>|<span data-ttu-id="ffc98-124">説明</span><span class="sxs-lookup"><span data-stu-id="ffc98-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ffc98-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="ffc98-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="ffc98-126">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="ffc98-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffc98-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffc98-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="ffc98-128">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="ffc98-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ffc98-129">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="ffc98-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
