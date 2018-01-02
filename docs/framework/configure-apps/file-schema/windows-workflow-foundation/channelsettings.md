---
title: '&lt;channelSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 94a4457f-f43f-458d-a47e-2d11103ee75e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f045665565a29f0248bf2e05bd1b285d59d6c375
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltchannelsettingsgt"></a><span data-ttu-id="ccbc7-102">&lt;channelSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="ccbc7-102">&lt;channelSettings&gt;</span></span>
<span data-ttu-id="ccbc7-103">チャネル キャッシュの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-103">Specifies the settings of the channel cache.</span></span>  
  
<span data-ttu-id="ccbc7-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccbc7-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-105">\<behaviors></span></span>  
<span data-ttu-id="ccbc7-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ccbc7-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-107">\<behavior></span></span>  
<span data-ttu-id="ccbc7-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-108">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="ccbc7-109">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-109">\<channelSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbc7-110">構文</span><span class="sxs-lookup"><span data-stu-id="ccbc7-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccbc7-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ccbc7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ccbc7-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccbc7-113">属性</span><span class="sxs-lookup"><span data-stu-id="ccbc7-113">Attributes</span></span>  
  
|<span data-ttu-id="ccbc7-114">属性</span><span class="sxs-lookup"><span data-stu-id="ccbc7-114">Attribute</span></span>|<span data-ttu-id="ccbc7-115">説明</span><span class="sxs-lookup"><span data-stu-id="ccbc7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccbc7-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="ccbc7-116">idleTimeout</span></span>|<span data-ttu-id="ccbc7-117">オブジェクトが破棄されるまでにキャッシュ内でアイドル状態を維持できる最大時間を指定する TimeSpan 値。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="ccbc7-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="ccbc7-118">leaseTimeout</span></span>|<span data-ttu-id="ccbc7-119">キャッシュからオブジェクトを削除するまでの間隔を指定する TimeSpan 値。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="ccbc7-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="ccbc7-120">maxItemsInCache</span></span>|<span data-ttu-id="ccbc7-121">キャッシュに置くことができるオブジェクトの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccbc7-122">子要素</span><span class="sxs-lookup"><span data-stu-id="ccbc7-122">Child Elements</span></span>  
 <span data-ttu-id="ccbc7-123">なし。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccbc7-124">親要素</span><span class="sxs-lookup"><span data-stu-id="ccbc7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ccbc7-125">要素</span><span class="sxs-lookup"><span data-stu-id="ccbc7-125">Element</span></span>|<span data-ttu-id="ccbc7-126">説明</span><span class="sxs-lookup"><span data-stu-id="ccbc7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccbc7-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="ccbc7-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="ccbc7-128">キャッシュ共有レベル、チャネル ファクトリ キャッシュの設定および送信メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定のカスタマイズをできるサービス動作です。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccbc7-129">コメント</span><span class="sxs-lookup"><span data-stu-id="ccbc7-129">Remarks</span></span>  
 <span data-ttu-id="ccbc7-130">このサービス動作は、サービス エンドポイントにメッセージを送信するワークフローを対象としています。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="ccbc7-131">これらのワークフローは、通常はクライアント ワークフローですが、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー サービスである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="ccbc7-132">既定では、<xref:System.ServiceModel.WorkflowServiceHost> によってホストされるワークフローでは、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティが使用するキャッシュは <xref:System.ServiceModel.WorkflowServiceHost> のすべてのワークフロー インスタンス間で共有されます (ホストレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="ccbc7-133"><xref:System.ServiceModel.WorkflowServiceHost> によってホストされないクライアント ワークフローの場合、キャッシュを使用できるのはワークフロー インスタンスだけです (インスタンスレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="ccbc7-134">構成でエンドポイントが定義されているワークフローに送信アクティビティがある場合、キャッシュは既定で無効になります。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="ccbc7-135">方法、既定のキャッシュ共有レベルを変更し、キャッシュのチャネル ファクトリおよびチャネル キャッシュ設定を参照してください[送信アクティビティのキャッシュ共有レベルを変更する](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)です。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-135"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccbc7-136">例</span><span class="sxs-lookup"><span data-stu-id="ccbc7-136">Example</span></span>  
 <span data-ttu-id="ccbc7-137">ホストされたワークフロー サービスでは、ファクトリ キャッシュとチャネル キャッシュの設定をアプリケーション構成ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="ccbc7-138">これを行うには、ファクトリ キャッシュおよびチャネル キャッシュのキャッシュ設定を含むサービス動作を追加し、そのサービス動作をサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="ccbc7-139">次の例を含む構成ファイルの内容を示しています、 **MyChannelCacheBehavior**サービス、カスタム ファクトリ キャッシュおよびチャネル キャッシュの設定で動作します。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-139">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="ccbc7-140">このサービスの動作がを通じてサービスに追加されて、 **behaviorConfiguarion**属性。</span><span class="sxs-lookup"><span data-stu-id="ccbc7-140">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccbc7-141">参照</span><span class="sxs-lookup"><span data-stu-id="ccbc7-141">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>  
 [<span data-ttu-id="ccbc7-142">Send アクティビティのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="ccbc7-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
