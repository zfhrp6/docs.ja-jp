---
title: '&lt;mexHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 759f28330bf54fb7be2f9f9ad67b4e45499b03bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="39eef-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="39eef-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="39eef-103">HTTPS 経由の WS-MetadataExchange (WS-MEX) メッセージ交換に使用されるバインディングの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="39eef-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="39eef-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="39eef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39eef-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="39eef-105">\<bindings></span></span>  
<span data-ttu-id="39eef-106">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="39eef-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39eef-107">構文</span><span class="sxs-lookup"><span data-stu-id="39eef-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39eef-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="39eef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39eef-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="39eef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39eef-110">属性</span><span class="sxs-lookup"><span data-stu-id="39eef-110">Attributes</span></span>  
  
|<span data-ttu-id="39eef-111">属性</span><span class="sxs-lookup"><span data-stu-id="39eef-111">Attribute</span></span>|<span data-ttu-id="39eef-112">説明</span><span class="sxs-lookup"><span data-stu-id="39eef-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="39eef-113">クローズ操作が完了するまでの期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="39eef-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="39eef-114">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39eef-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39eef-115">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="39eef-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="39eef-116">バインディングの構成名を格納する文字列です。</span><span class="sxs-lookup"><span data-stu-id="39eef-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="39eef-117">この値は、バインディングの ID として使用されるため、一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39eef-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="39eef-118">各バインドには、サービスのメタデータでこれをまとめて一意に識別する `name` および `namespace` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39eef-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="39eef-119">また、この名前は、同じ種類のバインディング間で一意です。</span><span class="sxs-lookup"><span data-stu-id="39eef-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="39eef-120">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39eef-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="39eef-121">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="39eef-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="39eef-122">実行中の操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="39eef-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="39eef-123">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39eef-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39eef-124">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="39eef-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="39eef-125">受信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="39eef-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="39eef-126">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39eef-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39eef-127">既定値は 00:10:00 です。</span><span class="sxs-lookup"><span data-stu-id="39eef-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="39eef-128">送信操作が完了するまでの時間間隔を指定する <xref:System.TimeSpan> 値です。</span><span class="sxs-lookup"><span data-stu-id="39eef-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="39eef-129">この値は必ず <xref:System.TimeSpan.Zero> 以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39eef-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39eef-130">既定値は 00:01:00 です。</span><span class="sxs-lookup"><span data-stu-id="39eef-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39eef-131">子要素</span><span class="sxs-lookup"><span data-stu-id="39eef-131">Child Elements</span></span>  
 <span data-ttu-id="39eef-132">なし。</span><span class="sxs-lookup"><span data-stu-id="39eef-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39eef-133">親要素</span><span class="sxs-lookup"><span data-stu-id="39eef-133">Parent Elements</span></span>  
  
|<span data-ttu-id="39eef-134">要素</span><span class="sxs-lookup"><span data-stu-id="39eef-134">Element</span></span>|<span data-ttu-id="39eef-135">説明</span><span class="sxs-lookup"><span data-stu-id="39eef-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39eef-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="39eef-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="39eef-137">この要素には、標準バインディングおよびカスタム バインドのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="39eef-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39eef-138">コメント</span><span class="sxs-lookup"><span data-stu-id="39eef-138">Remarks</span></span>  
 <span data-ttu-id="39eef-139">このバインディングは、基本的には証明書を使用してトランスポート レベルのセキュリティをサポートする `WSHttpBinding` バインディングです。</span><span class="sxs-lookup"><span data-stu-id="39eef-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="39eef-140">構成して、このようなメタデータ エンドポイントを使用しての詳細については、次を参照してください。[する方法: カスタム Ws-metadata Exchange バインディングを構成する](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)、[する方法: 取得メタデータ経由で、MEX 以外のバインディング](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)、サンプルとサンプル[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)です。</span><span class="sxs-lookup"><span data-stu-id="39eef-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39eef-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="39eef-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="39eef-142">方法 : 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="39eef-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="39eef-143">カスタム バインディングを介したメタデータの公開と取得</span><span class="sxs-lookup"><span data-stu-id="39eef-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="39eef-144">方法 : カスタム WS-Metadata Exchange バインディングを構成する</span><span class="sxs-lookup"><span data-stu-id="39eef-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="39eef-145">方法 : MEX 以外のバインディングを介してメタデータを取得する</span><span class="sxs-lookup"><span data-stu-id="39eef-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="39eef-146">カスタム セキュア メタデータ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="39eef-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="39eef-147">メタデータ</span><span class="sxs-lookup"><span data-stu-id="39eef-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="39eef-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="39eef-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="39eef-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="39eef-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="39eef-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="39eef-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="39eef-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="39eef-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
