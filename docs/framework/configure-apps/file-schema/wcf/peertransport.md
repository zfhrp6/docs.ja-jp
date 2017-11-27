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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9c01e997e3ba804eae3036e94f2e2e1b951b25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="e61f2-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="e61f2-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="e61f2-103">カスタム バインドのピア トランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="e61f2-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="e61f2-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e61f2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e61f2-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="e61f2-105">\<bindings></span></span>  
<span data-ttu-id="e61f2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e61f2-106">\<customBinding></span></span>  
<span data-ttu-id="e61f2-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="e61f2-107">\<binding></span></span>  
<span data-ttu-id="e61f2-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="e61f2-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61f2-109">構文</span><span class="sxs-lookup"><span data-stu-id="e61f2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e61f2-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e61f2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e61f2-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e61f2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e61f2-112">属性</span><span class="sxs-lookup"><span data-stu-id="e61f2-112">Attributes</span></span>  
  
|<span data-ttu-id="e61f2-113">属性</span><span class="sxs-lookup"><span data-stu-id="e61f2-113">Attribute</span></span>|<span data-ttu-id="e61f2-114">説明</span><span class="sxs-lookup"><span data-stu-id="e61f2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e61f2-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="e61f2-115">listenIpAddress</span></span>|<span data-ttu-id="e61f2-116">ピア ノードが TCP メッセージをリッスンする IP アドレスを指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="e61f2-117">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-117">The default is `null`.</span></span>|  
|<span data-ttu-id="e61f2-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e61f2-118">maxBufferPoolSize</span></span>|<span data-ttu-id="e61f2-119">バッファー プールの最大サイズを指定する正の整数です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="e61f2-120">既定値は 524288 です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="e61f2-121">WCF の多くの部分でバッファーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e61f2-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="e61f2-122">使用するたびに毎回バッファーを作成および破壊すると負荷が高くなります。バッファーのガベージ コレクションも同様です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="e61f2-123">バッファー プールを使用すると、バッファーをプールから取得して使用し、作業が終わったらプールに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="e61f2-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="e61f2-124">これで、バッファーの作成と破棄のオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="e61f2-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="e61f2-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e61f2-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="e61f2-126">ヘッダーなどのメッセージの最大サイズ (バイト単位) を定義する正の整数。</span><span class="sxs-lookup"><span data-stu-id="e61f2-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="e61f2-127">受信側にとってメッセージが大きすぎると、メッセージの送信側は SOAP エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e61f2-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="e61f2-128">メッセージは受信者によって破棄され、トレース ログにこのイベントのエントリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e61f2-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="e61f2-129">既定値は 65536 です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-129">The default is 65536.</span></span>|  
|<span data-ttu-id="e61f2-130">ポート</span><span class="sxs-lookup"><span data-stu-id="e61f2-130">port</span></span>|<span data-ttu-id="e61f2-131">このバインディングがピア チャネルの TCP メッセージを処理するネットワーク インターフェイス ポートを指定する整数です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="e61f2-132">この値の有効値の範囲は <xref:System.Net.IPEndPoint.MinPort> ～ <xref:System.Net.IPEndPoint.MaxPort> です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="e61f2-133">既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e61f2-134">子要素</span><span class="sxs-lookup"><span data-stu-id="e61f2-134">Child Elements</span></span>  
  
|<span data-ttu-id="e61f2-135">要素</span><span class="sxs-lookup"><span data-stu-id="e61f2-135">Element</span></span>|<span data-ttu-id="e61f2-136">説明</span><span class="sxs-lookup"><span data-stu-id="e61f2-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e61f2-137">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="e61f2-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="e61f2-138">このトランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="e61f2-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="e61f2-139">この要素は <xref:System.ServiceModel.Configuration.PeerSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e61f2-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e61f2-140">親要素</span><span class="sxs-lookup"><span data-stu-id="e61f2-140">Parent Elements</span></span>  
  
|<span data-ttu-id="e61f2-141">要素</span><span class="sxs-lookup"><span data-stu-id="e61f2-141">Element</span></span>|<span data-ttu-id="e61f2-142">説明</span><span class="sxs-lookup"><span data-stu-id="e61f2-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e61f2-143">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="e61f2-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e61f2-144">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="e61f2-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e61f2-145">コメント</span><span class="sxs-lookup"><span data-stu-id="e61f2-145">Remarks</span></span>  
 <span data-ttu-id="e61f2-146">このトランスポートは、要求/応答操作を含むコントラクトと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e61f2-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61f2-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="e61f2-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="e61f2-148">トランスポート</span><span class="sxs-lookup"><span data-stu-id="e61f2-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="e61f2-149">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="e61f2-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="e61f2-150">バインディング</span><span class="sxs-lookup"><span data-stu-id="e61f2-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e61f2-151">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="e61f2-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="e61f2-152">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="e61f2-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="e61f2-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e61f2-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
