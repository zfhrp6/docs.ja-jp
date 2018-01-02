---
title: "&lt;ws2007HttpBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 355fa3a7031c9650d52d258b9d5ef67b291e6e17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="154d7-102">&lt;ws2007HttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="154d7-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="154d7-103">使用されるセキュリティ設定を表す、 [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="154d7-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="154d7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="154d7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="154d7-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="154d7-105">\<bindings></span></span>  
<span data-ttu-id="154d7-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="154d7-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="154d7-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="154d7-107">\<binding></span></span>  
<span data-ttu-id="154d7-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="154d7-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="154d7-109">構文</span><span class="sxs-lookup"><span data-stu-id="154d7-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="154d7-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="154d7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="154d7-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="154d7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="154d7-112">属性</span><span class="sxs-lookup"><span data-stu-id="154d7-112">Attributes</span></span>  
  
|<span data-ttu-id="154d7-113">属性</span><span class="sxs-lookup"><span data-stu-id="154d7-113">Attribute</span></span>|<span data-ttu-id="154d7-114">説明</span><span class="sxs-lookup"><span data-stu-id="154d7-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="154d7-115">-省略可能です。</span><span class="sxs-lookup"><span data-stu-id="154d7-115">-   Optional.</span></span> <span data-ttu-id="154d7-116">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="154d7-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="154d7-117">既定値は、`Message` です。</span><span class="sxs-lookup"><span data-stu-id="154d7-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="154d7-118">この属性は <xref:System.ServiceModel.SecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="154d7-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="154d7-119">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="154d7-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="154d7-120">値</span><span class="sxs-lookup"><span data-stu-id="154d7-120">Value</span></span>|<span data-ttu-id="154d7-121">説明</span><span class="sxs-lookup"><span data-stu-id="154d7-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="154d7-122">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="154d7-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="154d7-123">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="154d7-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="154d7-124">サービスは、Secure Sockets Layer (SSL) 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="154d7-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="154d7-125">メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="154d7-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="154d7-126">クライアントの認証はによって制御されます、`ClientCredentials`の属性、 [\<トランスポート >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="154d7-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="154d7-127">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="154d7-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="154d7-128">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="154d7-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="154d7-129">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、<xref:System.ServiceModel.Security.SecurityMessageProperty> によってメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="154d7-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="154d7-130">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="154d7-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="154d7-131">このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="154d7-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="154d7-132">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="154d7-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="154d7-133">子要素</span><span class="sxs-lookup"><span data-stu-id="154d7-133">Child Elements</span></span>  
  
|<span data-ttu-id="154d7-134">要素</span><span class="sxs-lookup"><span data-stu-id="154d7-134">Element</span></span>|<span data-ttu-id="154d7-135">説明</span><span class="sxs-lookup"><span data-stu-id="154d7-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="154d7-136">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="154d7-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="154d7-137">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="154d7-137">Defines the transport security settings.</span></span> <span data-ttu-id="154d7-138">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="154d7-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="154d7-139">これらの設定は、モードが Transport に設定されている場合のみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="154d7-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="154d7-140">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="154d7-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="154d7-141">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="154d7-141">Defines the security settings for the message.</span></span> <span data-ttu-id="154d7-142">この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="154d7-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="154d7-143">これらの設定は、モードが Transport に設定されている場合は適用されません。</span><span class="sxs-lookup"><span data-stu-id="154d7-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="154d7-144">親要素</span><span class="sxs-lookup"><span data-stu-id="154d7-144">Parent Elements</span></span>  
  
|<span data-ttu-id="154d7-145">要素</span><span class="sxs-lookup"><span data-stu-id="154d7-145">Element</span></span>|<span data-ttu-id="154d7-146">説明</span><span class="sxs-lookup"><span data-stu-id="154d7-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="154d7-147">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="154d7-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="154d7-148">HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。</span><span class="sxs-lookup"><span data-stu-id="154d7-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="154d7-149">コメント</span><span class="sxs-lookup"><span data-stu-id="154d7-149">Remarks</span></span>  
 <span data-ttu-id="154d7-150">この要素は、WS-* 仕様を実装するサービスと相互運用するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="154d7-150">This element is designed for interoperation with services that implement WS-* specifications.</span></span> <span data-ttu-id="154d7-151">このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。</span><span class="sxs-lookup"><span data-stu-id="154d7-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="154d7-152">参照</span><span class="sxs-lookup"><span data-stu-id="154d7-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="154d7-153">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="154d7-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="154d7-154">バインディング</span><span class="sxs-lookup"><span data-stu-id="154d7-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="154d7-155">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="154d7-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="154d7-156">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="154d7-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="154d7-157">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="154d7-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
