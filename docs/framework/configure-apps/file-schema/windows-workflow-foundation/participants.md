---
title: "&lt;参加要素&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e20cc8ed26feccf6fcf7fae40d2a219cd103dbb0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltparticipantsgt"></a><span data-ttu-id="bb1ae-102">&lt;参加要素&gt;</span><span class="sxs-lookup"><span data-stu-id="bb1ae-102">&lt;participants&gt;</span></span>
<span data-ttu-id="bb1ae-103">ランタイムから直接出力される追跡レコードをリッスンし、追跡レコードの構成方法に従って処理を行う追跡参加要素の一覧を構成します。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="bb1ae-104">これには、特定の出力 (ファイル、コンソール、ETW など) への書き込み、レコードの処理や集計、またはその他の必要な組み合わせが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="bb1ae-105">ワークフロー追跡と追跡参加要素の詳細については、次を参照してください。[ワークフロー追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)と[追跡参加要素](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="bb1ae-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bb1ae-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bb1ae-107">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="bb1ae-107">\<tracking></span></span>  
<span data-ttu-id="bb1ae-108">\<参加者 ></span><span class="sxs-lookup"><span data-stu-id="bb1ae-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb1ae-109">構文</span><span class="sxs-lookup"><span data-stu-id="bb1ae-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb1ae-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="bb1ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bb1ae-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb1ae-112">属性</span><span class="sxs-lookup"><span data-stu-id="bb1ae-112">Attributes</span></span>  
 <span data-ttu-id="bb1ae-113">なし。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb1ae-114">子要素</span><span class="sxs-lookup"><span data-stu-id="bb1ae-114">Child Elements</span></span>  
  
|<span data-ttu-id="bb1ae-115">要素</span><span class="sxs-lookup"><span data-stu-id="bb1ae-115">Element</span></span>|<span data-ttu-id="bb1ae-116">説明</span><span class="sxs-lookup"><span data-stu-id="bb1ae-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb1ae-117">\<add></span><span class="sxs-lookup"><span data-stu-id="bb1ae-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="bb1ae-118">追跡参加要素を処理するための設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb1ae-119">親要素</span><span class="sxs-lookup"><span data-stu-id="bb1ae-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bb1ae-120">要素</span><span class="sxs-lookup"><span data-stu-id="bb1ae-120">Element</span></span>|<span data-ttu-id="bb1ae-121">説明</span><span class="sxs-lookup"><span data-stu-id="bb1ae-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb1ae-122">\<追跡 ></span><span class="sxs-lookup"><span data-stu-id="bb1ae-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="bb1ae-123">ワークフロー サービスの追跡設定を定義する構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb1ae-124">コメント</span><span class="sxs-lookup"><span data-stu-id="bb1ae-124">Remarks</span></span>  
 <span data-ttu-id="bb1ae-125">追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="bb1ae-126">同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="bb1ae-127">複数の追跡参加要素が追跡イベントを同時に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="bb1ae-128">各追跡参加要素は、それぞれ別の追跡プロファイルと関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="bb1ae-129">追跡レコードを ETW セッションに書き込む、標準の追跡参加要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="bb1ae-130">参加要素は、追跡固有の動作を構成ファイルに追加することによって、ワークフロー サービスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="bb1ae-131">ETW 追跡参加要素を有効にすると、追跡レコードをイベント ビューアーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="bb1ae-132">これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb1ae-133">例</span><span class="sxs-lookup"><span data-stu-id="bb1ae-133">Example</span></span>  
 <span data-ttu-id="bb1ae-134">次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="bb1ae-135">追跡レコードを ETW に書き込むため、ETW 追跡参加要素を使用するプロバイダー Id が定義されている、 **\<診断 >**セクションです。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="bb1ae-136">追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="bb1ae-137">これは、 **profileName**の属性、 **\<追加 >**要素。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="bb1ae-138">これらを定義すると、追跡参加要素に追加されます、  **\<etwTracking >**サービス動作。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="bb1ae-139">これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。</span><span class="sxs-lookup"><span data-stu-id="bb1ae-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb1ae-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb1ae-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="bb1ae-141">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="bb1ae-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bb1ae-142">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="bb1ae-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
