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
ms.workload: dotnet
ms.openlocfilehash: e768bf3014afa2c9205ea80fe1d101b93d36fbc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="7b77a-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7b77a-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="7b77a-103">TCP 経由の WS-MetadataExchange (WS-MEX) メッセージ交換に使用されるバインディングの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b77a-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="7b77a-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7b77a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b77a-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="7b77a-105">\<bindings></span></span>  
<span data-ttu-id="7b77a-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="7b77a-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b77a-107">構文</span><span class="sxs-lookup"><span data-stu-id="7b77a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b77a-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7b77a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7b77a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b77a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b77a-110">属性</span><span class="sxs-lookup"><span data-stu-id="7b77a-110">Attributes</span></span>  
  
|<span data-ttu-id="7b77a-111">属性</span><span class="sxs-lookup"><span data-stu-id="7b77a-111">Attribute</span></span>|<span data-ttu-id="7b77a-112">説明</span><span class="sxs-lookup"><span data-stu-id="7b77a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7b77a-113">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="7b77a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7b77a-114">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b77a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b77a-115">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="7b77a-116">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7b77a-117">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b77a-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7b77a-118">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b77a-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7b77a-119">また、この名前は、同じ種類のバインディング間で一意です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7b77a-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b77a-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7b77a-121">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7b77a-122">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7b77a-123">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b77a-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b77a-124">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7b77a-125">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7b77a-126">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b77a-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b77a-127">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7b77a-128">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7b77a-129">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b77a-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7b77a-130">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="7b77a-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b77a-131">子要素</span><span class="sxs-lookup"><span data-stu-id="7b77a-131">Child Elements</span></span>  
 <span data-ttu-id="7b77a-132">なし。</span><span class="sxs-lookup"><span data-stu-id="7b77a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b77a-133">親要素</span><span class="sxs-lookup"><span data-stu-id="7b77a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="7b77a-134">要素</span><span class="sxs-lookup"><span data-stu-id="7b77a-134">Element</span></span>|<span data-ttu-id="7b77a-135">説明</span><span class="sxs-lookup"><span data-stu-id="7b77a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b77a-136">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="7b77a-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7b77a-137">この要素には、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="7b77a-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b77a-138">参照</span><span class="sxs-lookup"><span data-stu-id="7b77a-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="7b77a-139">方法 : 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="7b77a-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="7b77a-140">カスタム バインディングを介したメタデータの公開と取得</span><span class="sxs-lookup"><span data-stu-id="7b77a-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="7b77a-141">メタデータ</span><span class="sxs-lookup"><span data-stu-id="7b77a-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="7b77a-142">バインディング</span><span class="sxs-lookup"><span data-stu-id="7b77a-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7b77a-143">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="7b77a-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7b77a-144">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="7b77a-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7b77a-145">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="7b77a-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
