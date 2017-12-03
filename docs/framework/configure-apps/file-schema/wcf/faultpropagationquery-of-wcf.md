---
title: "WCF の &lt;faultPropagationQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 330413b676025020924dc15f54170c4dc19e616a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="4f73b-102">WCF の &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="4f73b-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="4f73b-103">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="4f73b-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4f73b-104">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="4f73b-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="4f73b-105">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f73b-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="4f73b-106">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="4f73b-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="4f73b-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f73b-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="4f73b-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4f73b-108">\<system.serviceModel></span></span>  
<span data-ttu-id="4f73b-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="4f73b-109">\<tracking></span></span>  
<span data-ttu-id="4f73b-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4f73b-110">\<trackingProfile></span></span>  
<span data-ttu-id="4f73b-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="4f73b-111">\<workflow></span></span>  
<span data-ttu-id="4f73b-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="4f73b-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="4f73b-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="4f73b-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f73b-114">構文</span><span class="sxs-lookup"><span data-stu-id="4f73b-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f73b-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4f73b-115">Attributes and Elements</span></span>  
 <span data-ttu-id="4f73b-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4f73b-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f73b-117">属性</span><span class="sxs-lookup"><span data-stu-id="4f73b-117">Attributes</span></span>  
  
|<span data-ttu-id="4f73b-118">属性</span><span class="sxs-lookup"><span data-stu-id="4f73b-118">Attribute</span></span>|<span data-ttu-id="4f73b-119">説明</span><span class="sxs-lookup"><span data-stu-id="4f73b-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f73b-120">activityName</span><span class="sxs-lookup"><span data-stu-id="4f73b-120">activityName</span></span>|<span data-ttu-id="4f73b-121">エラーを伝達したエラー ハンドラー アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4f73b-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="4f73b-122">既定値は * で、すべてのアクティビティについてエラー伝達レコードが返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="4f73b-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="4f73b-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="4f73b-123">faultHandlerActivityName</span></span>|<span data-ttu-id="4f73b-124">エラーの原因となったアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4f73b-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f73b-125">子要素</span><span class="sxs-lookup"><span data-stu-id="4f73b-125">Child Elements</span></span>  
 <span data-ttu-id="4f73b-126">なし。</span><span class="sxs-lookup"><span data-stu-id="4f73b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f73b-127">親要素</span><span class="sxs-lookup"><span data-stu-id="4f73b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4f73b-128">要素</span><span class="sxs-lookup"><span data-stu-id="4f73b-128">Element</span></span>|<span data-ttu-id="4f73b-129">説明</span><span class="sxs-lookup"><span data-stu-id="4f73b-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f73b-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="4f73b-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="4f73b-131">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="4f73b-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4f73b-132">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="4f73b-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f73b-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f73b-133">See Also</span></span>  
 <span data-ttu-id="4f73b-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4f73b-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4f73b-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4f73b-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="4f73b-136">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="4f73b-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4f73b-137">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="4f73b-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
