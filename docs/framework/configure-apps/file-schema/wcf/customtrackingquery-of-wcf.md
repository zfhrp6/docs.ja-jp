---
title: "WCF の &lt;customTrackingQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27637abceb23a54e784afbcc2e0517db51542b53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="bdef2-102">WCF の &lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="bdef2-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="bdef2-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="bdef2-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="bdef2-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="bdef2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="bdef2-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bdef2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="bdef2-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bdef2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bdef2-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="bdef2-107">\<tracking></span></span>  
<span data-ttu-id="bdef2-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bdef2-108">\<trackingProfile></span></span>  
<span data-ttu-id="bdef2-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="bdef2-109">\<workflow></span></span>  
<span data-ttu-id="bdef2-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="bdef2-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="bdef2-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="bdef2-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdef2-112">構文</span><span class="sxs-lookup"><span data-stu-id="bdef2-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdef2-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bdef2-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bdef2-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdef2-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdef2-115">属性</span><span class="sxs-lookup"><span data-stu-id="bdef2-115">Attributes</span></span>  
  
|<span data-ttu-id="bdef2-116">属性</span><span class="sxs-lookup"><span data-stu-id="bdef2-116">Attribute</span></span>|<span data-ttu-id="bdef2-117">説明</span><span class="sxs-lookup"><span data-stu-id="bdef2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bdef2-118">activityName</span><span class="sxs-lookup"><span data-stu-id="bdef2-118">activityName</span></span>|<span data-ttu-id="bdef2-119">追跡レコードを生成したアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="bdef2-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="bdef2-120">name</span><span class="sxs-lookup"><span data-stu-id="bdef2-120">name</span></span>|<span data-ttu-id="bdef2-121">生成されたカスタム追跡レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="bdef2-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdef2-122">子要素</span><span class="sxs-lookup"><span data-stu-id="bdef2-122">Child Elements</span></span>  
 <span data-ttu-id="bdef2-123">なし。</span><span class="sxs-lookup"><span data-stu-id="bdef2-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdef2-124">親要素</span><span class="sxs-lookup"><span data-stu-id="bdef2-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bdef2-125">要素</span><span class="sxs-lookup"><span data-stu-id="bdef2-125">Element</span></span>|<span data-ttu-id="bdef2-126">説明</span><span class="sxs-lookup"><span data-stu-id="bdef2-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdef2-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="bdef2-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="bdef2-128">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="bdef2-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdef2-129">参照</span><span class="sxs-lookup"><span data-stu-id="bdef2-129">See Also</span></span>  
 <span data-ttu-id="bdef2-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bdef2-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="bdef2-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bdef2-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="bdef2-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="bdef2-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bdef2-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="bdef2-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
