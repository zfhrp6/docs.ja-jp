---
title: "&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 27fedcd8ae7501f484de0aa2f21af8c701990285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="6d901-102">&lt;ws2007FederationHttpBinding&gt; の &lt;security&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="6d901-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="6d901-103">セキュリティ設定を定義、 [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="6d901-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="6d901-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6d901-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6d901-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6d901-105">\<bindings></span></span>  
<span data-ttu-id="6d901-106">\<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6d901-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="6d901-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6d901-107">\<binding></span></span>  
<span data-ttu-id="6d901-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="6d901-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d901-109">構文</span><span class="sxs-lookup"><span data-stu-id="6d901-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d901-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6d901-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6d901-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d901-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d901-112">属性</span><span class="sxs-lookup"><span data-stu-id="6d901-112">Attributes</span></span>  
  
|<span data-ttu-id="6d901-113">属性</span><span class="sxs-lookup"><span data-stu-id="6d901-113">Attribute</span></span>|<span data-ttu-id="6d901-114">説明</span><span class="sxs-lookup"><span data-stu-id="6d901-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6d901-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6d901-115">Optional.</span></span> <span data-ttu-id="6d901-116">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6d901-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6d901-117">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="6d901-117">The default value is `Message`.</span></span> <span data-ttu-id="6d901-118">この属性は <xref:System.ServiceModel.WSFederationHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="6d901-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6d901-119">mode 属性</span><span class="sxs-lookup"><span data-stu-id="6d901-119">mode Attribute</span></span>  
  
|<span data-ttu-id="6d901-120">値</span><span class="sxs-lookup"><span data-stu-id="6d901-120">Value</span></span>|<span data-ttu-id="6d901-121">説明</span><span class="sxs-lookup"><span data-stu-id="6d901-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d901-122">なし</span><span class="sxs-lookup"><span data-stu-id="6d901-122">None</span></span>|<span data-ttu-id="6d901-123">SOAP メッセージは、転送中はセキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="6d901-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="6d901-124">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6d901-124">Message</span></span>|<span data-ttu-id="6d901-125">SOAP メッセージ セキュリティを使用して、整合性、機密性、サーバー認証、およびクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="6d901-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="6d901-126">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="6d901-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6d901-127">サービスは、証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d901-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="6d901-128">クライアント認証は、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="6d901-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="6d901-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6d901-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="6d901-130">整合性、機密性、およびサーバー認証は、HTTPS によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="6d901-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="6d901-131">サービスは、証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d901-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="6d901-132">クライアント認証は、SOAP メッセージ セキュリティによって提供され、セキュリティ トークン サービスによってクライアントに発行されるトークンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="6d901-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d901-133">子要素</span><span class="sxs-lookup"><span data-stu-id="6d901-133">Child Elements</span></span>  
  
|<span data-ttu-id="6d901-134">要素</span><span class="sxs-lookup"><span data-stu-id="6d901-134">Element</span></span>|<span data-ttu-id="6d901-135">説明</span><span class="sxs-lookup"><span data-stu-id="6d901-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d901-136">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="6d901-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="6d901-137">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d901-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="6d901-138">この要素は <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="6d901-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d901-139">親要素</span><span class="sxs-lookup"><span data-stu-id="6d901-139">Parent Elements</span></span>  
  
|<span data-ttu-id="6d901-140">要素</span><span class="sxs-lookup"><span data-stu-id="6d901-140">Element</span></span>|<span data-ttu-id="6d901-141">説明</span><span class="sxs-lookup"><span data-stu-id="6d901-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d901-142">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6d901-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6d901-143">すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="6d901-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d901-144">参照</span><span class="sxs-lookup"><span data-stu-id="6d901-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="6d901-145">方法 : WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="6d901-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="6d901-146">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6d901-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6d901-147">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="6d901-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="6d901-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="6d901-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6d901-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6d901-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6d901-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="6d901-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6d901-151">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="6d901-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
