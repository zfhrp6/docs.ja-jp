---
title: '&lt;activityStateQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 175089dad7809e412444681076163163bd6831e7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="1fa3d-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="1fa3d-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="1fa3d-103">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="1fa3d-104">たとえば、「電子メール送信」アクティビティがワークフロー インスタンス内で完了を毎回の追跡することがあります。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="1fa3d-105">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="1fa3d-106">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="1fa3d-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1fa3d-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-108">\<system.serviceModel></span></span>  
<span data-ttu-id="1fa3d-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-109">\<tracking></span></span>  
<span data-ttu-id="1fa3d-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-110">\<trackingProfile></span></span>  
<span data-ttu-id="1fa3d-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-111">\<workflow></span></span>  
<span data-ttu-id="1fa3d-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa3d-113">構文</span><span class="sxs-lookup"><span data-stu-id="1fa3d-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fa3d-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1fa3d-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1fa3d-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fa3d-116">属性</span><span class="sxs-lookup"><span data-stu-id="1fa3d-116">Attributes</span></span>  
 <span data-ttu-id="1fa3d-117">なし。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1fa3d-118">子要素</span><span class="sxs-lookup"><span data-stu-id="1fa3d-118">Child Elements</span></span>  
  
|<span data-ttu-id="1fa3d-119">要素</span><span class="sxs-lookup"><span data-stu-id="1fa3d-119">Element</span></span>|<span data-ttu-id="1fa3d-120">説明</span><span class="sxs-lookup"><span data-stu-id="1fa3d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fa3d-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="1fa3d-122">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1fa3d-123">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fa3d-124">親要素</span><span class="sxs-lookup"><span data-stu-id="1fa3d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1fa3d-125">要素</span><span class="sxs-lookup"><span data-stu-id="1fa3d-125">Element</span></span>|<span data-ttu-id="1fa3d-126">説明</span><span class="sxs-lookup"><span data-stu-id="1fa3d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fa3d-127">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="1fa3d-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1fa3d-128">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1fa3d-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fa3d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fa3d-129">See Also</span></span>  
 <span data-ttu-id="1fa3d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1fa3d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1fa3d-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1fa3d-131"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="1fa3d-132">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="1fa3d-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1fa3d-133">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="1fa3d-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
