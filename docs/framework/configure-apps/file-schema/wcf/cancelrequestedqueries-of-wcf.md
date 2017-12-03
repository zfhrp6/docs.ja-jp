---
title: "WCF の &lt;cancelRequestedQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be3c02bdf0d51006d7df3b382541b704f71f2463
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="c0e14-102">WCF の &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c0e14-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="c0e14-103">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="c0e14-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c0e14-104">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c0e14-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c0e14-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c0e14-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="c0e14-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c0e14-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c0e14-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="c0e14-107">\<tracking></span></span>  
<span data-ttu-id="c0e14-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="c0e14-108">\<trackingProfile></span></span>  
<span data-ttu-id="c0e14-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="c0e14-109">\<workflow></span></span>  
<span data-ttu-id="c0e14-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="c0e14-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e14-111">構文</span><span class="sxs-lookup"><span data-stu-id="c0e14-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0e14-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c0e14-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c0e14-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c0e14-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0e14-114">属性</span><span class="sxs-lookup"><span data-stu-id="c0e14-114">Attributes</span></span>  
 <span data-ttu-id="c0e14-115">なし。</span><span class="sxs-lookup"><span data-stu-id="c0e14-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0e14-116">子要素</span><span class="sxs-lookup"><span data-stu-id="c0e14-116">Child Elements</span></span>  
  
|<span data-ttu-id="c0e14-117">要素</span><span class="sxs-lookup"><span data-stu-id="c0e14-117">Element</span></span>|<span data-ttu-id="c0e14-118">説明</span><span class="sxs-lookup"><span data-stu-id="c0e14-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0e14-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="c0e14-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="c0e14-120">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="c0e14-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0e14-121">親要素</span><span class="sxs-lookup"><span data-stu-id="c0e14-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c0e14-122">要素</span><span class="sxs-lookup"><span data-stu-id="c0e14-122">Element</span></span>|<span data-ttu-id="c0e14-123">説明</span><span class="sxs-lookup"><span data-stu-id="c0e14-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0e14-124">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="c0e14-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c0e14-125">`a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="c0e14-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0e14-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0e14-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="c0e14-127">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="c0e14-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c0e14-128">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="c0e14-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
