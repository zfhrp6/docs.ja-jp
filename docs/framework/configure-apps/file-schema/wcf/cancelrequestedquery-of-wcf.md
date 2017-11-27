---
title: "WCF の &lt;cancelRequestedQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab16fe138701d180f528b5ec07e106acd53023b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="68b1e-102">WCF の &lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="68b1e-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="68b1e-103">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="68b1e-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="68b1e-104">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="68b1e-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="68b1e-105">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="68b1e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="68b1e-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="68b1e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="68b1e-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="68b1e-107">\<tracking></span></span>  
<span data-ttu-id="68b1e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="68b1e-108">\<trackingProfile></span></span>  
<span data-ttu-id="68b1e-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="68b1e-109">\<workflow></span></span>  
<span data-ttu-id="68b1e-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="68b1e-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="68b1e-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="68b1e-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b1e-112">構文</span><span class="sxs-lookup"><span data-stu-id="68b1e-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68b1e-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="68b1e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="68b1e-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="68b1e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68b1e-115">属性</span><span class="sxs-lookup"><span data-stu-id="68b1e-115">Attributes</span></span>  
  
|<span data-ttu-id="68b1e-116">属性</span><span class="sxs-lookup"><span data-stu-id="68b1e-116">Attribute</span></span>|<span data-ttu-id="68b1e-117">説明</span><span class="sxs-lookup"><span data-stu-id="68b1e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68b1e-118">activityName</span><span class="sxs-lookup"><span data-stu-id="68b1e-118">activityName</span></span>|<span data-ttu-id="68b1e-119">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="68b1e-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="68b1e-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="68b1e-120">childActivityName</span></span>|<span data-ttu-id="68b1e-121">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="68b1e-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68b1e-122">子要素</span><span class="sxs-lookup"><span data-stu-id="68b1e-122">Child Elements</span></span>  
 <span data-ttu-id="68b1e-123">なし。</span><span class="sxs-lookup"><span data-stu-id="68b1e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68b1e-124">親要素</span><span class="sxs-lookup"><span data-stu-id="68b1e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="68b1e-125">要素</span><span class="sxs-lookup"><span data-stu-id="68b1e-125">Element</span></span>|<span data-ttu-id="68b1e-126">説明</span><span class="sxs-lookup"><span data-stu-id="68b1e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68b1e-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="68b1e-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="68b1e-128">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="68b1e-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="68b1e-129">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="68b1e-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68b1e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="68b1e-130">See Also</span></span>  
 <span data-ttu-id="68b1e-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="68b1e-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="68b1e-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="68b1e-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="68b1e-133">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="68b1e-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="68b1e-134">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="68b1e-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
