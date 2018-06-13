---
title: WCF の &lt;faultPropagationQueries&gt;
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 5db043b5d4d150628df386dafb6e7bd351a0a28a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754005"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="7b0ef-102">WCF の &lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7b0ef-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="7b0ef-103">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="7b0ef-104">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="7b0ef-105">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="7b0ef-106">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="7b0ef-107">追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="7b0ef-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7b0ef-108">\<system.serviceModel></span></span>  
<span data-ttu-id="7b0ef-109">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="7b0ef-109">\<tracking></span></span>  
<span data-ttu-id="7b0ef-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7b0ef-110">\<trackingProfile></span></span>  
<span data-ttu-id="7b0ef-111">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="7b0ef-111">\<workflow></span></span>  
<span data-ttu-id="7b0ef-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="7b0ef-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b0ef-113">構文</span><span class="sxs-lookup"><span data-stu-id="7b0ef-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b0ef-114">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7b0ef-114">Attributes and Elements</span></span>  
 <span data-ttu-id="7b0ef-115">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b0ef-116">属性</span><span class="sxs-lookup"><span data-stu-id="7b0ef-116">Attributes</span></span>  
 <span data-ttu-id="7b0ef-117">なし。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b0ef-118">子要素</span><span class="sxs-lookup"><span data-stu-id="7b0ef-118">Child Elements</span></span>  
  
|<span data-ttu-id="7b0ef-119">要素</span><span class="sxs-lookup"><span data-stu-id="7b0ef-119">Element</span></span>|<span data-ttu-id="7b0ef-120">説明</span><span class="sxs-lookup"><span data-stu-id="7b0ef-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b0ef-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="7b0ef-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="7b0ef-122">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="7b0ef-123">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b0ef-124">親要素</span><span class="sxs-lookup"><span data-stu-id="7b0ef-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7b0ef-125">要素</span><span class="sxs-lookup"><span data-stu-id="7b0ef-125">Element</span></span>|<span data-ttu-id="7b0ef-126">説明</span><span class="sxs-lookup"><span data-stu-id="7b0ef-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b0ef-127">\<workflow></span><span class="sxs-lookup"><span data-stu-id="7b0ef-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7b0ef-128">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="7b0ef-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b0ef-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b0ef-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="7b0ef-130">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="7b0ef-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7b0ef-131">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="7b0ef-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
