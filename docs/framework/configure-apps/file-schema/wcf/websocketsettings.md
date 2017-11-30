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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2714b27916a47ae8e002ea857c93377736c4eff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="39c8f-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="39c8f-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="39c8f-103">Web ソケット設定を指定するために使用される構成要素。</span><span class="sxs-lookup"><span data-stu-id="39c8f-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="39c8f-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39c8f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39c8f-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="39c8f-105">\<bindings></span></span>  
<span data-ttu-id="39c8f-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="39c8f-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c8f-107">構文</span><span class="sxs-lookup"><span data-stu-id="39c8f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39c8f-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="39c8f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39c8f-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39c8f-110">属性</span><span class="sxs-lookup"><span data-stu-id="39c8f-110">Attributes</span></span>  
  
|<span data-ttu-id="39c8f-111">属性</span><span class="sxs-lookup"><span data-stu-id="39c8f-111">Attribute</span></span>|<span data-ttu-id="39c8f-112">説明</span><span class="sxs-lookup"><span data-stu-id="39c8f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39c8f-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="39c8f-113">createNotificationOnConnection</span></span>|<span data-ttu-id="39c8f-114">通知を接続時に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="39c8f-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="39c8f-115">disablePayloadMasking</span></span>|<span data-ttu-id="39c8f-116">Web ソケットのマスクが無効であるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="39c8f-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="39c8f-117">keepAliveInterval</span></span>|<span data-ttu-id="39c8f-118">接続維持の間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="39c8f-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="39c8f-119">maxPendingConnections</span></span>|<span data-ttu-id="39c8f-120">サービスでのディスパッチを待機している接続の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="39c8f-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="39c8f-121">receiveBufferSize</span></span>|<span data-ttu-id="39c8f-122">受信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="39c8f-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="39c8f-123">sendBufferSize</span></span>|<span data-ttu-id="39c8f-124">送信バッファーのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="39c8f-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="39c8f-125">subProtocol</span></span>|<span data-ttu-id="39c8f-126">Web ソケットのサブプロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="39c8f-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="39c8f-127">transportUsage</span></span>|<span data-ttu-id="39c8f-128">Web ソケットを使用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="39c8f-129">transportUsage 属性</span><span class="sxs-lookup"><span data-stu-id="39c8f-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="39c8f-130">値</span><span class="sxs-lookup"><span data-stu-id="39c8f-130">Value</span></span>|<span data-ttu-id="39c8f-131">説明</span><span class="sxs-lookup"><span data-stu-id="39c8f-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39c8f-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="39c8f-132">WhenDuplex</span></span>|<span data-ttu-id="39c8f-133">コントラクトが双方向の場合に、Web ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="39c8f-134">Always</span><span class="sxs-lookup"><span data-stu-id="39c8f-134">Always</span></span>|<span data-ttu-id="39c8f-135">コントラクトにかかわらず、常にWeb ソケット プロトコルを使用します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="39c8f-136">Never</span><span class="sxs-lookup"><span data-stu-id="39c8f-136">Never</span></span>|<span data-ttu-id="39c8f-137">Web ソケット プロトコルを使用しません。</span><span class="sxs-lookup"><span data-stu-id="39c8f-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39c8f-138">子要素</span><span class="sxs-lookup"><span data-stu-id="39c8f-138">Child Elements</span></span>  
 <span data-ttu-id="39c8f-139">なし</span><span class="sxs-lookup"><span data-stu-id="39c8f-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39c8f-140">親要素</span><span class="sxs-lookup"><span data-stu-id="39c8f-140">Parent Elements</span></span>  
  
|<span data-ttu-id="39c8f-141">要素</span><span class="sxs-lookup"><span data-stu-id="39c8f-141">Element</span></span>|<span data-ttu-id="39c8f-142">説明</span><span class="sxs-lookup"><span data-stu-id="39c8f-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39c8f-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="39c8f-143">\<netHttpBinding></span></span>|<span data-ttu-id="39c8f-144">NetHttpBinding を指定します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39c8f-145">例</span><span class="sxs-lookup"><span data-stu-id="39c8f-145">Example</span></span>  
 <span data-ttu-id="39c8f-146">次の例を使用する方法を示しています、 \<webSocketSettings > 要素。</span><span class="sxs-lookup"><span data-stu-id="39c8f-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39c8f-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="39c8f-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="39c8f-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="39c8f-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="39c8f-149">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="39c8f-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="39c8f-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="39c8f-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="39c8f-151">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="39c8f-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
