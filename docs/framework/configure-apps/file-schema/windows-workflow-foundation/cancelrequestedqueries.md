---
title: '&lt;cancelRequestedQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b3699985095fca59d5817a31c52b29fe7609a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="fd3e6-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="fd3e6-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="fd3e6-103">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="fd3e6-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="fd3e6-104">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="fd3e6-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="fd3e6-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fd3e6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fd3e6-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-106">\<system.serviceModel></span></span>  
<span data-ttu-id="fd3e6-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-107">\<tracking></span></span>  
<span data-ttu-id="fd3e6-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-108">\<trackingProfile></span></span>  
<span data-ttu-id="fd3e6-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-109">\<workflow></span></span>  
<span data-ttu-id="fd3e6-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3e6-111">構文</span><span class="sxs-lookup"><span data-stu-id="fd3e6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd3e6-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fd3e6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fd3e6-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fd3e6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd3e6-114">属性</span><span class="sxs-lookup"><span data-stu-id="fd3e6-114">Attributes</span></span>  
 <span data-ttu-id="fd3e6-115">なし。</span><span class="sxs-lookup"><span data-stu-id="fd3e6-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd3e6-116">子要素</span><span class="sxs-lookup"><span data-stu-id="fd3e6-116">Child Elements</span></span>  
  
|<span data-ttu-id="fd3e6-117">要素</span><span class="sxs-lookup"><span data-stu-id="fd3e6-117">Element</span></span>|<span data-ttu-id="fd3e6-118">説明</span><span class="sxs-lookup"><span data-stu-id="fd3e6-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd3e6-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="fd3e6-120">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="fd3e6-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd3e6-121">親要素</span><span class="sxs-lookup"><span data-stu-id="fd3e6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fd3e6-122">要素</span><span class="sxs-lookup"><span data-stu-id="fd3e6-122">Element</span></span>|<span data-ttu-id="fd3e6-123">説明</span><span class="sxs-lookup"><span data-stu-id="fd3e6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd3e6-124">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="fd3e6-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fd3e6-125">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="fd3e6-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd3e6-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd3e6-126">See Also</span></span>  
 [<span data-ttu-id="fd3e6-127">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="fd3e6-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="fd3e6-128">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="fd3e6-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
