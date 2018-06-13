---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 2abb2dc05bfec4419ca49d1517084ebc208e81e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757022"
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="a105d-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="a105d-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="a105d-103">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="a105d-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a105d-104">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="a105d-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="a105d-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a105d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a105d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a105d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="a105d-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="a105d-107">\<tracking></span></span>  
<span data-ttu-id="a105d-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a105d-108">\<trackingProfile></span></span>  
<span data-ttu-id="a105d-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="a105d-109">\<workflow></span></span>  
<span data-ttu-id="a105d-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="a105d-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a105d-111">構文</span><span class="sxs-lookup"><span data-stu-id="a105d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a105d-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a105d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a105d-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a105d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a105d-114">属性</span><span class="sxs-lookup"><span data-stu-id="a105d-114">Attributes</span></span>  
 <span data-ttu-id="a105d-115">なし。</span><span class="sxs-lookup"><span data-stu-id="a105d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a105d-116">子要素</span><span class="sxs-lookup"><span data-stu-id="a105d-116">Child Elements</span></span>  
  
|<span data-ttu-id="a105d-117">要素</span><span class="sxs-lookup"><span data-stu-id="a105d-117">Element</span></span>|<span data-ttu-id="a105d-118">説明</span><span class="sxs-lookup"><span data-stu-id="a105d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a105d-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="a105d-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="a105d-120">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="a105d-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a105d-121">親要素</span><span class="sxs-lookup"><span data-stu-id="a105d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a105d-122">要素</span><span class="sxs-lookup"><span data-stu-id="a105d-122">Element</span></span>|<span data-ttu-id="a105d-123">説明</span><span class="sxs-lookup"><span data-stu-id="a105d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a105d-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="a105d-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a105d-125">によって識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a105d-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a105d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a105d-126">See Also</span></span>  
 [<span data-ttu-id="a105d-127">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="a105d-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a105d-128">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="a105d-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
