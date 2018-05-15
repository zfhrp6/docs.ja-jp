---
title: '&lt;discoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6a352fbfced08001f76dceaff283d6bca25f56f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiscoveryendpointgt"></a><span data-ttu-id="2d4af-102">&lt;discoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="2d4af-102">&lt;discoveryEndpoint&gt;</span></span>

<span data-ttu-id="2d4af-103">この構成要素は、固定探索コントラクトが含まれた標準エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="2d4af-103">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="2d4af-104">サービスの構成に追加すると、この要素により、探索メッセージをリッスンする場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2d4af-104">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="2d4af-105">クライアントの構成に追加すると、この要素により、探索クエリの送信先となる場所が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2d4af-105">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="2d4af-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2d4af-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2d4af-107">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2d4af-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4af-108">構文</span><span class="sxs-lookup"><span data-stu-id="2d4af-108">Syntax</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed" 
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxResponseDelay="Timespan" 
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d4af-109">属性と要素</span><span class="sxs-lookup"><span data-stu-id="2d4af-109">Attributes and elements</span></span>

<span data-ttu-id="2d4af-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d4af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d4af-111">属性</span><span class="sxs-lookup"><span data-stu-id="2d4af-111">Attributes</span></span>

| <span data-ttu-id="2d4af-112">属性</span><span class="sxs-lookup"><span data-stu-id="2d4af-112">Attribute</span></span>        | <span data-ttu-id="2d4af-113">説明</span><span class="sxs-lookup"><span data-stu-id="2d4af-113">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="2d4af-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="2d4af-114">discoveryMode</span></span>    | <span data-ttu-id="2d4af-115">探索プロトコルのモードを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="2d4af-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="2d4af-116">有効な値は"Adhoc"と"Managed です"。</span><span class="sxs-lookup"><span data-stu-id="2d4af-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="2d4af-117">マネージ モードでは、プロトコルは Discoverable サービスのリポジトリとして機能する Discovery Proxy に依存します。</span><span class="sxs-lookup"><span data-stu-id="2d4af-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="2d4af-118">アドホック モードでは、プロトコルは UDP マルチキャスト メカニズムを使用して利用可能なサービスを探索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d4af-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="2d4af-119">プロパティの詳細については、次を参照してください。<xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>です。</span><span class="sxs-lookup"><span data-stu-id="2d4af-119">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="2d4af-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="2d4af-120">discoveryVersion</span></span> | <span data-ttu-id="2d4af-121">WS-Discovery プロトコルの 2 つのバージョンのうち、1 つを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2d4af-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="2d4af-122">有効値は WSDiscovery11 と WSDiscoveryApril2005 です。</span><span class="sxs-lookup"><span data-stu-id="2d4af-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="2d4af-123">この値は、<xref:System.ServiceModel.Discovery.DiscoveryVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="2d4af-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="2d4af-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="2d4af-124">maxResponseDelay</span></span> | <span data-ttu-id="2d4af-125">Discovery プロトコルが Probe Match や Resolve Match などのメッセージを送信するまでの待機時間の最大値を指定する Timespan 値。</span><span class="sxs-lookup"><span data-stu-id="2d4af-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="2d4af-126">すべての ProbeMatch が同時に送信されると、ネットワーク ストームが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2d4af-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="2d4af-127">これを防ぐために、各 ProbeMatch はランダムな時間だけ待機して送信されます。</span><span class="sxs-lookup"><span data-stu-id="2d4af-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="2d4af-128">ランダムな待機時間は、0 からこの属性に設定された値の範囲内で設定されます。</span><span class="sxs-lookup"><span data-stu-id="2d4af-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="2d4af-129">この属性を 0 に設定すると、ProbeMatch メッセージは待機せずに短いループで送信されます。</span><span class="sxs-lookup"><span data-stu-id="2d4af-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="2d4af-130">それ以外の場合は、ProbeMatch メッセージはランダムな時間だけ待機して送信されます。すべての ProbeMatch メッセージの送信にかかる合計時間が maxResponseDelay を超えることはありません。</span><span class="sxs-lookup"><span data-stu-id="2d4af-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="2d4af-131">この値はサービスのみに関連するもので、クライアントが使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="2d4af-131">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="2d4af-132">標準エンドポイントの構成名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2d4af-132">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="2d4af-133">この名前は、サービス エンドポイントの `endpointConfiguration` 属性で使用され、標準エンドポイントと構成を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="2d4af-133">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="2d4af-134">子要素</span><span class="sxs-lookup"><span data-stu-id="2d4af-134">Child elements</span></span>

<span data-ttu-id="2d4af-135">なし。</span><span class="sxs-lookup"><span data-stu-id="2d4af-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d4af-136">親要素</span><span class="sxs-lookup"><span data-stu-id="2d4af-136">Parent elements</span></span>

| <span data-ttu-id="2d4af-137">要素</span><span class="sxs-lookup"><span data-stu-id="2d4af-137">Element</span></span> | <span data-ttu-id="2d4af-138">説明</span><span class="sxs-lookup"><span data-stu-id="2d4af-138">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="2d4af-139">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="2d4af-139">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | <span data-ttu-id="2d4af-140">1 つ以上のプロパティ (アドレス、バインディング、コントラクト) が固定されている、あらかじめ定義されたエンドポイントである標準エンドポイントのコレクション。</span><span class="sxs-lookup"><span data-stu-id="2d4af-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="2d4af-141">例</span><span class="sxs-lookup"><span data-stu-id="2d4af-141">Example</span></span>

<span data-ttu-id="2d4af-142">ピア ネットワーク マルチキャスト トランスポート経由で探索メッセージをリッスンするサービスの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2d4af-142">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="2d4af-143">この例では、明示的に WS-Discovery April 2005 バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="2d4af-143">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="2d4af-144">標準エンドポイントの構成はサービスごとに定義します。サービス間で共有することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d4af-144">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="2d4af-145">別のサービスで同じ探索エンドポイントを使用するには、該当のサービスのセクションに同じ構成を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d4af-145">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml
<services>  
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding" 
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="peerNetDiscovery"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              kind="discoveryEndpoint"  
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />      
  </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"                         
                      version="WSDiscoveryApril2005" />  
  </discoveryEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d4af-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d4af-146">See also</span></span>

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
