---
title: '&lt;announcementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 3ce141d70e17c14facd6aa8560c7b3424a8d9ae8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="62eb1-102">&lt;announcementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="62eb1-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="62eb1-103">この構成要素は、固定アナウンス コントラクトが設定されている標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="62eb1-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="62eb1-104">サービスは、サービスが開いたとき、または閉じたときにオンラインおよびオフラインのアナウンス メッセージを送信することによって、その可用性をアナウンスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="62eb1-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="62eb1-105">Windows Communication Foundation (WCF) サービスでアナウンス エンドポイントを指定する、 [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)要素と使用をお知らせを実行する AnnouncementClient です。</span><span class="sxs-lookup"><span data-stu-id="62eb1-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="62eb1-106">他のサービスからのアナウンスが実際として動作しているをリッスンするように元のクライアントは、 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ; のサービスでそのクライアントのアナウンス エンドポイントを構成する必要があるため、 [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)セクションです。</span><span class="sxs-lookup"><span data-stu-id="62eb1-106">A client wishing to listen for the announcement from other service is actually acting as a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="62eb1-107">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="62eb1-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="62eb1-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="62eb1-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62eb1-109">構文</span><span class="sxs-lookup"><span data-stu-id="62eb1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62eb1-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="62eb1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62eb1-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="62eb1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62eb1-112">属性</span><span class="sxs-lookup"><span data-stu-id="62eb1-112">Attributes</span></span>  
  
|<span data-ttu-id="62eb1-113">属性</span><span class="sxs-lookup"><span data-stu-id="62eb1-113">Attribute</span></span>|<span data-ttu-id="62eb1-114">説明</span><span class="sxs-lookup"><span data-stu-id="62eb1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62eb1-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="62eb1-115">discoveryVersion</span></span>|<span data-ttu-id="62eb1-116">WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="62eb1-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="62eb1-117">有効値は WSDiscovery11 と WSDiscoveryApril2005 です。</span><span class="sxs-lookup"><span data-stu-id="62eb1-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="62eb1-118">この値は、<xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="62eb1-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="62eb1-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="62eb1-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="62eb1-120">Discovery プロトコルが Hello メッセージを送信するまでの待機時間の最大値を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="62eb1-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="62eb1-121">メッセージは送信前に 0 からこの属性値の間のランダムな時間だけ待機します。</span><span class="sxs-lookup"><span data-stu-id="62eb1-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="62eb1-122">この属性はランダムな短い待機時間を設定するために使用されるもので、ネットワークが機能しなくなり、すべてのサービスが同時にオンラインに戻ったときにネットワーク ストームが発生することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="62eb1-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="62eb1-123">name</span><span class="sxs-lookup"><span data-stu-id="62eb1-123">name</span></span>|<span data-ttu-id="62eb1-124">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="62eb1-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="62eb1-125">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="62eb1-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62eb1-126">子要素</span><span class="sxs-lookup"><span data-stu-id="62eb1-126">Child Elements</span></span>  
 <span data-ttu-id="62eb1-127">なし。</span><span class="sxs-lookup"><span data-stu-id="62eb1-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62eb1-128">親要素</span><span class="sxs-lookup"><span data-stu-id="62eb1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="62eb1-129">要素</span><span class="sxs-lookup"><span data-stu-id="62eb1-129">Element</span></span>|<span data-ttu-id="62eb1-130">説明</span><span class="sxs-lookup"><span data-stu-id="62eb1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62eb1-131">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="62eb1-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="62eb1-132">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="62eb1-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="62eb1-133">例</span><span class="sxs-lookup"><span data-stu-id="62eb1-133">Example</span></span>  
 <span data-ttu-id="62eb1-134">http およびピア ネットワーク経由でアナウンス メッセージをリッスンするクライアントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="62eb1-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62eb1-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="62eb1-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
