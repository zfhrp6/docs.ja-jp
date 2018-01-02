---
title: '&lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb60d901d498c6db194e60a9229c0d5b69eee31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="92af6-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="92af6-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="92af6-103">カスタム バインドのピア トランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="92af6-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="92af6-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="92af6-104">\<system.serviceModel></span></span>  
<span data-ttu-id="92af6-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="92af6-105">\<bindings></span></span>  
<span data-ttu-id="92af6-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="92af6-106">\<customBinding></span></span>  
<span data-ttu-id="92af6-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="92af6-107">\<binding></span></span>  
<span data-ttu-id="92af6-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="92af6-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92af6-109">構文</span><span class="sxs-lookup"><span data-stu-id="92af6-109">Syntax</span></span>  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92af6-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="92af6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="92af6-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="92af6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92af6-112">属性</span><span class="sxs-lookup"><span data-stu-id="92af6-112">Attributes</span></span>  
  
|<span data-ttu-id="92af6-113">属性</span><span class="sxs-lookup"><span data-stu-id="92af6-113">Attribute</span></span>|<span data-ttu-id="92af6-114">説明</span><span class="sxs-lookup"><span data-stu-id="92af6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92af6-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="92af6-115">listenIpAddress</span></span>|<span data-ttu-id="92af6-116">ピア ノードが TCP メッセージをリッスンする IP アドレスを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="92af6-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="92af6-117">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="92af6-117">The default is `null`.</span></span>|  
|<span data-ttu-id="92af6-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="92af6-118">maxBufferPoolSize</span></span>|<span data-ttu-id="92af6-119">バッファー プールの最大サイズを指定する正の整数です。</span><span class="sxs-lookup"><span data-stu-id="92af6-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="92af6-120">既定値は 524288 です。</span><span class="sxs-lookup"><span data-stu-id="92af6-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="92af6-121">WCF の多くの部分でバッファーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="92af6-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="92af6-122">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="92af6-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="92af6-123">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="92af6-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="92af6-124">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="92af6-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="92af6-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="92af6-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="92af6-126">ヘッダーなどのメッセージの最大サイズ (バイト単位) を定義する正の整数。</span><span class="sxs-lookup"><span data-stu-id="92af6-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="92af6-127">受信側にとってメッセージが大きすぎると、メッセージの送信側は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="92af6-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="92af6-128">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="92af6-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="92af6-129">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="92af6-129">The default is 65536.</span></span>|  
|<span data-ttu-id="92af6-130">ポート</span><span class="sxs-lookup"><span data-stu-id="92af6-130">port</span></span>|<span data-ttu-id="92af6-131">このバインディングがピア チャネルの TCP メッセージを処理するネットワーク インターフェイス ポートを指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="92af6-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="92af6-132">この値の有効値の範囲は <xref:System.Net.IPEndPoint.MinPort> ～ <xref:System.Net.IPEndPoint.MaxPort> です。</span><span class="sxs-lookup"><span data-stu-id="92af6-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="92af6-133">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="92af6-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92af6-134">子要素</span><span class="sxs-lookup"><span data-stu-id="92af6-134">Child Elements</span></span>  
  
|<span data-ttu-id="92af6-135">要素</span><span class="sxs-lookup"><span data-stu-id="92af6-135">Element</span></span>|<span data-ttu-id="92af6-136">説明</span><span class="sxs-lookup"><span data-stu-id="92af6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92af6-137">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="92af6-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="92af6-138">このトランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="92af6-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="92af6-139">この要素は <xref:System.ServiceModel.Configuration.PeerSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="92af6-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92af6-140">親要素</span><span class="sxs-lookup"><span data-stu-id="92af6-140">Parent Elements</span></span>  
  
|<span data-ttu-id="92af6-141">要素</span><span class="sxs-lookup"><span data-stu-id="92af6-141">Element</span></span>|<span data-ttu-id="92af6-142">説明</span><span class="sxs-lookup"><span data-stu-id="92af6-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92af6-143">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="92af6-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="92af6-144">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="92af6-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92af6-145">コメント</span><span class="sxs-lookup"><span data-stu-id="92af6-145">Remarks</span></span>  
 <span data-ttu-id="92af6-146">このトランスポートは、要求/応答操作を含むコントラクトと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="92af6-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92af6-147">参照</span><span class="sxs-lookup"><span data-stu-id="92af6-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="92af6-148">トランスポート</span><span class="sxs-lookup"><span data-stu-id="92af6-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="92af6-149">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="92af6-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="92af6-150">バインディング</span><span class="sxs-lookup"><span data-stu-id="92af6-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="92af6-151">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="92af6-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="92af6-152">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="92af6-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="92af6-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="92af6-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
