---
title: '&lt;issuedTokenParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef68585054d61de8c25b7e3effd1d72063d4589c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="41de5-102">&lt;issuedTokenParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="41de5-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="41de5-103">フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="41de5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="41de5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="41de5-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="41de5-105">\<bindings></span></span>  
<span data-ttu-id="41de5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="41de5-106">\<customBinding></span></span>  
<span data-ttu-id="41de5-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="41de5-107">\<binding></span></span>  
<span data-ttu-id="41de5-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="41de5-108">\<security></span></span>  
<span data-ttu-id="41de5-109">\<issuedTokenParameters ></span><span class="sxs-lookup"><span data-stu-id="41de5-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41de5-110">構文</span><span class="sxs-lookup"><span data-stu-id="41de5-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="41de5-111">型</span><span class="sxs-lookup"><span data-stu-id="41de5-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41de5-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="41de5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="41de5-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="41de5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41de5-114">属性</span><span class="sxs-lookup"><span data-stu-id="41de5-114">Attributes</span></span>  
  
|<span data-ttu-id="41de5-115">属性</span><span class="sxs-lookup"><span data-stu-id="41de5-115">Attribute</span></span>|<span data-ttu-id="41de5-116">説明</span><span class="sxs-lookup"><span data-stu-id="41de5-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41de5-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="41de5-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="41de5-118">バインドでサポートする必要があるセキュリティ仕様 (WS-Security、WS-Trust、WS-Secure Conversation、および WS-Security Policy) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="41de5-119">この値は、<xref:System.ServiceModel.MessageSecurityVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="41de5-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="41de5-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="41de5-120">inclusionMode</span></span>|<span data-ttu-id="41de5-121">トークン包含要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="41de5-122">この属性は <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="41de5-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="41de5-123">keySize</span><span class="sxs-lookup"><span data-stu-id="41de5-123">keySize</span></span>|<span data-ttu-id="41de5-124">トークン キー サイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="41de5-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="41de5-125">既定値は 256 です。</span><span class="sxs-lookup"><span data-stu-id="41de5-125">The default value is 256.</span></span>|  
|<span data-ttu-id="41de5-126">keyType</span><span class="sxs-lookup"><span data-stu-id="41de5-126">keyType</span></span>|<span data-ttu-id="41de5-127">キーの型を指定する <xref:System.IdentityModel.Tokens.SecurityKeyType> の有効な値。</span><span class="sxs-lookup"><span data-stu-id="41de5-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="41de5-128">既定値は、`SymmetricKey` です。</span><span class="sxs-lookup"><span data-stu-id="41de5-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="41de5-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="41de5-129">tokenType</span></span>|<span data-ttu-id="41de5-130">トークンの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="41de5-130">A string that specifies the token type.</span></span> <span data-ttu-id="41de5-131">既定値は、"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML" です。</span><span class="sxs-lookup"><span data-stu-id="41de5-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41de5-132">子要素</span><span class="sxs-lookup"><span data-stu-id="41de5-132">Child Elements</span></span>  
  
|<span data-ttu-id="41de5-133">要素</span><span class="sxs-lookup"><span data-stu-id="41de5-133">Element</span></span>|<span data-ttu-id="41de5-134">説明</span><span class="sxs-lookup"><span data-stu-id="41de5-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41de5-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="41de5-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="41de5-136">追加の要求パラメーターを指定する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="41de5-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="41de5-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="41de5-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="41de5-138">必須のクレームの種類のコレクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="41de5-139">フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。</span><span class="sxs-lookup"><span data-stu-id="41de5-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="41de5-140">たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41de5-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="41de5-141">このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="41de5-142">\<発行者 ></span><span class="sxs-lookup"><span data-stu-id="41de5-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="41de5-143">現在のトークンを発行するエンドポイントを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="41de5-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="41de5-144">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="41de5-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="41de5-145">トークン発行者のメタデータのエンドポイント アドレスを指定する構成要素。</span><span class="sxs-lookup"><span data-stu-id="41de5-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41de5-146">親要素</span><span class="sxs-lookup"><span data-stu-id="41de5-146">Parent Elements</span></span>  
  
|<span data-ttu-id="41de5-147">要素</span><span class="sxs-lookup"><span data-stu-id="41de5-147">Element</span></span>|<span data-ttu-id="41de5-148">説明</span><span class="sxs-lookup"><span data-stu-id="41de5-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41de5-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="41de5-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="41de5-150">セキュリティで保護されたメッセージ交換サービスの開始に使用される既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="41de5-151">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="41de5-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="41de5-152">カスタム バインドのセキュリティ オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="41de5-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41de5-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="41de5-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="41de5-154">バインディング</span><span class="sxs-lookup"><span data-stu-id="41de5-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="41de5-155">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="41de5-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="41de5-156">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="41de5-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="41de5-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="41de5-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="41de5-158">方法: SecurityBindingElement を使用してカスタム バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="41de5-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="41de5-159">カスタム バインディングのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="41de5-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="41de5-160">サービス Id と認証</span><span class="sxs-lookup"><span data-stu-id="41de5-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="41de5-161">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="41de5-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="41de5-162">カスタム バインドのセキュリティ機能</span><span class="sxs-lookup"><span data-stu-id="41de5-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="41de5-163">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="41de5-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
