---
title: "WCF の &lt;activityStateQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5261e0769e63513720cc2df185920d424fa1a8f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="dd0d4-102">WCF の &lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="dd0d4-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="dd0d4-103">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="dd0d4-104">たとえば、「電子メール送信」アクティビティがワークフロー インスタンス内で完了を毎回の追跡することがあります。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="dd0d4-105">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="dd0d4-106">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="dd0d4-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="dd0d4-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-108">\<system.serviceModel></span></span>  
<span data-ttu-id="dd0d4-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-109">\<tracking></span></span>  
<span data-ttu-id="dd0d4-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-110">\<trackingProfile></span></span>  
<span data-ttu-id="dd0d4-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-111">\<workflow></span></span>  
<span data-ttu-id="dd0d4-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd0d4-113">構文</span><span class="sxs-lookup"><span data-stu-id="dd0d4-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd0d4-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dd0d4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="dd0d4-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd0d4-116">属性</span><span class="sxs-lookup"><span data-stu-id="dd0d4-116">Attributes</span></span>  
 <span data-ttu-id="dd0d4-117">なし。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd0d4-118">子要素</span><span class="sxs-lookup"><span data-stu-id="dd0d4-118">Child Elements</span></span>  
  
|<span data-ttu-id="dd0d4-119">要素</span><span class="sxs-lookup"><span data-stu-id="dd0d4-119">Element</span></span>|<span data-ttu-id="dd0d4-120">説明</span><span class="sxs-lookup"><span data-stu-id="dd0d4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd0d4-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="dd0d4-122">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dd0d4-123">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd0d4-124">親要素</span><span class="sxs-lookup"><span data-stu-id="dd0d4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="dd0d4-125">要素</span><span class="sxs-lookup"><span data-stu-id="dd0d4-125">Element</span></span>|<span data-ttu-id="dd0d4-126">説明</span><span class="sxs-lookup"><span data-stu-id="dd0d4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd0d4-127">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="dd0d4-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="dd0d4-128">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="dd0d4-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd0d4-129">参照</span><span class="sxs-lookup"><span data-stu-id="dd0d4-129">See Also</span></span>  
 <span data-ttu-id="dd0d4-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="dd0d4-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="dd0d4-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="dd0d4-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="dd0d4-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="dd0d4-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="dd0d4-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="dd0d4-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
