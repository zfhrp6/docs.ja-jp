---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e532ea482108c9a5cabe13a99afddca10f8341d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="99cf4-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="99cf4-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="99cf4-103">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="99cf4-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="99cf4-104">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="99cf4-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="99cf4-105">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="99cf4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="99cf4-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99cf4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="99cf4-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="99cf4-107">\<tracking></span></span>  
<span data-ttu-id="99cf4-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="99cf4-108">\<trackingProfile></span></span>  
<span data-ttu-id="99cf4-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="99cf4-109">\<workflow></span></span>  
<span data-ttu-id="99cf4-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="99cf4-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="99cf4-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="99cf4-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cf4-112">構文</span><span class="sxs-lookup"><span data-stu-id="99cf4-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99cf4-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="99cf4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="99cf4-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="99cf4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99cf4-115">属性</span><span class="sxs-lookup"><span data-stu-id="99cf4-115">Attributes</span></span>  
  
|<span data-ttu-id="99cf4-116">属性</span><span class="sxs-lookup"><span data-stu-id="99cf4-116">Attribute</span></span>|<span data-ttu-id="99cf4-117">説明</span><span class="sxs-lookup"><span data-stu-id="99cf4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99cf4-118">activityName</span><span class="sxs-lookup"><span data-stu-id="99cf4-118">activityName</span></span>|<span data-ttu-id="99cf4-119">キャンセルを要求しているアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="99cf4-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="99cf4-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="99cf4-120">childActivityName</span></span>|<span data-ttu-id="99cf4-121">キャンセルが要求された子アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="99cf4-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99cf4-122">子要素</span><span class="sxs-lookup"><span data-stu-id="99cf4-122">Child Elements</span></span>  
 <span data-ttu-id="99cf4-123">なし。</span><span class="sxs-lookup"><span data-stu-id="99cf4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99cf4-124">親要素</span><span class="sxs-lookup"><span data-stu-id="99cf4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="99cf4-125">要素</span><span class="sxs-lookup"><span data-stu-id="99cf4-125">Element</span></span>|<span data-ttu-id="99cf4-126">説明</span><span class="sxs-lookup"><span data-stu-id="99cf4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99cf4-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="99cf4-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="99cf4-128">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="99cf4-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="99cf4-129">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="99cf4-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99cf4-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="99cf4-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="99cf4-131">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="99cf4-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="99cf4-132">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="99cf4-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
