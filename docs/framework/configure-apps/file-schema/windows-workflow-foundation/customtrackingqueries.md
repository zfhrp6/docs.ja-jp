---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: aa1e7ff4d53cbd40b168c3cc800a23dbcddc28f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="c6125-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c6125-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="c6125-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="c6125-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="c6125-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c6125-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="c6125-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c6125-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c6125-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6125-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c6125-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="c6125-107">\<tracking></span></span>  
<span data-ttu-id="c6125-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c6125-108">\<trackingProfile></span></span>  
<span data-ttu-id="c6125-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="c6125-109">\<workflow></span></span>  
<span data-ttu-id="c6125-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="c6125-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6125-111">構文</span><span class="sxs-lookup"><span data-stu-id="c6125-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6125-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c6125-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c6125-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6125-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6125-114">属性</span><span class="sxs-lookup"><span data-stu-id="c6125-114">Attributes</span></span>  
 <span data-ttu-id="c6125-115">なし。</span><span class="sxs-lookup"><span data-stu-id="c6125-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6125-116">子要素</span><span class="sxs-lookup"><span data-stu-id="c6125-116">Child Elements</span></span>  
  
|<span data-ttu-id="c6125-117">要素</span><span class="sxs-lookup"><span data-stu-id="c6125-117">Element</span></span>|<span data-ttu-id="c6125-118">説明</span><span class="sxs-lookup"><span data-stu-id="c6125-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6125-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="c6125-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="c6125-120">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="c6125-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6125-121">親要素</span><span class="sxs-lookup"><span data-stu-id="c6125-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c6125-122">要素</span><span class="sxs-lookup"><span data-stu-id="c6125-122">Element</span></span>|<span data-ttu-id="c6125-123">説明</span><span class="sxs-lookup"><span data-stu-id="c6125-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6125-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c6125-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c6125-125">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c6125-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6125-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6125-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="c6125-127">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="c6125-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c6125-128">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="c6125-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
