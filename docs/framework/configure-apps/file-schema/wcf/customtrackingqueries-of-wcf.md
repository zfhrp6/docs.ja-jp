---
title: "WCF の &lt;customTrackingQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1d87a5b95d7679018c7e50af3c8e1c0265a3d4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="b4ae2-102">WCF の &lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="b4ae2-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="b4ae2-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b4ae2-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="b4ae2-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="b4ae2-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="b4ae2-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b4ae2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="b4ae2-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b4ae2-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-107">\<tracking></span></span>  
<span data-ttu-id="b4ae2-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-108">\<trackingProfile></span></span>  
<span data-ttu-id="b4ae2-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-109">\<workflow></span></span>  
<span data-ttu-id="b4ae2-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ae2-111">構文</span><span class="sxs-lookup"><span data-stu-id="b4ae2-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4ae2-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b4ae2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b4ae2-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4ae2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4ae2-114">属性</span><span class="sxs-lookup"><span data-stu-id="b4ae2-114">Attributes</span></span>  
 <span data-ttu-id="b4ae2-115">なし。</span><span class="sxs-lookup"><span data-stu-id="b4ae2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4ae2-116">子要素</span><span class="sxs-lookup"><span data-stu-id="b4ae2-116">Child Elements</span></span>  
  
|<span data-ttu-id="b4ae2-117">要素</span><span class="sxs-lookup"><span data-stu-id="b4ae2-117">Element</span></span>|<span data-ttu-id="b4ae2-118">説明</span><span class="sxs-lookup"><span data-stu-id="b4ae2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4ae2-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="b4ae2-120">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="b4ae2-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4ae2-121">親要素</span><span class="sxs-lookup"><span data-stu-id="b4ae2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b4ae2-122">要素</span><span class="sxs-lookup"><span data-stu-id="b4ae2-122">Element</span></span>|<span data-ttu-id="b4ae2-123">説明</span><span class="sxs-lookup"><span data-stu-id="b4ae2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4ae2-124">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="b4ae2-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b4ae2-125">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="b4ae2-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4ae2-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4ae2-126">See Also</span></span>  
 <span data-ttu-id="b4ae2-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b4ae2-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b4ae2-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b4ae2-128"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b4ae2-129">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="b4ae2-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b4ae2-130">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="b4ae2-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
