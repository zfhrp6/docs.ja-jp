---
title: '&lt;mexTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef9df72d06c598cc641d884dadbf9d4f5cee9f5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="43722-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="43722-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="43722-103">TCP 経由の WS-MetadataExchange (WS-MEX) メッセージ交換に使用されるバインディングの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="43722-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="43722-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="43722-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="43722-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="43722-105">\<bindings></span></span>  
<span data-ttu-id="43722-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="43722-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43722-107">構文</span><span class="sxs-lookup"><span data-stu-id="43722-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43722-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="43722-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43722-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="43722-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43722-110">属性</span><span class="sxs-lookup"><span data-stu-id="43722-110">Attributes</span></span>  
  
|<span data-ttu-id="43722-111">属性</span><span class="sxs-lookup"><span data-stu-id="43722-111">Attribute</span></span>|<span data-ttu-id="43722-112">説明</span><span class="sxs-lookup"><span data-stu-id="43722-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="43722-113">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="43722-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="43722-114">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="43722-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43722-115">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="43722-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="43722-116">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="43722-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="43722-117">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43722-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="43722-118">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="43722-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="43722-119">また、この名前は、同じ種類のバインディング間で一意です。</span><span class="sxs-lookup"><span data-stu-id="43722-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="43722-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="43722-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="43722-121">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="43722-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="43722-122">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="43722-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="43722-123">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="43722-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43722-124">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="43722-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="43722-125">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="43722-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="43722-126">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="43722-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43722-127">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="43722-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="43722-128">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="43722-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="43722-129">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="43722-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="43722-130">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="43722-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43722-131">子要素</span><span class="sxs-lookup"><span data-stu-id="43722-131">Child Elements</span></span>  
 <span data-ttu-id="43722-132">なし。</span><span class="sxs-lookup"><span data-stu-id="43722-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43722-133">親要素</span><span class="sxs-lookup"><span data-stu-id="43722-133">Parent Elements</span></span>  
  
|<span data-ttu-id="43722-134">要素</span><span class="sxs-lookup"><span data-stu-id="43722-134">Element</span></span>|<span data-ttu-id="43722-135">説明</span><span class="sxs-lookup"><span data-stu-id="43722-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43722-136">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="43722-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="43722-137">この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="43722-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43722-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="43722-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="43722-139">方法: 構成ファイルを使用して、サービスのメタデータを公開</span><span class="sxs-lookup"><span data-stu-id="43722-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="43722-140">公開およびカスタム バインディングを介したメタデータの取得</span><span class="sxs-lookup"><span data-stu-id="43722-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="43722-141">メタデータ</span><span class="sxs-lookup"><span data-stu-id="43722-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="43722-142">バインディング</span><span class="sxs-lookup"><span data-stu-id="43722-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="43722-143">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="43722-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="43722-144">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="43722-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="43722-145">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="43722-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
