---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c9dc0e0580c884377e790fa8c1e9a23de9ecd1c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="e4eae-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e4eae-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="e4eae-103">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="e4eae-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e4eae-104">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="e4eae-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e4eae-105">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4eae-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e4eae-106">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="e4eae-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e4eae-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="e4eae-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e4eae-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e4eae-108">\<system.serviceModel></span></span>  
<span data-ttu-id="e4eae-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="e4eae-109">\<tracking></span></span>  
<span data-ttu-id="e4eae-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e4eae-110">\<trackingProfile></span></span>  
<span data-ttu-id="e4eae-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="e4eae-111">\<workflow></span></span>  
<span data-ttu-id="e4eae-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e4eae-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="e4eae-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e4eae-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4eae-114">構文</span><span class="sxs-lookup"><span data-stu-id="e4eae-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4eae-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e4eae-115">Attributes and Elements</span></span>  
 <span data-ttu-id="e4eae-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4eae-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4eae-117">属性</span><span class="sxs-lookup"><span data-stu-id="e4eae-117">Attributes</span></span>  
  
|<span data-ttu-id="e4eae-118">属性</span><span class="sxs-lookup"><span data-stu-id="e4eae-118">Attribute</span></span>|<span data-ttu-id="e4eae-119">説明</span><span class="sxs-lookup"><span data-stu-id="e4eae-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4eae-120">activityName</span><span class="sxs-lookup"><span data-stu-id="e4eae-120">activityName</span></span>|<span data-ttu-id="e4eae-121">エラーを伝達したエラー ハンドラー アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e4eae-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="e4eae-122">既定値は * で、すべてのアクティビティについてエラー伝達レコードが返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="e4eae-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="e4eae-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="e4eae-123">faultHandlerActivityName</span></span>|<span data-ttu-id="e4eae-124">エラーの原因となったアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e4eae-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4eae-125">子要素</span><span class="sxs-lookup"><span data-stu-id="e4eae-125">Child Elements</span></span>  
 <span data-ttu-id="e4eae-126">なし。</span><span class="sxs-lookup"><span data-stu-id="e4eae-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4eae-127">親要素</span><span class="sxs-lookup"><span data-stu-id="e4eae-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e4eae-128">要素</span><span class="sxs-lookup"><span data-stu-id="e4eae-128">Element</span></span>|<span data-ttu-id="e4eae-129">説明</span><span class="sxs-lookup"><span data-stu-id="e4eae-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4eae-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e4eae-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="e4eae-131">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="e4eae-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e4eae-132">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="e4eae-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4eae-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4eae-133">See Also</span></span>  
 <span data-ttu-id="e4eae-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e4eae-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e4eae-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e4eae-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e4eae-136">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="e4eae-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e4eae-137">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="e4eae-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
