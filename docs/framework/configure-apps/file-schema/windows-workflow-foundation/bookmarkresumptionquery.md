---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 821ded03ced33ee44c6588daefaf9049741abf8c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="3a0b0-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="3a0b0-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="3a0b0-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="3a0b0-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3a0b0-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="3a0b0-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="3a0b0-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3a0b0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3a0b0-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-106">\<system.serviceModel></span></span>  
<span data-ttu-id="3a0b0-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-107">\<tracking></span></span>  
<span data-ttu-id="3a0b0-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-108">\<trackingProfile></span></span>  
<span data-ttu-id="3a0b0-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-109">\<workflow></span></span>  
<span data-ttu-id="3a0b0-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3a0b0-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0b0-112">構文</span><span class="sxs-lookup"><span data-stu-id="3a0b0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a0b0-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3a0b0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3a0b0-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3a0b0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a0b0-115">属性</span><span class="sxs-lookup"><span data-stu-id="3a0b0-115">Attributes</span></span>  
  
|<span data-ttu-id="3a0b0-116">属性</span><span class="sxs-lookup"><span data-stu-id="3a0b0-116">Attribute</span></span>|<span data-ttu-id="3a0b0-117">説明</span><span class="sxs-lookup"><span data-stu-id="3a0b0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a0b0-118">name</span><span class="sxs-lookup"><span data-stu-id="3a0b0-118">name</span></span>|<span data-ttu-id="3a0b0-119">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="3a0b0-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a0b0-120">子要素</span><span class="sxs-lookup"><span data-stu-id="3a0b0-120">Child Elements</span></span>  
 <span data-ttu-id="3a0b0-121">なし。</span><span class="sxs-lookup"><span data-stu-id="3a0b0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a0b0-122">親要素</span><span class="sxs-lookup"><span data-stu-id="3a0b0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3a0b0-123">要素</span><span class="sxs-lookup"><span data-stu-id="3a0b0-123">Element</span></span>|<span data-ttu-id="3a0b0-124">説明</span><span class="sxs-lookup"><span data-stu-id="3a0b0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a0b0-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="3a0b0-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="3a0b0-126">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="3a0b0-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a0b0-127">参照</span><span class="sxs-lookup"><span data-stu-id="3a0b0-127">See Also</span></span>  
 <span data-ttu-id="3a0b0-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3a0b0-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="3a0b0-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3a0b0-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="3a0b0-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="3a0b0-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="3a0b0-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="3a0b0-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
