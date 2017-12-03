---
title: "ワークフローの &lt;serviceBehaviors&gt; の &lt;behavior&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3a25e0cf9f5390fcc05cf9db0b6071ea94b9a4c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="4c7de-102">ワークフローの &lt;serviceBehaviors&gt; の &lt;behavior&gt;</span><span class="sxs-lookup"><span data-stu-id="4c7de-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="4c7de-103">**動作**要素には、サービスの動作の設定のコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c7de-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="4c7de-104">各動作のインデックスを作成してその**名前**です。</span><span class="sxs-lookup"><span data-stu-id="4c7de-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="4c7de-105">サービスを使用して、この名前を使用して各動作にリンクできます、 **behaviorConfiguration**の属性、 [\<エンドポイント >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="4c7de-105">Services can link to each behavior through this name using the **behaviorConfiguration**attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="4c7de-106">これにより、設定を再定義することなく、エンドポイント間で共通の動作構成を共有できます。</span><span class="sxs-lookup"><span data-stu-id="4c7de-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="4c7de-107">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4c7de-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="4c7de-108">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="4c7de-108">\<behaviors></span></span>  
<span data-ttu-id="4c7de-109">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4c7de-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="4c7de-110">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="4c7de-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c7de-111">構文</span><span class="sxs-lookup"><span data-stu-id="4c7de-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  honstLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c7de-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4c7de-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4c7de-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c7de-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c7de-114">属性</span><span class="sxs-lookup"><span data-stu-id="4c7de-114">Attributes</span></span>  
  
|<span data-ttu-id="4c7de-115">属性</span><span class="sxs-lookup"><span data-stu-id="4c7de-115">Attribute</span></span>|<span data-ttu-id="4c7de-116">説明</span><span class="sxs-lookup"><span data-stu-id="4c7de-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c7de-117">name</span><span class="sxs-lookup"><span data-stu-id="4c7de-117">name</span></span>|<span data-ttu-id="4c7de-118">動作の構成名を含む一意の文字列。</span><span class="sxs-lookup"><span data-stu-id="4c7de-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="4c7de-119">この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c7de-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c7de-120">子要素</span><span class="sxs-lookup"><span data-stu-id="4c7de-120">Child Elements</span></span>  
  
|<span data-ttu-id="4c7de-121">要素</span><span class="sxs-lookup"><span data-stu-id="4c7de-121">Element</span></span>|<span data-ttu-id="4c7de-122">説明</span><span class="sxs-lookup"><span data-stu-id="4c7de-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c7de-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="4c7de-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="4c7de-124">サービスが、バッファーされた受信処理を使用するためのサービス動作。これにより、ワークフロー サービスは、順番を無視したメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="4c7de-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="4c7de-125">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="4c7de-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="4c7de-126">により、サービスを使用して ETW の追跡を使用するサービスの動作、<xref:System.Activities.Tracking.EtwTrackingParticipant>です。</span><span class="sxs-lookup"><span data-stu-id="4c7de-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="4c7de-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="4c7de-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="4c7de-128">キャッシュ共有レベル、チャネル ファクトリ キャッシュの設定および送信メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定のカスタマイズをできるサービス動作です。</span><span class="sxs-lookup"><span data-stu-id="4c7de-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="4c7de-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="4c7de-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="4c7de-130">サービスの動作を構成することができます、<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>機能で、SQL Server 2005 または SQL Server 2008 データベースにワークフロー サービス インスタンスの永続化の状態情報をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4c7de-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="4c7de-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="4c7de-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="4c7de-132">アイドル状態のワークフロー インスタンスのアンロードおよび永続化のタイミングを制御するサービス動作。</span><span class="sxs-lookup"><span data-stu-id="4c7de-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="4c7de-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="4c7de-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="4c7de-134">ワークフロー インスタンスの実行方法を制御する設定を指定するためのサービス動作。これには、永続する未処理の例外動作やアイドル状態の動作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4c7de-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="4c7de-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="4c7de-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="4c7de-136">ワークフロー サービス内で未処理の例外が発生した場合のアクションを指定するためのサービス動作。</span><span class="sxs-lookup"><span data-stu-id="4c7de-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c7de-137">親要素</span><span class="sxs-lookup"><span data-stu-id="4c7de-137">Parent Elements</span></span>  
  
|<span data-ttu-id="4c7de-138">要素</span><span class="sxs-lookup"><span data-stu-id="4c7de-138">Element</span></span>|<span data-ttu-id="4c7de-139">説明</span><span class="sxs-lookup"><span data-stu-id="4c7de-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c7de-140">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4c7de-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="4c7de-141">サービス動作要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="4c7de-141">A collection of service behavior elements.</span></span>|
