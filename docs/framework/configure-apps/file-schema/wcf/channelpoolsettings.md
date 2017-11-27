---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44e79c7af470cefead8bcfb0ef96606ecde30383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="8c057-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="8c057-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="8c057-103">カスタム バインドのチャネル プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="8c057-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="8c057-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8c057-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8c057-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8c057-105">\<bindings></span></span>  
<span data-ttu-id="8c057-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c057-106">\<customBinding></span></span>  
<span data-ttu-id="8c057-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="8c057-107">\<binding></span></span>  
<span data-ttu-id="8c057-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="8c057-108">\<oneWay></span></span>  
<span data-ttu-id="8c057-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="8c057-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c057-110">構文</span><span class="sxs-lookup"><span data-stu-id="8c057-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c057-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8c057-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8c057-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c057-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c057-113">属性</span><span class="sxs-lookup"><span data-stu-id="8c057-113">Attributes</span></span>  
  
|<span data-ttu-id="8c057-114">属性</span><span class="sxs-lookup"><span data-stu-id="8c057-114">Attribute</span></span>|<span data-ttu-id="8c057-115">説明</span><span class="sxs-lookup"><span data-stu-id="8c057-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="8c057-116">プール内のチャネルの接続が切断されるまでの最大アイドル時間を指定する正の <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c057-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="8c057-117">既定値は 00:02:00 です。</span><span class="sxs-lookup"><span data-stu-id="8c057-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="8c057-118">プールに返されたチャネルが閉じられるまでの時間を指定する <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="8c057-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="8c057-119">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="8c057-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="8c057-120">各リモート エンドポイントのプール内に格納できるチャネルの最大数を指定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="8c057-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="8c057-121">既定値は 10 です。</span><span class="sxs-lookup"><span data-stu-id="8c057-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c057-122">子要素</span><span class="sxs-lookup"><span data-stu-id="8c057-122">Child Elements</span></span>  
 <span data-ttu-id="8c057-123">なし。</span><span class="sxs-lookup"><span data-stu-id="8c057-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c057-124">親要素</span><span class="sxs-lookup"><span data-stu-id="8c057-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8c057-125">要素</span><span class="sxs-lookup"><span data-stu-id="8c057-125">Element</span></span>|<span data-ttu-id="8c057-126">説明</span><span class="sxs-lookup"><span data-stu-id="8c057-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c057-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="8c057-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="8c057-128">カスタム バインドでパケット ルーティングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8c057-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c057-129">コメント</span><span class="sxs-lookup"><span data-stu-id="8c057-129">Remarks</span></span>  
 <span data-ttu-id="8c057-130">クォータは、リソースの過剰な消費を防ぐためのポリシー メカニズムとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c057-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="8c057-131">クォータは、悪質な、または意図的でないサービス拒否 (DOS) 攻撃を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="8c057-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="8c057-132">カスタム チャネルにチャネル クォータを設定するには、この要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="8c057-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="8c057-133">`ChannelPoolSettings` では、次の 3 つのクォータを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c057-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="8c057-134">`idleTimeout` クォータは、サーバーでは、長時間リソースを停滞させることによるサービス拒否 (DOS) 攻撃を軽減するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c057-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="8c057-135">クライアントでは、適切な値を設定することで、サービスとの接続の信頼性を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="8c057-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="8c057-136">既定値では、リソースが控えめに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="8c057-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="8c057-137">開発環境、および小規模のインストール シナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="8c057-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="8c057-138">インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c057-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="8c057-139">`leaseTimeout` クォータは、負荷分散機能との統合、および信頼性の向上のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c057-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="8c057-140">既定値では、リソースが控えめに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="8c057-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="8c057-141">開発環境、および小規模のインストール シナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="8c057-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="8c057-142">インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c057-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="8c057-143">`maxOutboundChannelsPerEndpoint` クォータは、サーバーとクライアントの両方に対するキャッシュ制限を設定し、信頼性向上のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c057-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="8c057-144">既定値ではリソースが控えめに割り当てられており、開発環境および小規模なインストール シナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="8c057-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="8c057-145">インストールでリソースが不足している場合、または追加リソースが使用可能であるにもかかわらず接続が制限されている場合、サービス管理者は値をレビューする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c057-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c057-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c057-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8c057-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="8c057-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="8c057-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="8c057-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8c057-149">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="8c057-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8c057-150">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="8c057-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8c057-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8c057-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
