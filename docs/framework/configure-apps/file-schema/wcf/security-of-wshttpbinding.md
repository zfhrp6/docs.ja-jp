---
title: '&lt;wsHttpBinding&gt; の &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 836e920ef7c95d4a7a2b752c2f76f29d8c880e7c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="45c74-102">&lt;wsHttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="45c74-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="45c74-103">セキュリティ機能を表す、 [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="45c74-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="45c74-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="45c74-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="45c74-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="45c74-105">\<bindings></span></span>  
<span data-ttu-id="45c74-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="45c74-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="45c74-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="45c74-107">\<binding></span></span>  
<span data-ttu-id="45c74-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="45c74-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45c74-109">構文</span><span class="sxs-lookup"><span data-stu-id="45c74-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45c74-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="45c74-110">Attributes and Elements</span></span>  
 <span data-ttu-id="45c74-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="45c74-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45c74-112">属性</span><span class="sxs-lookup"><span data-stu-id="45c74-112">Attributes</span></span>  
  
|<span data-ttu-id="45c74-113">属性</span><span class="sxs-lookup"><span data-stu-id="45c74-113">Attribute</span></span>|<span data-ttu-id="45c74-114">説明</span><span class="sxs-lookup"><span data-stu-id="45c74-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45c74-115">モード</span><span class="sxs-lookup"><span data-stu-id="45c74-115">mode</span></span>|<span data-ttu-id="45c74-116">-省略可能です。</span><span class="sxs-lookup"><span data-stu-id="45c74-116">-   Optional.</span></span> <span data-ttu-id="45c74-117">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="45c74-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="45c74-118">既定値は、`Message` です。</span><span class="sxs-lookup"><span data-stu-id="45c74-118">The default is `Message`.</span></span><br /><span data-ttu-id="45c74-119">-この属性は型<xref:System.ServiceModel.SecurityMode>です。</span><span class="sxs-lookup"><span data-stu-id="45c74-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="45c74-120">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="45c74-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="45c74-121">値</span><span class="sxs-lookup"><span data-stu-id="45c74-121">Value</span></span>|<span data-ttu-id="45c74-122">説明</span><span class="sxs-lookup"><span data-stu-id="45c74-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45c74-123">なし</span><span class="sxs-lookup"><span data-stu-id="45c74-123">None</span></span>|<span data-ttu-id="45c74-124">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="45c74-124">Security is disabled.</span></span>|  
|<span data-ttu-id="45c74-125">Transport</span><span class="sxs-lookup"><span data-stu-id="45c74-125">Transport</span></span>|<span data-ttu-id="45c74-126">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="45c74-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="45c74-127">サービスは、SSL 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45c74-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="45c74-128">メッセージは、HTTPS を使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="45c74-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="45c74-129">クライアント認証は、`ClientCredentials` 属性を使用して制御されます。</span><span class="sxs-lookup"><span data-stu-id="45c74-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="45c74-130">[\<トランスポート >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="45c74-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="45c74-131">メッセージ</span><span class="sxs-lookup"><span data-stu-id="45c74-131">Message</span></span>|<span data-ttu-id="45c74-132">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="45c74-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="45c74-133">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="45c74-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="45c74-134">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、Security.Message プロパティを使用してメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="45c74-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="45c74-135">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="45c74-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="45c74-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="45c74-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="45c74-137">このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="45c74-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="45c74-138">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="45c74-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45c74-139">子要素</span><span class="sxs-lookup"><span data-stu-id="45c74-139">Child Elements</span></span>  
  
|<span data-ttu-id="45c74-140">要素</span><span class="sxs-lookup"><span data-stu-id="45c74-140">Element</span></span>|<span data-ttu-id="45c74-141">説明</span><span class="sxs-lookup"><span data-stu-id="45c74-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45c74-142">\<transport></span><span class="sxs-lookup"><span data-stu-id="45c74-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="45c74-143">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="45c74-143">Defines the transport security settings.</span></span> <span data-ttu-id="45c74-144">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="45c74-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="45c74-145">\<message></span><span class="sxs-lookup"><span data-stu-id="45c74-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="45c74-146">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="45c74-146">Defines the security settings for the message.</span></span> <span data-ttu-id="45c74-147">この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="45c74-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45c74-148">親要素</span><span class="sxs-lookup"><span data-stu-id="45c74-148">Parent Elements</span></span>  
  
|<span data-ttu-id="45c74-149">要素</span><span class="sxs-lookup"><span data-stu-id="45c74-149">Element</span></span>|<span data-ttu-id="45c74-150">説明</span><span class="sxs-lookup"><span data-stu-id="45c74-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45c74-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="45c74-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="45c74-152">HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。</span><span class="sxs-lookup"><span data-stu-id="45c74-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45c74-153">コメント</span><span class="sxs-lookup"><span data-stu-id="45c74-153">Remarks</span></span>  
 <span data-ttu-id="45c74-154">WSHttpBinding クラスは、WS-\* 仕様を実装するサービスと相互運用するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="45c74-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="45c74-155">このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。</span><span class="sxs-lookup"><span data-stu-id="45c74-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c74-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="45c74-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="45c74-157">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="45c74-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="45c74-158">バインディング</span><span class="sxs-lookup"><span data-stu-id="45c74-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="45c74-159">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="45c74-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="45c74-160">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="45c74-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="45c74-161">\<binding></span><span class="sxs-lookup"><span data-stu-id="45c74-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
