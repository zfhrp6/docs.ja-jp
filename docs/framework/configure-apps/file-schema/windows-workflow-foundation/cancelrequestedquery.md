---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c9ad0f766256d6507775c2cca1b9d54b474abc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="27e8f-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="27e8f-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="27e8f-103">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="27e8f-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="27e8f-104">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="27e8f-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="27e8f-105">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="27e8f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="27e8f-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="27e8f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="27e8f-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="27e8f-107">\<tracking></span></span>  
<span data-ttu-id="27e8f-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="27e8f-108">\<trackingProfile></span></span>  
<span data-ttu-id="27e8f-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="27e8f-109">\<workflow></span></span>  
<span data-ttu-id="27e8f-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="27e8f-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="27e8f-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="27e8f-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e8f-112">構文</span><span class="sxs-lookup"><span data-stu-id="27e8f-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27e8f-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="27e8f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="27e8f-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="27e8f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27e8f-115">属性</span><span class="sxs-lookup"><span data-stu-id="27e8f-115">Attributes</span></span>  
  
|<span data-ttu-id="27e8f-116">属性</span><span class="sxs-lookup"><span data-stu-id="27e8f-116">Attribute</span></span>|<span data-ttu-id="27e8f-117">説明</span><span class="sxs-lookup"><span data-stu-id="27e8f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27e8f-118">activityName</span><span class="sxs-lookup"><span data-stu-id="27e8f-118">activityName</span></span>|<span data-ttu-id="27e8f-119">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="27e8f-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="27e8f-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="27e8f-120">childActivityName</span></span>|<span data-ttu-id="27e8f-121">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="27e8f-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27e8f-122">子要素</span><span class="sxs-lookup"><span data-stu-id="27e8f-122">Child Elements</span></span>  
 <span data-ttu-id="27e8f-123">なし。</span><span class="sxs-lookup"><span data-stu-id="27e8f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27e8f-124">親要素</span><span class="sxs-lookup"><span data-stu-id="27e8f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="27e8f-125">要素</span><span class="sxs-lookup"><span data-stu-id="27e8f-125">Element</span></span>|<span data-ttu-id="27e8f-126">説明</span><span class="sxs-lookup"><span data-stu-id="27e8f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27e8f-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="27e8f-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="27e8f-128">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="27e8f-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="27e8f-129">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="27e8f-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27e8f-130">参照</span><span class="sxs-lookup"><span data-stu-id="27e8f-130">See Also</span></span>  
 <span data-ttu-id="27e8f-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="27e8f-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="27e8f-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="27e8f-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="27e8f-133">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="27e8f-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="27e8f-134">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="27e8f-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
