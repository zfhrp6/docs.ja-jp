---
title: '&lt;announcementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae03b5d4a82c08978a3456e80428ba6ad8ac532a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="90980-102">&lt;announcementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="90980-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="90980-103">この構成要素は、固定アナウンス コントラクトが設定されている標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="90980-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="90980-104">サービスは、サービスが開いたとき、または閉じたときにオンラインおよびオフラインのアナウンス メッセージを送信することによって、その可用性をアナウンスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="90980-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="90980-105">A[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]サービスでアナウンス エンドポイントの指定、 [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)要素と使用をお知らせを実行する AnnouncementClient です。</span><span class="sxs-lookup"><span data-stu-id="90980-105">A [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="90980-106">他のサービスからのアナウンスが実際として動作しているをリッスンするように元のクライアントは、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ; のサービスでそのクライアントのアナウンス エンドポイントを構成する必要があるため、 [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)セクションです。</span><span class="sxs-lookup"><span data-stu-id="90980-106">A client wishing to listen for the announcement from other service is actually acting as a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="90980-107">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="90980-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="90980-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="90980-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90980-109">構文</span><span class="sxs-lookup"><span data-stu-id="90980-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan" 
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90980-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="90980-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90980-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90980-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90980-112">属性</span><span class="sxs-lookup"><span data-stu-id="90980-112">Attributes</span></span>  
  
|<span data-ttu-id="90980-113">属性</span><span class="sxs-lookup"><span data-stu-id="90980-113">Attribute</span></span>|<span data-ttu-id="90980-114">説明</span><span class="sxs-lookup"><span data-stu-id="90980-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90980-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="90980-115">discoveryVersion</span></span>|<span data-ttu-id="90980-116">WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="90980-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="90980-117">有効値は WSDiscovery11 と WSDiscoveryApril2005 です。</span><span class="sxs-lookup"><span data-stu-id="90980-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="90980-118">この値は、<xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="90980-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="90980-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="90980-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="90980-120">Discovery プロトコルが Hello メッセージを送信するまでの待機時間の最大値を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="90980-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="90980-121">メッセージは送信前に 0 からこの属性値の間のランダムな時間だけ待機します。</span><span class="sxs-lookup"><span data-stu-id="90980-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="90980-122">この属性はランダムな短い待機時間を設定するために使用されるもので、ネットワークが機能しなくなり、すべてのサービスが同時にオンラインに戻ったときにネットワーク ストームが発生することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="90980-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="90980-123">name</span><span class="sxs-lookup"><span data-stu-id="90980-123">name</span></span>|<span data-ttu-id="90980-124">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="90980-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="90980-125">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="90980-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90980-126">子要素</span><span class="sxs-lookup"><span data-stu-id="90980-126">Child Elements</span></span>  
 <span data-ttu-id="90980-127">なし。</span><span class="sxs-lookup"><span data-stu-id="90980-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90980-128">親要素</span><span class="sxs-lookup"><span data-stu-id="90980-128">Parent Elements</span></span>  
  
|<span data-ttu-id="90980-129">要素</span><span class="sxs-lookup"><span data-stu-id="90980-129">Element</span></span>|<span data-ttu-id="90980-130">説明</span><span class="sxs-lookup"><span data-stu-id="90980-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90980-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="90980-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="90980-132">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="90980-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90980-133">例</span><span class="sxs-lookup"><span data-stu-id="90980-133">Example</span></span>  
 <span data-ttu-id="90980-134">http およびピア ネットワーク経由でアナウンス メッセージをリッスンするクライアントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="90980-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
    <endpoint name="httpAnnouncementEndpoint"  
              kind="announcementEndpoint"  
              binding="basicHttpBinding"  
              address="announcements" />  
    <endpoint name="peerNetAnnouncementEndpoint"  
              kind="announcementEndpoint"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />  
  ...  
  </service>  
</services>  
  
<standardEndpoints>  
  <announcementEndpoint>  
    <standardEndpoint name="httpAnnouncementEndpoint"                         
                      version="WSDiscoveryApril2005" />  
    <standardEndpoint name="peerNetAnnouncementEndpoint"                         
                      version="WSDiscoveryApril2005" />  
   </announcementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a><span data-ttu-id="90980-135">参照</span><span class="sxs-lookup"><span data-stu-id="90980-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
