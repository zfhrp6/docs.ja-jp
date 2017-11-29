---
title: "WCF の &lt;activityScheduledQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97726c7faa08477351d4496650b6c08b643cdb76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="cb8ed-102">WCF の &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="cb8ed-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="cb8ed-103">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="cb8ed-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="cb8ed-104">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="cb8ed-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="cb8ed-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cb8ed-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="cb8ed-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-106">\<system.serviceModel></span></span>  
<span data-ttu-id="cb8ed-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-107">\<tracking></span></span>  
<span data-ttu-id="cb8ed-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-108">\<trackingProfile></span></span>  
<span data-ttu-id="cb8ed-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-109">\<workflow></span></span>  
<span data-ttu-id="cb8ed-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8ed-111">構文</span><span class="sxs-lookup"><span data-stu-id="cb8ed-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb8ed-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cb8ed-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cb8ed-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb8ed-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb8ed-114">属性</span><span class="sxs-lookup"><span data-stu-id="cb8ed-114">Attributes</span></span>  
 <span data-ttu-id="cb8ed-115">なし。</span><span class="sxs-lookup"><span data-stu-id="cb8ed-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb8ed-116">子要素</span><span class="sxs-lookup"><span data-stu-id="cb8ed-116">Child Elements</span></span>  
  
|<span data-ttu-id="cb8ed-117">要素</span><span class="sxs-lookup"><span data-stu-id="cb8ed-117">Element</span></span>|<span data-ttu-id="cb8ed-118">説明</span><span class="sxs-lookup"><span data-stu-id="cb8ed-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb8ed-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="cb8ed-120">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="cb8ed-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb8ed-121">親要素</span><span class="sxs-lookup"><span data-stu-id="cb8ed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="cb8ed-122">要素</span><span class="sxs-lookup"><span data-stu-id="cb8ed-122">Element</span></span>|<span data-ttu-id="cb8ed-123">説明</span><span class="sxs-lookup"><span data-stu-id="cb8ed-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb8ed-124">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="cb8ed-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="cb8ed-125">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="cb8ed-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb8ed-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb8ed-126">See Also</span></span>  
 <span data-ttu-id="cb8ed-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="cb8ed-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="cb8ed-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="cb8ed-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="cb8ed-129">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="cb8ed-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="cb8ed-130">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="cb8ed-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
