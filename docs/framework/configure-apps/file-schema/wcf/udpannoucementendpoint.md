---
title: '&lt;udpAnnoucementEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad3ac58b92c70f32b8a0e6a81f8ebb2b23f25c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltudpannoucementendpointgt"></a><span data-ttu-id="1558b-102">&lt;udpAnnoucementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="1558b-102">&lt;udpAnnoucementEndpoint&gt;</span></span>
<span data-ttu-id="1558b-103">この構成要素は、UDP バインディングを使用してアナウンス メッセージを送信するためにサービスが使用する標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="1558b-103">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="1558b-104">これには固定コントラクトがあり、2 つの探索のバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1558b-104">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="1558b-105">また、WS-Discovery の仕様 (WS-Discovery April 2005 または WS-Discovery V1.1) に規定された固定 UDP バインディングと既定のアドレスも備えています。</span><span class="sxs-lookup"><span data-stu-id="1558b-105">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="1558b-106">アナウンス メッセージの送受信に使用するマルチキャスト アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1558b-106">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="1558b-107">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1558b-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="1558b-108">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1558b-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1558b-109">構文</span><span class="sxs-lookup"><span data-stu-id="1558b-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1558b-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1558b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1558b-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1558b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1558b-112">属性</span><span class="sxs-lookup"><span data-stu-id="1558b-112">Attributes</span></span>  
  
|<span data-ttu-id="1558b-113">属性</span><span class="sxs-lookup"><span data-stu-id="1558b-113">Attribute</span></span>|<span data-ttu-id="1558b-114">説明</span><span class="sxs-lookup"><span data-stu-id="1558b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1558b-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="1558b-115">discoveryVersion</span></span>|<span data-ttu-id="1558b-116">WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="1558b-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="1558b-117">有効値は WSDiscovery11 と WSDiscoveryApril2005 です。</span><span class="sxs-lookup"><span data-stu-id="1558b-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="1558b-118">この値は、<xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="1558b-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="1558b-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="1558b-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="1558b-120">Discovery プロトコルが Hello メッセージを送信するまでの待機時間の最大値を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="1558b-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="1558b-121">メッセージは送信前に 0 からこの属性値の間のランダムな時間だけ待機します。</span><span class="sxs-lookup"><span data-stu-id="1558b-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="1558b-122">この属性はランダムな短い待機時間を設定するために使用されるもので、ネットワークが機能しなくなり、すべてのサービスが同時にオンラインに戻ったときにネットワーク ストームが発生することを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="1558b-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="1558b-123">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="1558b-123">multicastAddress</span></span>|<span data-ttu-id="1558b-124">探索メッセージの送受信に使用するマルチキャスト アドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="1558b-124">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="1558b-125">既定値は、プロトコル仕様に準じたマルチキャスト アドレスです。</span><span class="sxs-lookup"><span data-stu-id="1558b-125">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="1558b-126">name</span><span class="sxs-lookup"><span data-stu-id="1558b-126">name</span></span>|<span data-ttu-id="1558b-127">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="1558b-127">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="1558b-128">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="1558b-128">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1558b-129">子要素</span><span class="sxs-lookup"><span data-stu-id="1558b-129">Child Elements</span></span>  
  
|<span data-ttu-id="1558b-130">要素</span><span class="sxs-lookup"><span data-stu-id="1558b-130">Element</span></span>|<span data-ttu-id="1558b-131">説明</span><span class="sxs-lookup"><span data-stu-id="1558b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1558b-132">\<udpTransportSettings ></span><span class="sxs-lookup"><span data-stu-id="1558b-132">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="1558b-133">UDP エンドポイントの UDP トランスポートを構成できる設定のコレクション。</span><span class="sxs-lookup"><span data-stu-id="1558b-133">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1558b-134">親要素</span><span class="sxs-lookup"><span data-stu-id="1558b-134">Parent Elements</span></span>  
  
|<span data-ttu-id="1558b-135">要素</span><span class="sxs-lookup"><span data-stu-id="1558b-135">Element</span></span>|<span data-ttu-id="1558b-136">説明</span><span class="sxs-lookup"><span data-stu-id="1558b-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1558b-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="1558b-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1558b-138">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="1558b-138">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1558b-139">例</span><span class="sxs-lookup"><span data-stu-id="1558b-139">Example</span></span>  
 <span data-ttu-id="1558b-140">既定のマルチキャスト アドレスを使用した UDP マルチキャスト トランスポート経由、および指定されたマルチキャスト アドレスを使用した UDP マルチキャスト トランスポート経由でアナウンスをリッスンするクライアントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1558b-140">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>  
  <service name="ServiceAnnouncementListener">  
      <endpoint name="udpAnnouncementEndpointStandard"  
                kind="udpAnnouncementEndpoint"  
                bindingConfiguration="..." />  
      <endpoint name="udpAnnouncementEndpoint2"  
                kind="udpAnnouncementEndpoint"  
                endpointConfiguration="AnnouncementConfiguration3702"  
                bindingConfiguration="..." />  
...  
  </service>  
</services>  
<standardEndpoints>  
  <udpAnnouncementEndpoint>  
     <standardEndpoint name="AnnouncementConfiguration2"   
          version="WSDiscoveryApril2005"   
          multicastAddress="soap.udp://239.255.255.250:3703"/>          
  </udpAnnouncementEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1558b-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="1558b-141">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
