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
ms.workload: dotnet
ms.openlocfilehash: f017b695b91a08c1126b48c944977c054c73affe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="b29c6-102">WCF の &lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b29c6-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="b29c6-103">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリを表します。</span><span class="sxs-lookup"><span data-stu-id="b29c6-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b29c6-104">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="b29c6-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b29c6-105">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b29c6-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b29c6-106">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="b29c6-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="b29c6-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="b29c6-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="b29c6-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b29c6-108">\<system.serviceModel></span></span>  
<span data-ttu-id="b29c6-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="b29c6-109">\<tracking></span></span>  
<span data-ttu-id="b29c6-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b29c6-110">\<trackingProfile></span></span>  
<span data-ttu-id="b29c6-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="b29c6-111">\<workflow></span></span>  
<span data-ttu-id="b29c6-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b29c6-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="b29c6-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b29c6-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b29c6-114">構文</span><span class="sxs-lookup"><span data-stu-id="b29c6-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b29c6-115">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b29c6-115">Attributes and Elements</span></span>  
 <span data-ttu-id="b29c6-116">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b29c6-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b29c6-117">属性</span><span class="sxs-lookup"><span data-stu-id="b29c6-117">Attributes</span></span>  
  
|<span data-ttu-id="b29c6-118">属性</span><span class="sxs-lookup"><span data-stu-id="b29c6-118">Attribute</span></span>|<span data-ttu-id="b29c6-119">説明</span><span class="sxs-lookup"><span data-stu-id="b29c6-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b29c6-120">activityName</span><span class="sxs-lookup"><span data-stu-id="b29c6-120">activityName</span></span>|<span data-ttu-id="b29c6-121">エラーを伝達したエラー ハンドラー アクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b29c6-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="b29c6-122">既定値は * で、すべてのアクティビティについてエラー伝達レコードが返されることを示します。</span><span class="sxs-lookup"><span data-stu-id="b29c6-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="b29c6-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="b29c6-123">faultHandlerActivityName</span></span>|<span data-ttu-id="b29c6-124">エラーの原因となったアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b29c6-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b29c6-125">子要素</span><span class="sxs-lookup"><span data-stu-id="b29c6-125">Child Elements</span></span>  
 <span data-ttu-id="b29c6-126">なし。</span><span class="sxs-lookup"><span data-stu-id="b29c6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b29c6-127">親要素</span><span class="sxs-lookup"><span data-stu-id="b29c6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b29c6-128">要素</span><span class="sxs-lookup"><span data-stu-id="b29c6-128">Element</span></span>|<span data-ttu-id="b29c6-129">説明</span><span class="sxs-lookup"><span data-stu-id="b29c6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b29c6-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="b29c6-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="b29c6-131">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、構成要素の一覧を表します。</span><span class="sxs-lookup"><span data-stu-id="b29c6-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b29c6-132">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="b29c6-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b29c6-133">参照</span><span class="sxs-lookup"><span data-stu-id="b29c6-133">See Also</span></span>  
 <span data-ttu-id="b29c6-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b29c6-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b29c6-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b29c6-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b29c6-136">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="b29c6-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b29c6-137">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="b29c6-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
