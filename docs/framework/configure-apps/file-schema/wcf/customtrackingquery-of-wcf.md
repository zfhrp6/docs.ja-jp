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
ms.openlocfilehash: 350ebbd0cc7be66f27ed2f70e1369e249267f359
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="b1e29-102">WCF の &lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b1e29-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="b1e29-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b1e29-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="b1e29-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="b1e29-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="b1e29-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b1e29-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="b1e29-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b1e29-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b1e29-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="b1e29-107">\<tracking></span></span>  
<span data-ttu-id="b1e29-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b1e29-108">\<trackingProfile></span></span>  
<span data-ttu-id="b1e29-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="b1e29-109">\<workflow></span></span>  
<span data-ttu-id="b1e29-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="b1e29-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="b1e29-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="b1e29-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e29-112">構文</span><span class="sxs-lookup"><span data-stu-id="b1e29-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1e29-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b1e29-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b1e29-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1e29-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1e29-115">属性</span><span class="sxs-lookup"><span data-stu-id="b1e29-115">Attributes</span></span>  
  
|<span data-ttu-id="b1e29-116">属性</span><span class="sxs-lookup"><span data-stu-id="b1e29-116">Attribute</span></span>|<span data-ttu-id="b1e29-117">説明</span><span class="sxs-lookup"><span data-stu-id="b1e29-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1e29-118">activityName</span><span class="sxs-lookup"><span data-stu-id="b1e29-118">activityName</span></span>|<span data-ttu-id="b1e29-119">追跡レコードを生成したアクティビティの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b1e29-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="b1e29-120">name</span><span class="sxs-lookup"><span data-stu-id="b1e29-120">name</span></span>|<span data-ttu-id="b1e29-121">生成されたカスタム追跡レコードの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="b1e29-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1e29-122">子要素</span><span class="sxs-lookup"><span data-stu-id="b1e29-122">Child Elements</span></span>  
 <span data-ttu-id="b1e29-123">なし。</span><span class="sxs-lookup"><span data-stu-id="b1e29-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1e29-124">親要素</span><span class="sxs-lookup"><span data-stu-id="b1e29-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b1e29-125">要素</span><span class="sxs-lookup"><span data-stu-id="b1e29-125">Element</span></span>|<span data-ttu-id="b1e29-126">説明</span><span class="sxs-lookup"><span data-stu-id="b1e29-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1e29-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="b1e29-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="b1e29-128">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="b1e29-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1e29-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1e29-129">See Also</span></span>  
 <span data-ttu-id="b1e29-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1e29-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="b1e29-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b1e29-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b1e29-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="b1e29-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b1e29-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="b1e29-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
