---
title: '&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素'
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5f1a7d0ed1bffe2ca2da9318eef700b1d4924c22
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749882"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="501e8-102">&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="501e8-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="501e8-103">セキュリティ設定を定義、 [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="501e8-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="501e8-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="501e8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="501e8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="501e8-105">\<bindings></span></span>  
<span data-ttu-id="501e8-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="501e8-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="501e8-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="501e8-107">\<binding></span></span>  
<span data-ttu-id="501e8-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="501e8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="501e8-109">構文</span><span class="sxs-lookup"><span data-stu-id="501e8-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="501e8-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="501e8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="501e8-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="501e8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="501e8-112">属性</span><span class="sxs-lookup"><span data-stu-id="501e8-112">Attributes</span></span>  
  
|<span data-ttu-id="501e8-113">属性</span><span class="sxs-lookup"><span data-stu-id="501e8-113">Attribute</span></span>|<span data-ttu-id="501e8-114">説明</span><span class="sxs-lookup"><span data-stu-id="501e8-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="501e8-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="501e8-115">Optional.</span></span> <span data-ttu-id="501e8-116">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="501e8-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="501e8-117">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="501e8-117">The default value is `Message`.</span></span> <span data-ttu-id="501e8-118">この属性は <xref:System.ServiceModel.WSFederationHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="501e8-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="501e8-119">mode 属性</span><span class="sxs-lookup"><span data-stu-id="501e8-119">mode Attribute</span></span>  
  
|<span data-ttu-id="501e8-120">値</span><span class="sxs-lookup"><span data-stu-id="501e8-120">Value</span></span>|<span data-ttu-id="501e8-121">説明</span><span class="sxs-lookup"><span data-stu-id="501e8-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="501e8-122">なし</span><span class="sxs-lookup"><span data-stu-id="501e8-122">None</span></span>|<span data-ttu-id="501e8-123">SOAP メッセージは、転送中はセキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="501e8-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="501e8-124">メッセージ</span><span class="sxs-lookup"><span data-stu-id="501e8-124">Message</span></span>|<span data-ttu-id="501e8-125">SOAP メッセージ セキュリティを使用して、整合性、機密性、サーバー認証、およびクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="501e8-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="501e8-126">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="501e8-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="501e8-127">サービスは、証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="501e8-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="501e8-128">クライアント認証は、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="501e8-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="501e8-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="501e8-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="501e8-130">整合性、機密性、およびサーバー認証は、HTTPS によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="501e8-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="501e8-131">サービスは、証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="501e8-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="501e8-132">クライアント認証は、SOAP メッセージ セキュリティによって提供され、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="501e8-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="501e8-133">子要素</span><span class="sxs-lookup"><span data-stu-id="501e8-133">Child Elements</span></span>  
  
|<span data-ttu-id="501e8-134">要素</span><span class="sxs-lookup"><span data-stu-id="501e8-134">Element</span></span>|<span data-ttu-id="501e8-135">説明</span><span class="sxs-lookup"><span data-stu-id="501e8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="501e8-136">\<message></span><span class="sxs-lookup"><span data-stu-id="501e8-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="501e8-137">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="501e8-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="501e8-138">この要素は <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="501e8-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="501e8-139">親要素</span><span class="sxs-lookup"><span data-stu-id="501e8-139">Parent Elements</span></span>  
  
|<span data-ttu-id="501e8-140">要素</span><span class="sxs-lookup"><span data-stu-id="501e8-140">Element</span></span>|<span data-ttu-id="501e8-141">説明</span><span class="sxs-lookup"><span data-stu-id="501e8-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="501e8-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="501e8-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="501e8-143">すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="501e8-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="501e8-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="501e8-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="501e8-145">方法 : WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="501e8-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="501e8-146">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="501e8-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="501e8-147">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="501e8-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="501e8-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="501e8-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="501e8-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="501e8-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="501e8-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="501e8-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="501e8-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="501e8-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
