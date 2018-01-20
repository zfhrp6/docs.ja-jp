---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01bc858aeeff750baa3f54e813dea5c9779143f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="ba217-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="ba217-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="ba217-103">Web ソケット設定を指定するために使用される構成要素。</span><span class="sxs-lookup"><span data-stu-id="ba217-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="ba217-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba217-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba217-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ba217-105">\<bindings></span></span>  
<span data-ttu-id="ba217-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ba217-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba217-107">構文</span><span class="sxs-lookup"><span data-stu-id="ba217-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba217-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ba217-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ba217-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba217-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba217-110">属性</span><span class="sxs-lookup"><span data-stu-id="ba217-110">Attributes</span></span>  
  
|<span data-ttu-id="ba217-111">属性</span><span class="sxs-lookup"><span data-stu-id="ba217-111">Attribute</span></span>|<span data-ttu-id="ba217-112">説明</span><span class="sxs-lookup"><span data-stu-id="ba217-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba217-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="ba217-113">createNotificationOnConnection</span></span>|<span data-ttu-id="ba217-114">通知を接続時に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="ba217-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="ba217-115">disablePayloadMasking</span></span>|<span data-ttu-id="ba217-116">Web ソケットのマスクが無効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="ba217-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="ba217-117">keepAliveInterval</span></span>|<span data-ttu-id="ba217-118">接続維持の間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="ba217-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="ba217-119">maxPendingConnections</span></span>|<span data-ttu-id="ba217-120">サービスでのディスパッチを待機している接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="ba217-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="ba217-121">receiveBufferSize</span></span>|<span data-ttu-id="ba217-122">受信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="ba217-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="ba217-123">sendBufferSize</span></span>|<span data-ttu-id="ba217-124">送信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="ba217-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="ba217-125">subProtocol</span></span>|<span data-ttu-id="ba217-126">Web ソケットのサブプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="ba217-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="ba217-127">transportUsage</span></span>|<span data-ttu-id="ba217-128">Web ソケットを使用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="ba217-129">transportUsage 属性</span><span class="sxs-lookup"><span data-stu-id="ba217-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="ba217-130">値</span><span class="sxs-lookup"><span data-stu-id="ba217-130">Value</span></span>|<span data-ttu-id="ba217-131">説明</span><span class="sxs-lookup"><span data-stu-id="ba217-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ba217-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="ba217-132">WhenDuplex</span></span>|<span data-ttu-id="ba217-133">コントラクトが双方向の場合に、Web ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba217-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="ba217-134">Always</span><span class="sxs-lookup"><span data-stu-id="ba217-134">Always</span></span>|<span data-ttu-id="ba217-135">コントラクトにかかわらず、常にWeb ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ba217-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="ba217-136">Never</span><span class="sxs-lookup"><span data-stu-id="ba217-136">Never</span></span>|<span data-ttu-id="ba217-137">Web ソケット プロトコルを使用しません。</span><span class="sxs-lookup"><span data-stu-id="ba217-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba217-138">子要素</span><span class="sxs-lookup"><span data-stu-id="ba217-138">Child Elements</span></span>  
 <span data-ttu-id="ba217-139">なし</span><span class="sxs-lookup"><span data-stu-id="ba217-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ba217-140">親要素</span><span class="sxs-lookup"><span data-stu-id="ba217-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ba217-141">要素</span><span class="sxs-lookup"><span data-stu-id="ba217-141">Element</span></span>|<span data-ttu-id="ba217-142">説明</span><span class="sxs-lookup"><span data-stu-id="ba217-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba217-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ba217-143">\<netHttpBinding></span></span>|<span data-ttu-id="ba217-144">NetHttpBinding を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba217-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ba217-145">例</span><span class="sxs-lookup"><span data-stu-id="ba217-145">Example</span></span>  
 <span data-ttu-id="ba217-146">次の例を使用する方法を示しています、 \<webSocketSettings > 要素。</span><span class="sxs-lookup"><span data-stu-id="ba217-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba217-147">参照</span><span class="sxs-lookup"><span data-stu-id="ba217-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="ba217-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="ba217-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ba217-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="ba217-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ba217-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="ba217-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ba217-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="ba217-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
