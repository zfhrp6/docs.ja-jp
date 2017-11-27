---
title: '&lt;namedPipeTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d2d4be08012c1d33341ddd17713903782027c31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="2c781-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="2c781-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="2c781-103">チャネルがカスタム バインドに含まれているときに名前付きパイプを使用してメッセージを転送するトランスポートを定義します。</span><span class="sxs-lookup"><span data-stu-id="2c781-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="2c781-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2c781-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2c781-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2c781-105">\<bindings></span></span>  
<span data-ttu-id="2c781-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2c781-106">\<customBinding></span></span>  
<span data-ttu-id="2c781-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2c781-107">\<binding></span></span>  
<span data-ttu-id="2c781-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="2c781-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c781-109">構文</span><span class="sxs-lookup"><span data-stu-id="2c781-109">Syntax</span></span>  
  
```xml
<namedPipeTransport channelInitializationTimeout="TimeSpan"   
                    connectionBufferSize="Integer"   
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
                    manualAddressing="Boolean"   
                    maxBufferPoolSize="Integer"  
                    maxBufferSize="Integer"  
                    maxOutputDelay="TimeSpan"  
                    maxPendingAccepts="Integer"   
                    maxPendingConnections="Integer"  
                    maxReceivedMessageSize="Integer"   
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">  
  <connectionPoolSettings groupName="String" 
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c781-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2c781-110">Attributes and Elements</span></span>  
<span data-ttu-id="2c781-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2c781-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c781-112">属性</span><span class="sxs-lookup"><span data-stu-id="2c781-112">Attributes</span></span>  
<span data-ttu-id="2c781-113">なし。</span><span class="sxs-lookup"><span data-stu-id="2c781-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c781-114">子要素</span><span class="sxs-lookup"><span data-stu-id="2c781-114">Child Elements</span></span>  
  
|<span data-ttu-id="2c781-115">要素</span><span class="sxs-lookup"><span data-stu-id="2c781-115">Element</span></span>|<span data-ttu-id="2c781-116">説明</span><span class="sxs-lookup"><span data-stu-id="2c781-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c781-117">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="2c781-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="2c781-118">取得または設定、<xref:System.TimeSpan>チャネルが切断されるまで初期化状態にすることができます、最大時間を決定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="2c781-119">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="2c781-119">ConnectionBufferSize</span></span>|<span data-ttu-id="2c781-120">クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="2c781-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="2c781-121">hostNameComparisonMode</span></span>|<span data-ttu-id="2c781-122">URI で一致する場合にサービスに到達するためにホスト名を使用するかどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="2c781-123">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="2c781-123">manualAddressing</span></span>|<span data-ttu-id="2c781-124">メッセージの手動アドレス指定が必要かどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="2c781-125">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="2c781-125">maxBufferPoolSize</span></span>|<span data-ttu-id="2c781-126">取得または (バイト単位)、トランスポートによって使用されるバッファー プールの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="2c781-127">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="2c781-127">maxBufferSize</span></span>|<span data-ttu-id="2c781-128">使用するバッファーの最大サイズを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="2c781-129">ストリーム メッセージの場合、この値は少なくともメッセージ ヘッダーで使用できる最大サイズにする必要があります。これは、バッファー モードで読み取られます。</span><span class="sxs-lookup"><span data-stu-id="2c781-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="2c781-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="2c781-130">maxOutputDelay</span></span>|<span data-ttu-id="2c781-131">メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="2c781-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="2c781-132">maxPendingAccepts</span></span>|<span data-ttu-id="2c781-133">取得または設定、チャネルの最大数、サービスは、サービスへの着信接続を処理するためのリスナーで待機を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="2c781-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="2c781-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="2c781-134">maxPendingConnections</span></span>|<span data-ttu-id="2c781-135">サービスでディスパッチを待機している最大接続数を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="2c781-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="2c781-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="2c781-137">取得し、(バイト単位) が受信可能な最大メッセージ サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="2c781-138">transferMode</span><span class="sxs-lookup"><span data-stu-id="2c781-138">transferMode</span></span>|<span data-ttu-id="2c781-139">接続指向のトランスポートでメッセージをバッファーするか、ストリーム配信するかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="2c781-140">\<connectionPoolSettings > の\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="2c781-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="2c781-141">名前付きパイプ バインディングの追加の接続プール設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="2c781-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c781-142">親要素</span><span class="sxs-lookup"><span data-stu-id="2c781-142">Parent Elements</span></span>  
  
|<span data-ttu-id="2c781-143">要素</span><span class="sxs-lookup"><span data-stu-id="2c781-143">Element</span></span>|<span data-ttu-id="2c781-144">説明</span><span class="sxs-lookup"><span data-stu-id="2c781-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c781-145">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2c781-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2c781-146">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="2c781-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c781-147">コメント</span><span class="sxs-lookup"><span data-stu-id="2c781-147">Remarks</span></span>  
<span data-ttu-id="2c781-148">このトランスポートは、"net.pipe://hostname/path" の形式の URI を使用します。</span><span class="sxs-lookup"><span data-stu-id="2c781-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="2c781-149">他の URI コンポーネントは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2c781-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="2c781-150">`namedPipeTransport` 要素は、名前付きパイプ トランスポート プロトコルを実装するカスタム バインディングを作成する場合の開始点となります。</span><span class="sxs-lookup"><span data-stu-id="2c781-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="2c781-151">このトランスポートは、コンピューター上での WCF (Windows Communication Foundation) 間の通信に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c781-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c781-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c781-152">See Also</span></span>  
<span data-ttu-id="2c781-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span><span class="sxs-lookup"><span data-stu-id="2c781-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span></span>   
<span data-ttu-id="2c781-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="2c781-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span></span>   
<span data-ttu-id="2c781-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="2c781-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span></span>   
<span data-ttu-id="2c781-156"><xref:System.ServiceModel.Channels.CustomBinding></span><span class="sxs-lookup"><span data-stu-id="2c781-156"><xref:System.ServiceModel.Channels.CustomBinding></span></span>   
<span data-ttu-id="2c781-157">[トランスポート](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="2c781-157">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="2c781-158">[トランスポートの選択](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="2c781-158">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="2c781-159">[バインド](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="2c781-159">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="2c781-160">[バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="2c781-160">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="2c781-161">[カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="2c781-161">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="2c781-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2c781-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
