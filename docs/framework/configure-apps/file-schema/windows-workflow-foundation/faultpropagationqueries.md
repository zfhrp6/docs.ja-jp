---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 5fd6ffc9560247089c7fbb60b0e5a7d3a417ea6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="c2107-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c2107-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="c2107-103">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="c2107-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c2107-104">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="c2107-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c2107-105">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2107-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c2107-106">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="c2107-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c2107-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2107-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c2107-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c2107-108">\<system.serviceModel></span></span>  
<span data-ttu-id="c2107-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="c2107-109">\<tracking></span></span>  
<span data-ttu-id="c2107-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c2107-110">\<trackingProfile></span></span>  
<span data-ttu-id="c2107-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="c2107-111">\<workflow></span></span>  
<span data-ttu-id="c2107-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c2107-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2107-113">構文</span><span class="sxs-lookup"><span data-stu-id="c2107-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2107-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c2107-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c2107-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c2107-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2107-116">属性</span><span class="sxs-lookup"><span data-stu-id="c2107-116">Attributes</span></span>  
 <span data-ttu-id="c2107-117">なし。</span><span class="sxs-lookup"><span data-stu-id="c2107-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2107-118">子要素</span><span class="sxs-lookup"><span data-stu-id="c2107-118">Child Elements</span></span>  
  
|<span data-ttu-id="c2107-119">要素</span><span class="sxs-lookup"><span data-stu-id="c2107-119">Element</span></span>|<span data-ttu-id="c2107-120">説明</span><span class="sxs-lookup"><span data-stu-id="c2107-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2107-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c2107-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="c2107-122">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="c2107-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c2107-123">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="c2107-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2107-124">親要素</span><span class="sxs-lookup"><span data-stu-id="c2107-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c2107-125">要素</span><span class="sxs-lookup"><span data-stu-id="c2107-125">Element</span></span>|<span data-ttu-id="c2107-126">説明</span><span class="sxs-lookup"><span data-stu-id="c2107-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2107-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="c2107-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c2107-128">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c2107-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2107-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2107-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="c2107-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="c2107-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c2107-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="c2107-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
