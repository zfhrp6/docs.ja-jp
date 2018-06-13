---
title: WCF の &lt;customTrackingQueries&gt;
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 11ad4281d2925a48508c6a3e8258b0b1cd49a326
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749687"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="29148-102">WCF の &lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="29148-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="29148-103">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="29148-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="29148-104">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="29148-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="29148-105">追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="29148-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="29148-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="29148-106">\<system.serviceModel></span></span>  
<span data-ttu-id="29148-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="29148-107">\<tracking></span></span>  
<span data-ttu-id="29148-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="29148-108">\<trackingProfile></span></span>  
<span data-ttu-id="29148-109">\<ワークフロー ></span><span class="sxs-lookup"><span data-stu-id="29148-109">\<workflow></span></span>  
<span data-ttu-id="29148-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="29148-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29148-111">構文</span><span class="sxs-lookup"><span data-stu-id="29148-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29148-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="29148-112">Attributes and Elements</span></span>  
 <span data-ttu-id="29148-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="29148-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29148-114">属性</span><span class="sxs-lookup"><span data-stu-id="29148-114">Attributes</span></span>  
 <span data-ttu-id="29148-115">なし。</span><span class="sxs-lookup"><span data-stu-id="29148-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="29148-116">子要素</span><span class="sxs-lookup"><span data-stu-id="29148-116">Child Elements</span></span>  
  
|<span data-ttu-id="29148-117">要素</span><span class="sxs-lookup"><span data-stu-id="29148-117">Element</span></span>|<span data-ttu-id="29148-118">説明</span><span class="sxs-lookup"><span data-stu-id="29148-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29148-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="29148-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="29148-120">コード アクティビティで定義するイベントを追跡するために使用するクエリ。</span><span class="sxs-lookup"><span data-stu-id="29148-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29148-121">親要素</span><span class="sxs-lookup"><span data-stu-id="29148-121">Parent Elements</span></span>  
  
|<span data-ttu-id="29148-122">要素</span><span class="sxs-lookup"><span data-stu-id="29148-122">Element</span></span>|<span data-ttu-id="29148-123">説明</span><span class="sxs-lookup"><span data-stu-id="29148-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29148-124">\<workflow></span><span class="sxs-lookup"><span data-stu-id="29148-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="29148-125">`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="29148-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29148-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="29148-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="29148-127">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="29148-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="29148-128">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="29148-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
