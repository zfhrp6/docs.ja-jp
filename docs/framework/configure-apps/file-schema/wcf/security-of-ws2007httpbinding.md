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
ms.openlocfilehash: 78a87add1ed71786dd0e4181c7eeb70e3b63cec1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="6af8e-102">&lt;ws2007HttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="6af8e-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="6af8e-103">使用されるセキュリティ設定を表す、 [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="6af8e-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="6af8e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6af8e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6af8e-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6af8e-105">\<bindings></span></span>  
<span data-ttu-id="6af8e-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6af8e-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="6af8e-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6af8e-107">\<binding></span></span>  
<span data-ttu-id="6af8e-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="6af8e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af8e-109">構文</span><span class="sxs-lookup"><span data-stu-id="6af8e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6af8e-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6af8e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6af8e-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6af8e-112">属性</span><span class="sxs-lookup"><span data-stu-id="6af8e-112">Attributes</span></span>  
  
|<span data-ttu-id="6af8e-113">属性</span><span class="sxs-lookup"><span data-stu-id="6af8e-113">Attribute</span></span>|<span data-ttu-id="6af8e-114">説明</span><span class="sxs-lookup"><span data-stu-id="6af8e-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6af8e-115">-省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6af8e-115">-   Optional.</span></span> <span data-ttu-id="6af8e-116">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6af8e-117">既定値は、`Message` です。</span><span class="sxs-lookup"><span data-stu-id="6af8e-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="6af8e-118">この属性は <xref:System.ServiceModel.SecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="6af8e-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6af8e-119">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="6af8e-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="6af8e-120">値</span><span class="sxs-lookup"><span data-stu-id="6af8e-120">Value</span></span>|<span data-ttu-id="6af8e-121">説明</span><span class="sxs-lookup"><span data-stu-id="6af8e-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6af8e-122">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6af8e-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="6af8e-123">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="6af8e-124">サービスは、Secure Sockets Layer (SSL) 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6af8e-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="6af8e-125">メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="6af8e-126">クライアントの認証はによって制御されます、`ClientCredentials`の属性、 [\<トランスポート >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="6af8e-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="6af8e-127">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6af8e-128">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="6af8e-129">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、<xref:System.ServiceModel.Security.SecurityMessageProperty> によってメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="6af8e-130">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="6af8e-131">このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="6af8e-132">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6af8e-133">子要素</span><span class="sxs-lookup"><span data-stu-id="6af8e-133">Child Elements</span></span>  
  
|<span data-ttu-id="6af8e-134">要素</span><span class="sxs-lookup"><span data-stu-id="6af8e-134">Element</span></span>|<span data-ttu-id="6af8e-135">説明</span><span class="sxs-lookup"><span data-stu-id="6af8e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6af8e-136">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="6af8e-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="6af8e-137">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-137">Defines the transport security settings.</span></span> <span data-ttu-id="6af8e-138">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="6af8e-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="6af8e-139">これらの設定は、モードが Transport に設定されている場合のみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="6af8e-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="6af8e-140">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="6af8e-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="6af8e-141">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-141">Defines the security settings for the message.</span></span> <span data-ttu-id="6af8e-142">この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="6af8e-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="6af8e-143">これらの設定は、モードが Transport に設定されている場合は適用されません。</span><span class="sxs-lookup"><span data-stu-id="6af8e-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6af8e-144">親要素</span><span class="sxs-lookup"><span data-stu-id="6af8e-144">Parent Elements</span></span>  
  
|<span data-ttu-id="6af8e-145">要素</span><span class="sxs-lookup"><span data-stu-id="6af8e-145">Element</span></span>|<span data-ttu-id="6af8e-146">説明</span><span class="sxs-lookup"><span data-stu-id="6af8e-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6af8e-147">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6af8e-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="6af8e-148">HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。</span><span class="sxs-lookup"><span data-stu-id="6af8e-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6af8e-149">コメント</span><span class="sxs-lookup"><span data-stu-id="6af8e-149">Remarks</span></span>  
 <span data-ttu-id="6af8e-150">この要素は、WS-* 仕様を実装するサービスと相互運用するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="6af8e-150">This element is designed for interoperation with services that implement WS-* specifications.</span></span> <span data-ttu-id="6af8e-151">このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。</span><span class="sxs-lookup"><span data-stu-id="6af8e-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af8e-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="6af8e-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="6af8e-153">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6af8e-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6af8e-154">バインディング</span><span class="sxs-lookup"><span data-stu-id="6af8e-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6af8e-155">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="6af8e-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6af8e-156">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="6af8e-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6af8e-157">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6af8e-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
