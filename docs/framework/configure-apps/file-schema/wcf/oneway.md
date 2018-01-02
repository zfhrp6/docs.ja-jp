---
title: "&lt;一方向&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1436bc0c1708649378ec6747aed9c23cfc1744dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltonewaygt"></a><span data-ttu-id="91a8e-102">&lt;一方向&gt;</span><span class="sxs-lookup"><span data-stu-id="91a8e-102">&lt;oneWay&gt;</span></span>
<span data-ttu-id="91a8e-103">カスタム バインドのパケット ルーティングを有効にし、一方向メソッドを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="91a8e-103">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
 <span data-ttu-id="91a8e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="91a8e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="91a8e-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="91a8e-105">\<bindings></span></span>  
<span data-ttu-id="91a8e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="91a8e-106">\<customBinding></span></span>  
<span data-ttu-id="91a8e-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="91a8e-107">\<binding></span></span>  
<span data-ttu-id="91a8e-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="91a8e-108">\<oneWay></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a8e-109">構文</span><span class="sxs-lookup"><span data-stu-id="91a8e-109">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
```xml  
</oneWay>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91a8e-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="91a8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="91a8e-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="91a8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91a8e-112">属性</span><span class="sxs-lookup"><span data-stu-id="91a8e-112">Attributes</span></span>  
  
|<span data-ttu-id="91a8e-113">属性</span><span class="sxs-lookup"><span data-stu-id="91a8e-113">Attribute</span></span>|<span data-ttu-id="91a8e-114">説明</span><span class="sxs-lookup"><span data-stu-id="91a8e-114">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="91a8e-115">パケット ルーティングが有効かどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="91a8e-115">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="91a8e-116">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="91a8e-116">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="91a8e-117">許容できるチャネルの最大数を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="91a8e-117">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91a8e-118">子要素</span><span class="sxs-lookup"><span data-stu-id="91a8e-118">Child Elements</span></span>  
  
|<span data-ttu-id="91a8e-119">要素</span><span class="sxs-lookup"><span data-stu-id="91a8e-119">Element</span></span>|<span data-ttu-id="91a8e-120">説明</span><span class="sxs-lookup"><span data-stu-id="91a8e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91a8e-121">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="91a8e-121">\<channelPoolSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|<span data-ttu-id="91a8e-122">現在のチャネルのチャネル プールのプロパティを格納する <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="91a8e-122">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91a8e-123">親要素</span><span class="sxs-lookup"><span data-stu-id="91a8e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91a8e-124">要素</span><span class="sxs-lookup"><span data-stu-id="91a8e-124">Element</span></span>|<span data-ttu-id="91a8e-125">説明</span><span class="sxs-lookup"><span data-stu-id="91a8e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91a8e-126">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="91a8e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="91a8e-127">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="91a8e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91a8e-128">コメント</span><span class="sxs-lookup"><span data-stu-id="91a8e-128">Remarks</span></span>  
 <span data-ttu-id="91a8e-129">パケット ルーティングを有効にするには、この要素が提供する "一方向の変換" 層が必要です。</span><span class="sxs-lookup"><span data-stu-id="91a8e-129">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="91a8e-130">カスタム バインディングを作成し、このバインディングをセッション対応または要求応答のトランスポートの上に重ねて、パケット ルーティング可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="91a8e-130">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="91a8e-131">この要素は、一方向メソッドをよりネイティブな形式で公開するときにも役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="91a8e-131">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="91a8e-132">複合二重や信頼できるメッセージ機能などのさらに大きい変換は、この層に対して適用できます。</span><span class="sxs-lookup"><span data-stu-id="91a8e-132">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a8e-133">参照</span><span class="sxs-lookup"><span data-stu-id="91a8e-133">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>  
 <xref:System.ServiceModel.Configuration.OneWayElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="91a8e-134">バインディング</span><span class="sxs-lookup"><span data-stu-id="91a8e-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="91a8e-135">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="91a8e-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="91a8e-136">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="91a8e-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="91a8e-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="91a8e-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
