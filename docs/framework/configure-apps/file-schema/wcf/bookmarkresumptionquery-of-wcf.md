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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3240fcf026869aee7540c0e792ccd81e2592e620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="d8f6b-102">WCF の &lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="d8f6b-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="d8f6b-103">ワークフロー インスタンス内のブックマークの再開を追跡するために使用されるクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="d8f6b-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d8f6b-104">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="d8f6b-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="d8f6b-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8f6b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d8f6b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d8f6b-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-107">\<tracking></span></span>  
<span data-ttu-id="d8f6b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-108">\<trackingProfile></span></span>  
<span data-ttu-id="d8f6b-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-109">\<workflow></span></span>  
<span data-ttu-id="d8f6b-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="d8f6b-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8f6b-112">構文</span><span class="sxs-lookup"><span data-stu-id="d8f6b-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8f6b-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d8f6b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d8f6b-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8f6b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8f6b-115">属性</span><span class="sxs-lookup"><span data-stu-id="d8f6b-115">Attributes</span></span>  
  
|<span data-ttu-id="d8f6b-116">属性</span><span class="sxs-lookup"><span data-stu-id="d8f6b-116">Attribute</span></span>|<span data-ttu-id="d8f6b-117">説明</span><span class="sxs-lookup"><span data-stu-id="d8f6b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8f6b-118">name</span><span class="sxs-lookup"><span data-stu-id="d8f6b-118">name</span></span>|<span data-ttu-id="d8f6b-119">定期受信するブックマーク レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d8f6b-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8f6b-120">子要素</span><span class="sxs-lookup"><span data-stu-id="d8f6b-120">Child Elements</span></span>  
 <span data-ttu-id="d8f6b-121">なし。</span><span class="sxs-lookup"><span data-stu-id="d8f6b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8f6b-122">親要素</span><span class="sxs-lookup"><span data-stu-id="d8f6b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d8f6b-123">要素</span><span class="sxs-lookup"><span data-stu-id="d8f6b-123">Element</span></span>|<span data-ttu-id="d8f6b-124">説明</span><span class="sxs-lookup"><span data-stu-id="d8f6b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8f6b-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="d8f6b-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="d8f6b-126">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="d8f6b-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8f6b-127">参照</span><span class="sxs-lookup"><span data-stu-id="d8f6b-127">See Also</span></span>  
 <span data-ttu-id="d8f6b-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d8f6b-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="d8f6b-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d8f6b-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="d8f6b-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="d8f6b-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d8f6b-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="d8f6b-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
