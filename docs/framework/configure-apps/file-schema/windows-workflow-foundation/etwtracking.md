---
title: '&lt;etwTracking&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 583c5bcb1e864b79f80a9c3095ed8ce7b74a19eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="9d836-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="9d836-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="9d836-103">により、サービスを使用して ETW の追跡を使用するサービスの動作、<xref:System.Activities.Tracking.EtwTrackingParticipant>です。</span><span class="sxs-lookup"><span data-stu-id="9d836-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="9d836-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9d836-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d836-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="9d836-105">\<behaviors></span></span>  
<span data-ttu-id="9d836-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9d836-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9d836-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="9d836-107">\<behavior></span></span>  
<span data-ttu-id="9d836-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="9d836-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d836-109">構文</span><span class="sxs-lookup"><span data-stu-id="9d836-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d836-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9d836-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d836-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d836-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d836-112">属性</span><span class="sxs-lookup"><span data-stu-id="9d836-112">Attributes</span></span>  
  
|<span data-ttu-id="9d836-113">属性</span><span class="sxs-lookup"><span data-stu-id="9d836-113">Attribute</span></span>|<span data-ttu-id="9d836-114">説明</span><span class="sxs-lookup"><span data-stu-id="9d836-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d836-115">profileName</span><span class="sxs-lookup"><span data-stu-id="9d836-115">profileName</span></span>|<span data-ttu-id="9d836-116">この動作に関連付けられた追跡プロファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="9d836-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d836-117">子要素</span><span class="sxs-lookup"><span data-stu-id="9d836-117">Child Elements</span></span>  
 <span data-ttu-id="9d836-118">なし。</span><span class="sxs-lookup"><span data-stu-id="9d836-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d836-119">親要素</span><span class="sxs-lookup"><span data-stu-id="9d836-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9d836-120">要素</span><span class="sxs-lookup"><span data-stu-id="9d836-120">Element</span></span>|<span data-ttu-id="9d836-121">説明</span><span class="sxs-lookup"><span data-stu-id="9d836-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d836-122">\<動作 > の\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9d836-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9d836-123">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="9d836-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d836-124">コメント</span><span class="sxs-lookup"><span data-stu-id="9d836-124">Remarks</span></span>  
 <span data-ttu-id="9d836-125">サービスの動作構成に追加すると、この構成要素により、ワークフロー サービスの追跡参加要素が構成されます。</span><span class="sxs-lookup"><span data-stu-id="9d836-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="9d836-126">追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9d836-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="9d836-127">同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d836-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d836-128">例</span><span class="sxs-lookup"><span data-stu-id="9d836-128">Example</span></span>  
 <span data-ttu-id="9d836-129">次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。</span><span class="sxs-lookup"><span data-stu-id="9d836-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="9d836-130">追跡レコードを ETW に書き込むため、ETW 追跡参加要素を使用するプロバイダー Id が定義されている、 **\<診断 >**セクションです。</span><span class="sxs-lookup"><span data-stu-id="9d836-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="9d836-131">追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="9d836-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="9d836-132">これは、 **profileName**の属性、 **\<追加 >**要素。</span><span class="sxs-lookup"><span data-stu-id="9d836-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="9d836-133">これらを定義すると、追跡参加要素に追加されます、  **\<etwTracking >**サービス動作。</span><span class="sxs-lookup"><span data-stu-id="9d836-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="9d836-134">これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。</span><span class="sxs-lookup"><span data-stu-id="9d836-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d836-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d836-135">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="9d836-136">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="9d836-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9d836-137">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="9d836-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
