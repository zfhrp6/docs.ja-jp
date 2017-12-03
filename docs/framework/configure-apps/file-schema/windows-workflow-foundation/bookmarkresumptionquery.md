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
ms.openlocfilehash: bafb044d052692385e0be0f4dbb1271eca847b1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="ee641-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ee641-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="ee641-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="ee641-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="ee641-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="ee641-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="ee641-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ee641-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ee641-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ee641-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ee641-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="ee641-107">\<tracking></span></span>  
<span data-ttu-id="ee641-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ee641-108">\<trackingProfile></span></span>  
<span data-ttu-id="ee641-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="ee641-109">\<workflow></span></span>  
<span data-ttu-id="ee641-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ee641-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="ee641-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="ee641-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee641-112">構文</span><span class="sxs-lookup"><span data-stu-id="ee641-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee641-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ee641-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ee641-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee641-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee641-115">属性</span><span class="sxs-lookup"><span data-stu-id="ee641-115">Attributes</span></span>  
  
|<span data-ttu-id="ee641-116">属性</span><span class="sxs-lookup"><span data-stu-id="ee641-116">Attribute</span></span>|<span data-ttu-id="ee641-117">説明</span><span class="sxs-lookup"><span data-stu-id="ee641-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ee641-118">name</span><span class="sxs-lookup"><span data-stu-id="ee641-118">name</span></span>|<span data-ttu-id="ee641-119">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="ee641-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee641-120">子要素</span><span class="sxs-lookup"><span data-stu-id="ee641-120">Child Elements</span></span>  
 <span data-ttu-id="ee641-121">なし。</span><span class="sxs-lookup"><span data-stu-id="ee641-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee641-122">親要素</span><span class="sxs-lookup"><span data-stu-id="ee641-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ee641-123">要素</span><span class="sxs-lookup"><span data-stu-id="ee641-123">Element</span></span>|<span data-ttu-id="ee641-124">説明</span><span class="sxs-lookup"><span data-stu-id="ee641-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ee641-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="ee641-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="ee641-126">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="ee641-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee641-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee641-127">See Also</span></span>  
 <span data-ttu-id="ee641-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ee641-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ee641-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ee641-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ee641-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="ee641-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ee641-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="ee641-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
